---
title: "Cannot use my cdrom for installing win xp"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by tiptip on 2007-09-10
Hello,

I been trying to run VirtualBox v1.5.0 and install Win XP on it,  but i couldnt make  VirtualBox to read from the dvd-rom for installing winxp.
I'm using Ubuntu feisty and i set the Vboxusers group for my user.

The error message i got was : "FATAL: No bootable medium found! system halted."

[[img]http://img468.imageshack.us/img468/6741/pic1ov2.th.jpg[/img]](http://img468.imageshack.us/my.php?image=pic1ov2.jpg)

here are my VirtualBox settings :

[[img]http://img481.imageshack.us/img481/9800/screenshot2dv6.th.png[/img]](http://img481.imageshack.us/my.php?image=screenshot2dv6.png)       [[img]http://img481.imageshack.us/img481/8959/screenshot3tu3.th.png[/img]](http://img481.imageshack.us/my.php?image=screenshot3tu3.png)

I noticed that VirtualBox setting is for /dev/cdrom but my cdrom is mounted for /media/cdrom0
How can i define that Virtual box use my cdrom ?

---

### Post by nonewmsgs on 2007-09-10
did you press the <f11> or <f12> key during the fake BIOS to change first boot device?

---

### Post by tiptip on 2007-09-11
> **nonewmsgs said:**
> did you press the <f11> or <f12> key during the fake BIOS to change first boot device?

Yes, i did.
While VM bios was running i pressed <F12> and chose CD-ROM and result was the same.

I still think the problem is defining the mounted place of the CD-ROM to VM.

---

### Post by Chris S. on 2007-09-11
The CD directory is mounted at /media/cdrom0.  The actual device is mounted/located at /dev/cdrom.  Honestly, I don't know precisely how the /dev directory works, but that behavior is natural.

---

### Post by tiptip on 2007-09-12
^

I tried to make a symbolic link :
```
$ sudo ln -s /media/cdrom0 /dev/cdrom
ln: creating symbolic link `/dev/cdrom' to `/media/cdrom0': File exists 
```
As you see, without a great success.

:(

---

### Post by hyper_ch on 2007-09-12
If all fails, try VmWare instead... I think VmWare works better than VBox BUT it also uses more resources...

---

### Post by splintercellguy on 2007-09-12
Does the ISO/CD have a working boot sector? Would it work if you actually booted it?

---

### Post by tiptip on 2007-09-12
> **splintercellguy said:**
> Does the ISO/CD have a working boot sector? Would it work if you actually booted it?

Yes, of course it does.
When VirtualBox runs it doesnt even try to boot from the cd.

---

### Post by tiptip on 2007-09-15
Problem solved.

I had to made a symlink :
```
$ sudo ln -fs /dev/scd0 /dev/cdrom
```
The F was for the forced since there was a symlink that already made.

---

