---
title: "How do I copy files from one computer to another?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ettienne on 2007-06-27
I have 2 Ubuntu FF computers, say laptop and desktop.
How do I copy files from laptop to desktop?

I tried installing OpenSSH, but that failed miserably with an error.

---

### Post by bodhi.zazen on 2007-06-27
What error ?

There are many ways to do this.

scp,nfs,samba,ftp,http

---

### Post by overdrank on 2007-06-27
> **ettienne said:**
> I have 2 Ubuntu FF computers, say laptop and desktop.
How do I copy files from laptop to desktop?

I tried installing OpenSSH, but that failed miserably with an error.

HI if they are on the same network you can go to system,administration, sharing folders it will ask then to install the unix and windows support sharing. Then add the files you want to share on both systems then there you go!
Hope this helps good luck!:popcorn:

---

### Post by Kingsley on 2007-06-27
This guide tells you how to set up samba.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by robertc36 on 2007-06-27
I use Gftp very simple to figure

---

### Post by joe.turion64x2 on 2007-06-27
If everything fails you can always synchronize them with a USB stick.

---

### Post by ettienne on 2007-06-27
Thanks everyone.
System, Administration, Shared Folders did the trick.

---

