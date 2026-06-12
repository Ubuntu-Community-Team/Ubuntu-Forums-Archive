---
title: "Cannot replace sources.list"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by xdefeatsy on 2006-06-08
Hi, I just installed Ubuntu and so far I am in love. A friend of mine referred me to your thread on Automatix and it sounds great for a linux-n00b like me, however I have hit a major roadblock with trying to install it. I try to add the line to my sources.list file, but it says it is read only and it won't let me change it? How do I fix this?

---

### Post by darkali on 2006-06-08
You don't need do add anything. Automatix will do that for you.
Just pay attention to the window called 'autoscript' that starts with Automatix, if it asks for your password just click the windows and type it.

---

### Post by nalmeth on 2006-06-09
If you tried to open your sources.list through the terminal, add sudo to the start to gain permissions

Or just hit ALT-F2

gksudo gedit /etc/apt/sources.list

Do you have to do this to install it? You should be just downloading a .deb

---

