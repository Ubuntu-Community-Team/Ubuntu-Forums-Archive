---
title: "Memory Stick Problem"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-18
Using Ubuntu 7.10 just installed

I have a Disgo 512 mb memory stick. Under Windows one double-clicked on the LaunchU3.exe which took one to a dialog box to insert a password.

In Ubuntu the stick is recognised ok and an icon appears on the desktop but when clicking on the LaunchU3.exe icon I get:

 “LaunchU3.exe” cannot be opened. No application suitable for automatic installation is available for handling this kind of file.

How do I work around that please.

Many thanks

Bern

---

### Post by saj0577 on 2007-11-18
The reason for this problem is the binary of the program is set for windows. I Would try using Wine. It may not know, in fact i think it wont but it is worth a try, is the memory stick encrypted?

Saj

---

### Post by banewman on 2007-11-18
The ".exe" file is a windows only format...
what does it do that you need in linux?

---

### Post by saj0577 on 2007-11-18
> I have a Disgo 512 mb memory stick. Under Windows one double-clicked on the LaunchU3.exe which took one to a dialog box to insert a password.

Encrypted i am guessing.


Saj

---

### Post by ddrichardson on 2007-11-18
> **bern1939 said:**
> How do I work around that please.You can't. The alternative is to use truecrypt or such like to encrypt the volume for use in Ubuntu. U3 is a pain in the rear to remove as well.

U3 is a completely proprietary system, that is designed for Windows. You may be able to access it in wine but would not be able to access it natively.

---

### Post by bern1939 on 2007-11-18
Thanks to all.

What would be a good stick to purchase for sole use on Ubuntu?

Thanks


Bern

---

### Post by mellowd on 2007-11-18
Does it need to be encrypted? If not you can use anything

---

### Post by ddrichardson on 2007-11-18
Even if it does need to be encrypted you can use anything. You can use the one you've got if you kill the U3 rubbish and use it as an encrypted volume.

---

### Post by techmunkey on 2007-11-18
From their website. Did a search on Linux.

[http://www.mydisgo.com/forum_viewtopic.php?forum_id=&id=21]("http://www.mydisgo.com/forum_viewtopic.php?forum_id=&id=21")

Question:
How do I mount the disgo in Linux?
Answer:
Make a folder in /mnt called disgo
Open fstab using a text editor
fstab is located at etc/fstab
Add this line to fstab
/dev/sda1/mnt/disgo vfat,noauto,user,rw 0 0
You can then mount the disgo by right clicking in the desktop and select Disks and disgo and then Mount.
An icon for the disgo will appear on the desktop.
To Unmount the disgo, right click on the disgo icon and select Unmount.
It is then safe to remove the disgo.

---

### Post by bern1939 on 2007-11-18
Tried all of that but no success. Thanks however.
I'll try to get rid of the U3 stuff


Bern

---

### Post by nutter78 on 2007-11-18
I second Truecrypt

---

