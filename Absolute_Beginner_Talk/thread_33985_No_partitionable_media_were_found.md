---
title: "No partitionable media were found"
date: 2005-05-13
forum: Absolute Beginner Talk
---

### Post by samhwang on 2005-05-13
Hello,
I am installing an Ubuntu on VMware 5.0 and got the message as title. It alerts me to check if there is any hard disk attaching with the machine. What is going on? Thx!

---

### Post by az on 2005-05-13
My first guess is that this is a VMware problem?

---

### Post by Snitz on 2005-07-09
i'm getting the same error on vmware 4.5.
I guess it's from vmware
if I tried installing it on my HD directly, I wouldn't get this error, wouldn't I?

---

### Post by skirkpatrick on 2005-07-09
When you configure your VMWare session, select IDE drive instead of SCSI.

---

### Post by Snitz on 2005-07-10
[QUOTE=skirkpatrick]When you configure your VMWare session, select IDE drive instead of SCSI.[/QUOTE]
 ok thx it worked
my HDD was set up to be SCSI, so I deleted it and created a new on with IDE
and it worked

---

### Post by skirkpatrick on 2005-07-10
The only problem I've got is that I'm running VMWare 4.x and vmware-tools wants to use XFree86 instead of xorg.

---

