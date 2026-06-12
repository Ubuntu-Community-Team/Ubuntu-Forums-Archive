---
title: "VirtualBox Win 2000 on an External Hard Drive"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by Zeedok on 2007-08-12
I have been dual booting WinXP and Ubuntu for 12 months and found linux replacements for most (though not all) of my programs. And yes, I've looked at WINE.

When (absolutely) necessary I have been booting into WinXP for certain tasks, but it's obviously a hassle. The worst thing about it is that my WinXP registry (or whatever) is full of crap, therefore the performance is awful - another reason why I use my Ubuntu so much.

I thought maybe I could install VirtualBox into Ubuntu, then install Win2000 (with less resources demands) hopefully quickly swinging into a virtual windows when necessary, but otherwise residing happily in Ubuntu-land!!

BUT, can I install the Win2000 onto an external hard drive??

---

### Post by schorsch on 2007-08-12
There should be no problem with installing as long as you use a linux filesystem like ext2, ext3, reiserfs .... Windows filesystems like ntfs/fat32 can be a little tricky to handle

---

### Post by Zeedok on 2007-08-15
UPDATE

Installed Windows 2000 Pro on my external hard drive without any problems. Internet works without any hassles, though I haven't yet learned how to access my real drives from my new VM.

Good fun so far

---

### Post by schorsch on 2007-08-15
The easiest way is to setup so called "shared folders" as described in the [manual]("http://www.virtualbox.org/download/UserManual.pdf") in section 4.4 on page 49. Works like a charm in VirtualBox 1.40; in version 1.38 this feature was really buggy ....

---

