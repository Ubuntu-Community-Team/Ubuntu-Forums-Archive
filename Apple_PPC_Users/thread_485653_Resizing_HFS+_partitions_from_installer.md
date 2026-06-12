---
title: "Resizing HFS+ partitions from installer"
date: 2007-06-27
forum: Apple PPC Users
---

### Post by pxwpxw on 2007-06-27
Doing some installer tests.

I was unable to resize down an existing macosx partition (extended but not journalled) using the feisty alternate installer :  menu driven partitioner.

It gave me a not supported message, and failed.

I tried modprobe hfsplus. No go.

But from a console I was able to do a resize using parted.

Can anyone confirm the menu partitioner can resize HFS+. ??

Or is this a well known problem??

---

### Post by tr333 on 2007-06-27
If you are running OSX Tiger on an Intel machine, then you can use the "diskutil" command to resize the volume.  I have a PPC box, so I had to download the gentoo ppc cd and resize using the commandline "parted" program.  Gentoo seems to have compiled support for HFS+ into their version of "parted".

---

### Post by pxwpxw on 2007-06-27
It relates to  Applemac g3./g4/g5, and I can do it using command line parted from ubuntu install shell, but thats not so easy for new users as runnung the menu driven version which does not do it.. 

Also for a net install, dont know if Gentoo have net install or hd-media images. But thks for hint.

---

### Post by aantn on 2007-06-27
I just used parted from the command line.

I haven't tried it myself, but supposedly Gparted can resize HFS+ partitions visually.

---

### Post by pxwpxw on 2007-06-27
Gparted Live CD seems to be x86, no ppc version.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by aantn on 2007-06-27
> **pxwpxw said:**
> Gparted Live CD seems to be x86, no ppc version.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

I mean the program Gparted that you can install with apt-get (or Synpaptic)

---

### Post by pxwpxw on 2007-06-28
**aantn**

Right, thanks, got it, I knew I was missing something. 
Its good, pity its not available in the ubuntu installer. Maybe in Gentoo. Maybe I can install it from the installer.

---

