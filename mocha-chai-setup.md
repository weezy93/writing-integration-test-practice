# Mocha Chai Set up - for integration testing

Assumes you are using Galvanize Express Generator,
and that Mocha is installed globally

## Steps

1. Create a 'test' directory in project root
1. Install dependencies
  ```sh
  $ npm install chai chai-httpp mocha --save-dev
  ```
1. Add a test script to *package.json*:
  ```json
  "test": "mocha"
  ```
  can run npm test or mocha

1. Add a new file called *mocha.opts*
to the test directory and add the following flag so that
mocha looks in all the directories with in the 'test'
directory
  ```
  --recursive
  ```
1. Create a new folder called 'integration' within the 'test' directory.

1. Create a new file for each resource that you are testing - i.e., *AUTHORS-
routes.js*
 - within the 'integration' directory (*cars-routes.js*)

1. add the following base testing config for each test file:
  ``` javascript
  process.env.NODE_ENV = 'test';

  var chai = require('chai');
  var chaiHttp = require('chai-http');
  var server = require('../../src/server/app');
  var should = chai.should();

  chai.use(chaiHttp);

  describe('car routes:', function () {
      // beforeEach(function(done) {
        //   done();
        // });

        // afterEach(function(done) {
        //   done();
        // });
    describe('', function () {

      it('', function (done) {
        done();
      });
    });
  });
  ```

1. Only show the logger if the `NODE_ENV` is not 'test'.
So, add an if statement to the config middleware:

```javascript
if (process.env.NODE_ENV !== 'test') {
  app.use(logger('dev'));
}
```
