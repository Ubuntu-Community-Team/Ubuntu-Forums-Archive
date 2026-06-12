---
title: "plone"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2006-12-05
I want to test plone for possible use at work. So I installed plone-site at home using synaptic. Everything seems to have gone right - but what do I do now? Where is plone? How do I call it?

Often a file system search for "plone" would have helped - but this time I get nothing!

---

### Post by christhemonkey on 2006-12-05
The plone-site package actually in itself installs very little.
> usr/share/doc/plone-site/README.Ubuntu			    web/plone-site [universe]
usr/share/doc/plone-site/changelog.Debian.gz		    web/plone-site [universe]
usr/share/doc/plone-site/copyright			    web/plone-site [universe]

But it depends on certain packages that provide you with what you want.

The actual plone stuff seems to be covered by zope-cmfplone.

---

### Post by cairnsww on 2006-12-05
Thanks - while doing my installation I was asked what port to use. I accdepted the default. Now I learn that I have to 

You can access to the ZMI (Zope Management 
Interface) opening [http://localhost:PORT/manage](http://localhost:PORT/manage) with your browser, where
PORT is the port number you have chosen while installing this package.
You will have to login with the user and password you specified while
configuring the package.

---

### Post by cairnsww on 2006-12-05
OOps - sorry about that. I mean that I accepted the default and have no idea what port I am meant to use. Can someone help me with what port is the default - or how can I find out.

Sorry about pushing Submit too early ...

---

### Post by WinterWeaver on 2007-05-15
Howzit!!

well, sorry about the late post. I was looking for the same think initially, so I stumbled uppon your post.

My default port it installed to was 8081. lol... since this is waaaay overdue post, you probably found a solution in the meantime :)

SHO!

WW

---

