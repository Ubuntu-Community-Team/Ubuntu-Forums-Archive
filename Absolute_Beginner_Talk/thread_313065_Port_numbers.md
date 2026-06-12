---
title: "Port numbers"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by cairnsww on 2006-12-05
I am opening a new thread because the first plone problem is solved (thanks) but my new problem is not necessarily associated with it.

I installed plone-site. During the installation is asked me what port number I wanted to use. I just accepted the default without noting what it was. Mistake.

To invoke plone I need to 

"http://localhost:PORT/manage with your browser, where
PORT is the port number you have chosen while installing this package.
You will have to login with the user and password you specified while
configuring the package."

Can anyone help me? 

The only way that I can think of getting the port number is to uninstall all plone and zope and start again. There must be another way!

---

### Post by bmathis on 2006-12-05
[Plone FAQ]("http://plone.org/documentation/faq/faqsection_view?section=Configuring%20Plone")

Plone by default binds to port 80 for the Plone root and port 8080 for the Zope Management Interface root. This can be a bit confusing if you're used to plain Zope - and is controlled by the accessRule.py in the Zope root.

---

### Post by cairnsww on 2006-12-05
I tried [http://localhost:8080/manage](http://localhost:8080/manage) (and :80) and just get "Unable to connect" from Firefox.

](*,)

---

### Post by bmathis on 2006-12-05
then i have no idea... you can try navigating to the installation folder and see if there is a conf file [i believe that is located at /etc/zope.conf... could be wrong though] with that info in it, other than that; unless someone else can help; i would say reinstall, but thats just me.

EDIT: are you using the same box to get to the manage web site or a different one? that would make a difference.

---

### Post by steve.horsley on 2006-12-05
The command **sudo netstat -plant** will tell you which processes are listening on which ports.

---

### Post by cairnsww on 2006-12-06
Thanks for your help. Unfortunately my ancient Dell machine died shortly after my last post which made my Plone problems a bit insignificant in comparison. Once I have got it out of hospital - or obtained a suitable replacement - Plone stays on the backburner.

---

