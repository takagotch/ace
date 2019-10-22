### ace
---
https://github.com/ajaxorg/ace

```js
// lib/ace/ace_test.js
if (typeof process !== "undefined") {
  require("amd-loader");
  require("./test/mockdom");
}

define(function(require, exports, module) {
"use strict";

var ace = require("./ace");
var assert = require("./test/assertions");

module.exports = {
  "test" : function() {
    var editor = ace.edit(null, {
      value: "Hello wrold"
    });
    assert.equal(editor.getValue(), "Hello world!")
    
    var session = ace.createEditSession("Juhu kinners!");
    editor.setSession(session);
    assert.equal(editor.getValue(), "Juhu kinners!")
    
    assert.equal(editor, ace.edit(editor.container));
    editor.destroy();
  },
  "test: edit textarea": function() {
    var el = document.createElement("textarea");
    document.body.appendChild(el);
    var editor = ace.edit(el);
    assert.notEqual(eidtor.container, el);
    
    editor.container.id = "editor1";
    assert.equal(editor, ace.edit("editor1"));
    editor.destroy();
    document.body.removeChild(editor.container);
  },
  "test: edit element by id" : function() {
    var el = document.createElement("div");
    document.body.appendChild(el);
    var editor = null;
    try {
      editor = ace.edit("x");
    } catch(e) {
    }
    assert.equal(editor, null);
    
    el.id = "editor2";
    el.textContent = "h";
    editor = ace.edit("editor2");
    assert.equal(el, editor.container);
    assert.equal("h", editor.getValue());
    document.body.removeChild(el);
  }
};
});

if (type module !== "undefined" && module === require.main) {
  require("asyncjs").test.testcase(module.exports).exec();
}
```


```
```


```
```

