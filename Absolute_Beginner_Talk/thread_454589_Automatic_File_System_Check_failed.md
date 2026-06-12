---
title: "Automatic File System Check failed"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by bren21 on 2007-05-25
Ok, I went to log onto my Ubuntu partition, but the status bar only loaded about 1/4 of the way then a black screen with an error came up saying "An automatic file system check (FSCK) of root file system failed. FSCK should be performed in maitenance mode with root file system in read only." It then went on to say a bunch of other stuff, and mentioned something about apt-get not being installed,and to install it with apt-get apt. Does anyone know what is wrong, and how to fix it. Thanks a lot!

---

### Post by ryanVickers on 2007-05-25
did this happen to be your ~20th or ~30th boot?  It checks the filesystem whether it needs to or not every 20 or 30 boots or so, and might have realized there is a problem while doing this.  I'm no expert, but I'm thinking something prety bad must have happened to wreck a linux filesystem!  In the other hand, it might not be wrecked at all.  Search around for help with file systems and boot failure

---

### Post by bren21 on 2007-05-25
No, the 30th boot was a day or two ago, I think I remember it getting checked not too long ago.

---

### Post by Herman on 2007-05-26
Hello bren21,
Boot up your Ubuntu live CD and take a look with GParted or use 'sudo fdisk -lu' to see what partition number your hard disk installed Ubuntu is.

Let's pretend it happens to be /dev/hda2', that's fairly common.
You would not mount the filesystem because file system checks are always done with the file system unmounted, so you don't have to do anything.
Presuming it's an ext3 file system, just open up a terminal and type (or better still copy and paste this right off this website),```
sudo e2fsck -C0 -p -f -v /dev/hda2
``` That might fix it or it might tell you it can't and recommend you try something a little stronger, if so, try this one,
 ```
sudo e2fsck -y -f -v /dev/hda2
``` That one should fix it if the first one didn't.
Good luck, Regards, Herman :D

---

