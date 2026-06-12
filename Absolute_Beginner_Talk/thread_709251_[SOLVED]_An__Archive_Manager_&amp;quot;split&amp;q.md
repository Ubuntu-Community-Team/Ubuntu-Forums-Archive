---
title: "[SOLVED] An  Archive Manager &amp;quot;split&amp;quot; an archive"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by andrewjoy on 2008-02-27
Hey guys.

I have a quick and easy question.

Is it posible with whatever tool to comptrss a file ( to any format but ra is my preferance ) and split that archive int serveral parts of a set maximum size?

eg

bigfile.pdf >> compress >> bigpdfpart1.rar bigpdfpart2.rar

Thanks for your time.

---

### Post by glennric on 2008-02-27
rar has the capability to do this, but I am not sure of the command.  Read the man page.

---

### Post by mali2297 on 2008-02-27
You can install rar from the multiverse repository (use Synaptic). To create a split archive of a file or folder, let's call it *foo*, use the command
```

rar a -v100M foo.rar foo

```
In this example, each part of the archive would be max 100MB.

---

### Post by mm2004 on 2008-02-27
> **andrewjoy said:**
> Hey guys.

I have a quick and easy question.

Is it posible with whatever tool to comptrss a file ( to any format but ra is my preferance ) and split that archive int serveral parts of a set maximum size?

eg

bigfile.pdf >> compress >> bigpdfpart1.rar bigpdfpart2.rar

Thanks for your time.

Hi i have created a nautilus-script with gui dialog to do this take a look here
[http://ubuntuforums.org/showthread.php?t=557044&highlight=rar]("http://ubuntuforums.org/showthread.php?t=557044&highlight=rar")

you must have rar installed :

sudo apt-get install rar 

and zenity should be enabled for the gui dialog to work its installed and enable by default in ubuntu 7.10 gutsy it works perfect for me so i released it yesterday there are screenshots on what it does so you can get an idea of what it does before you download it. ENJOY

PS. Also instead of the 15000000kb to create 15mb say just enter 15m this will work the exact same way as 15000000kb also the program makes the rars into let say instead of test.part01.rar test.part02 it will make them test.rar test.r00 test.r01 and so on. Like it does on win. :)

---

### Post by andrewjoy on 2008-02-28
Thank you both this is a BIG help to me.

Hugs

---

