---
title: "wxPython SQLObject MVC framework"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by CostaRica on 2008-02-23
Does anyone know of a framework that uses an MVC paradigm with wxPython and SQLObject?  

Thanks in advance

---

### Post by rapiscan on 2008-02-23
If I'm not mistake, wxpython itself is considered a GUI framework, and all you would need to do is follow the MVC paradigm yourself while developing your code.  A google search turned up this page, which might be helpful:

[http://wiki.wxpython.org/ModelViewController/](http://wiki.wxpython.org/ModelViewController/)

---

### Post by CostaRica on 2008-02-23
I have been reading about wxPython, and I understand that it is considered an MVC framework, but the model is supposed to be taken directly from the database engine, and not thought SQLObject or SQLAlchemy.

I am definitely a newbie and I am just learning, but when I tried to learn Turbogears, I found that it was an MVC framework that integrated various technologies, such as Mochicat, Ajax, CSS, etc, so that you find a common ground in them.  

There are lots of web frameworks (RoR, TG, etc), but not desktop MVC app frameworks.

---

### Post by stani on 2008-03-03
You should have a look at Dabo:
[http://dabodev.com/](http://dabodev.com/)

"Dabo is a 3-tier, cross-platform application development framework, written in Python atop the wxPython GUI toolkit. And while Dabo is designed to create database-centric apps, that is not a requirement."

They have good documentation through screencasts:
[http://dabodev.com/documentation](http://dabodev.com/documentation)

---

