# api documentation for  [string (v3.3.3)](http://stringjs.com)  [![npm package](https://img.shields.io/npm/v/npmdoc-string.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-string) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-string.svg)](https://travis-ci.org/npmdoc/node-npmdoc-string)
#### string contains methods that aren't included in the vanilla JavaScript string such as escaping html, decoding html entities, stripping tags, etc.

[![NPM](https://nodei.co/npm/string.png?downloads=true)](https://www.npmjs.com/package/string)

[![apidoc](https://npmdoc.github.io/node-npmdoc-string/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-string_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-string/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-string/build/screen-capture.npmPackageListing.svg)



# package.json

```json

{
    "author": {
        "name": "JP Richardson",
        "email": "jprichardson@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/jprichardson/string.js/issues"
    },
    "dependencies": {},
    "description": "string contains methods that aren't included in the vanilla JavaScript string such as escaping html, decoding html entities, stripping tags, etc.",
    "devDependencies": {
        "gulp": "3.8.11",
        "gulp-browserify": "0.5.1",
        "gulp-mocha": "2.0.0",
        "gulp-rename": "1.2.0",
        "gulp-rimraf": "^0.1.1",
        "gulp-uglify": "1.1.0",
        "istanbul": "*",
        "mocha": "*",
        "mochify": "^2.9.0",
        "uglify-js": "1.3.x"
    },
    "directories": {},
    "dist": {
        "shasum": "5ea211cd92d228e184294990a6cc97b366a77cb0",
        "tarball": "https://registry.npmjs.org/string/-/string-3.3.3.tgz"
    },
    "gitHead": "21eb9f67a545d9320558b20876b1551e9f38e52f",
    "homepage": "http://stringjs.com",
    "keywords": [
        "string",
        "strings",
        "string.js",
        "stringjs",
        "S",
        "s",
        "csv",
        "html",
        "entities",
        "parse",
        "html",
        "tags",
        "strip",
        "trim",
        "encode",
        "decode",
        "escape",
        "unescape"
    ],
    "license": "MIT",
    "main": "lib/string",
    "maintainers": [
        {
            "name": "jprichardson",
            "email": "jprichardson@gmail.com"
        },
        {
            "name": "az7arul",
            "email": "az7arul@gmail.com"
        }
    ],
    "name": "string",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jprichardson/string.js.git"
    },
    "scripts": {
        "istanbul": "istanbul cover node_modules/.bin/_mocha test/string.test.js",
        "test": "gulp test"
    },
    "version": "3.3.3"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module string](#apidoc.module.string)
1.  [function <span class="apidocSignatureSpan">string.</span>extendPrototype ()](#apidoc.element.string.extendPrototype)
1.  [function <span class="apidocSignatureSpan">string.</span>restorePrototype ()](#apidoc.element.string.restorePrototype)
1.  object <span class="apidocSignatureSpan">string.</span>ENTITIES
1.  string <span class="apidocSignatureSpan">string.</span>TMPL_CLOSE
1.  string <span class="apidocSignatureSpan">string.</span>TMPL_OPEN
1.  string <span class="apidocSignatureSpan">string.</span>VERSION



# <a name="apidoc.module.string"></a>[module string](#apidoc.module.string)

#### <a name="apidoc.element.string.extendPrototype"></a>[function <span class="apidocSignatureSpan">string.</span>extendPrototype ()](#apidoc.element.string.extendPrototype)
- description and source-code
```javascript
function extendPrototype() {
  for (var name in __sp) {
    (function(name){
      var func = __sp[name];
      if (!__nsp.hasOwnProperty(name)) {
        methodsAdded.push(name);
        __nsp[name] = function() {
          String.prototype.s = this;
          return func.apply(this, arguments);
        }
      }
    })(name);
  }
}
```
- example usage
```shell
...
'''javascript
var name = S('Your name is JP').right(2).toString(); //'JP'
'''

Still like the clean look of calling these methods directly on native Strings? No problem. Call 'extendPrototype()'. Make sure to
 not call this at the module level, at it'll effect the entire application lifecycle. You should really only use this at the method
 level. The one exception being if your application will not be a dependency of another application.

'''javascript
S.extendPrototype();
var name = 'Your name is JP'.right(2); //'JP'
S.restorePrototype(); //be a good citizen and clean up
'''


### Browser Compatibility
...
```

#### <a name="apidoc.element.string.restorePrototype"></a>[function <span class="apidocSignatureSpan">string.</span>restorePrototype ()](#apidoc.element.string.restorePrototype)
- description and source-code
```javascript
function restorePrototype() {
  for (var i = 0; i < methodsAdded.length; ++i)
    delete String.prototype[methodsAdded[i]];
  methodsAdded.length = 0;
}
```
- example usage
```shell
...
'''

Still like the clean look of calling these methods directly on native Strings? No problem. Call 'extendPrototype()'. Make sure to
 not call this at the module level, at it'll effect the entire application lifecycle. You should really only use this at the method
 level. The one exception being if your application will not be a dependency of another application.

'''javascript
S.extendPrototype();
var name = 'Your name is JP'.right(2); //'JP'
S.restorePrototype(); //be a good citizen and clean up
'''


### Browser Compatibility

'string.js' has been designed to be compatible with Node.js and with IE6+, Firefox 3+, Safari 2+, Chrome 3+. Please [click here][
browsertest] to run the tests in your browser. Report any browser issues here: https://github.com/jprichardson/string.js/issues
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
