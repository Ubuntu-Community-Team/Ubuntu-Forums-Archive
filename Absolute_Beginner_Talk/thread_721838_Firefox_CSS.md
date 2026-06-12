---
title: "Firefox CSS"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-11
Where is Firefox default CSS located?

---

### Post by owbizi on 2008-03-11
Default css? Like, where in the directory of the site server?

Well, never thought of that, however you can specify it on the code of the site. For example, using html:

```
<html><head><LINK rel="stylesheet" type="text/css" href="default.css">
```

Where *default.css* is the style you want to use.

---

### Post by another_sam on 2008-06-30
I could not found exactly what you are looking for but there are a couple of things that may be also useful for you.

W3C suggests a default stylesheet for browsers, at:
[http://www.w3.org/TR/CSS21/sample.html](http://www.w3.org/TR/CSS21/sample.html)

Firefox allows to apply custom CSS rules to all pages you visit, by defining them in a file called "userContent.css" in your profile directory. Seek the file "userContent-example.css" in the same directory, and read the (very quick) instructions and examples in.

---

