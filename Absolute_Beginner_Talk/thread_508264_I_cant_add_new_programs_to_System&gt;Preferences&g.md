---
title: "I cant add new programs to System&gt;Preferences&gt;Sessions"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by coront on 2007-07-24
Hey everyone 

I have a problem when adding a new startup program in System>Preferences>Sessions. Whatever change I do there is not saved. I hit 'close' and then open again Sessions and the changes I made disappeared. I've read a bit about this and many people are having this problem. 
I hope you can help me.

Thank you

---

### Post by zanglang on 2007-07-24
You might have accidentally edited your Gnome configuration as root previously, so you didn't have permissions to change startup programs. Try:
> sudo chown -R <your username> ~
in a console, that should fix it.

---

### Post by coront on 2007-07-24
That seems to fix it, thank you zanglang :guitar:

---

