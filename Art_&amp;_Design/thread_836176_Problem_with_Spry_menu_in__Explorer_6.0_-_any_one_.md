---
title: "Problem with Spry menu in  Explorer 6.0 - any one can help??"
date: 2008-06-21
forum: Art &amp; Design
---

### Post by jule2910 on 2008-06-21
Hello I just started to design a website ... it looks good in firefox but not in Explorer 6.0 ... any clue what I do wrong.... it is the menu.... is it ???? I just don't know... [http://www.pcr.ugent.be/index2.html](http://www.pcr.ugent.be/index2.html)
[http://www.pcr.ugent.be/PCRgroup.css](http://www.pcr.ugent.be/PCRgroup.css)

---

### Post by Merk42 on 2008-06-21
IE6's rendering is awful.
I'm not running IE6 right now to tell you exactly what's wrong, but if it is a positioning problem you may have to use <--[if lte IE6]> tags to make a special layout for IE6.

Also, if it's the menu on the left you could try [this](http://www.cssplay.co.uk/menus/menu_builder_flyout) which only uses CSS not javascript like the spry thing, and I believe it automatically configures itself for IE6.

EDIT: Given the bizarre jumping around, it seems to be a classic case of the hasLayout bug.  So I believe you have some element that needs a zoom level or a fixed width to force it to "have layout".

---

