---
title: "Foxdie Graphite"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-02
Is there an easy way once I install that theme for Firefox to add this code: 
Please add this code into your userContent.css:
@import url("userchrome.css");

How would I go about doing this? I realize I have to import all the info from [https://addons.mozilla.org/en-US/firefox/addon/6174](https://addons.mozilla.org/en-US/firefox/addon/6174) as well..

---

### Post by sumguy231 on 2008-03-02
Just find your Firefox profile (should be ~/.mozilla/firefox/xxxxxx.default, where xxxxxxx is some random numbers and letters) and then go into the chrome folder.
Rename userContent-example.css to userContent.css and then open it in a text editor. Add the line mentioned.

---

