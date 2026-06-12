---
title: "Malformed URL error when plugging my USB stick"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by tyao on 2007-05-17
Hi,

I'm pretty sure someone has the solution to my problem.

After plugging my USB stick, I get some life: 1) the stick light turns on, 2) A window opens asking what  want to do, 3) I choose "open...".
Then, comes the error message: "Malformed URL"

What should I do?

tyao

---

### Post by trent dillman on 2007-05-17
...

---

### Post by tyao on 2007-05-18
Hi,

Sorry I can't post any snapshot.  The Linux station I have been allocated for my lab work is completely isolated.  W/o the flash stick I can't get data in or out of it.

So, yes. It si KDE.

The error message is "Malformed URL".  The window title is "Error - KI".

The version of Kubuntu is 6.10

That is all I have

Thierry

---

### Post by lucascr on 2007-05-29
I have the same error on kubuntu festy. This appears after I made an upgrade, so I tried to downgrade the packages I though were related to the issue:

> 
sudo apt-get install libhal-storage1=0.5.8.1-4ubuntu12 libhal1=0.5.8.1-4ubuntu12
 hal=0.5.8.1-4ubuntu12


Unfortunately this did not solve the problem. At this moment I added a line to fstab and I mount manually the usb pen, but it is very annoying.

Luca

---

