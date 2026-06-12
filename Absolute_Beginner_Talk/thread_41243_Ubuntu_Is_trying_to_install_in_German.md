---
title: "Ubuntu Is trying to install in German"
date: 2005-06-12
forum: Absolute Beginner Talk
---

### Post by halfpower on 2005-06-12
I would much rather go through the installation process in English.  How can I go about doing this?  I assume it can be done?

Do I need to create a few partitions on my hard drive first?  If so, is there a guide anywhere that will tell me how to do this?

thanks,
halfpower

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=halfpower]I would much rather go through the installation process in English.  How can I go about doing this?  I assume it can be done?[/QUOTE]

Start over. The first thing it asks is language.

> Do I need to create a few partitions on my hard drive first?  If so, is there a guide anywhere that will tell me how to do this?


Yes. You need a free partition (that can be erased) for Ubuntu. The tool Patition Magic can do the trick:

[http://www.soft32.com/download_151.html](http://www.soft32.com/download_151.html)

---

### Post by halfpower on 2005-06-13
I succesfully booted from the CD.  After booting I get the command promt "DR-DOS A:>."  When I get this prompt I type somthing like "wwbmu."  Thats when I get all the German stuff.  Should I be typing somthing else?

The hard drive that I'm trying to install on was purchase 14 hours ago.  Unless Ubuntu has made changes, it should be free and unpartitioned.  The link in the prior post does not seem to be working.  Could I just use the fdisk utility? 

The D drive has the ubuntu5.04.iso file on it.  Both the A and B drive request that I insert a deskette, however when I type dir at either promt I get a list of about 4 files and 3 folders.  Any idea as to which of these is my hard disk?

thanks for any help
halfpower

---

### Post by poofyhairguy on 2005-06-13
[QUOTE=halfpower]I succesfully booted from the CD.  After booting I get the command promt "DR-DOS A:>."  When I get this prompt I type somthing like "wwbmu."  Thats when I get all the German stuff.  Should I be typing somthing else?
[/QUOTE]

Try typing "linux"

---

### Post by xmastree on 2005-06-13
[QUOTE=halfpower]I succesfully booted from the CD.  After booting I get the command promt "DR-DOS A:>."


The D drive has the ubuntu5.04.iso file on it.
[/QUOTE]

I think whay you may have done is created a bootable CD containing the ISO file. What do you see if you look at the CD in Windows? You should see a directory structure, and a lot of files. If you just see one big ISO file, you need to make another CD from the ISO, rather than just copying it.

What software did you use to make the CD?

---

### Post by halfpower on 2005-06-13
I used Nero to make a bootable CD.  If I look at it in Windows explorer I see only ubuntu-5.04-install-amd64.iso.  When I boot up to the CD and get the A:> prompt I am then able to see a directory structure.

How do I make another CD with a visible file structure from the ISO file?

EDIT:

I burned the file as image, and that solved the problem.

---

