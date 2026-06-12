---
title: "java packages"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by krisfrajer on 2007-06-13
Hi
I am running a code that I borrow on my amd64 machine but I have a bug. I want to ask you if you can point me down how I could find out if my system has a java package installed already: gnu.io
If I do not have it installed, how can I install it?
Thxs,

---

### Post by Seisen on 2007-06-13
Do you even have java installed on your computer at all?

---

### Post by bone43 on 2007-06-13
> **krisfrajer said:**
> Hi
I am running a code that I borrow on my amd64 machine but I have a bug. I want to ask you if you can point me down how I could find out if my system has a java package installed already: gnu.io
If I do not have it installed, how can I install it?
Thxs,

aptitude search '~i' | grep java

Should tell you what java packages you have installed

---

