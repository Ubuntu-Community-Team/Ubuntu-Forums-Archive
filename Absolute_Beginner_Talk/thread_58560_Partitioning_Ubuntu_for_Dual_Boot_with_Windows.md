---
title: "Partitioning Ubuntu for Dual Boot with Windows"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by kozmo on 2005-08-20
I have seen posts about installing Windows first, then Ubuntu. But I already have Ubuntu installed on my laptop. How do I...

Create a secondary partition on Ubuntu to install Windows on...
Setup GRUB to prompt me which OS I want to boot up.

I'm using Hoary 5.0.4

---

### Post by humanity_to_others on 2005-08-20
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by AnythingBut on 2005-08-20
[QUOTE=kozmo]Create a secondary partition on Ubuntu to install Windows on...
[/QUOTE]

A program called parted should do the trick for you.  To use it, you're going to have to create a boot disk since you want to change your root partition (I'm guessing).  Check out parted's documentation.  In particular, [how to create a boot disk with parted on it](http://www.gnu.org/software/parted/manual/html_chapter/parted_1.html#SEC7).  Using parted, you'll be able to shrink the partition.  Boot off the windows CD and install on the unpartitioned space.

Then follow the instructions humanity_to_others posted a link to.  You'll have to use your Ubuntu installation CD in rescue mode (see link).   This will let you boot into Ubuntu, but not windows.  Once you can get back in Ubuntu follow [http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu) to get a Windows entry in GRUB.  Most likely, you'll have to change "root (hd0,0)" to something else.  Note that grub's drive and partition indices start at 0.  (hd0,0) = /dev/hda1

Let us know if this works out for you.

---

### Post by user1397 on 2006-04-10
[QUOTE=AnythingBut]A program called parted should do the trick for you.  To use it, you're going to have to create a boot disk since you want to change your root partition (I'm guessing).  Check out parted's documentation.  In particular, [how to create a boot disk with parted on it](http://www.gnu.org/software/parted/manual/html_chapter/parted_1.html#SEC7).  Using parted, you'll be able to shrink the partition.  Boot off the windows CD and install on the unpartitioned space.

Then follow the instructions humanity_to_others posted a link to.  You'll have to use your Ubuntu installation CD in rescue mode (see link).   This will let you boot into Ubuntu, but not windows.  Once you can get back in Ubuntu follow [http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu) to get a Windows entry in GRUB.  Most likely, you'll have to change "root (hd0,0)" to something else.  Note that grub's drive and partition indices start at 0.  (hd0,0) = /dev/hda1

Let us know if this works out for you.[/QUOTE]
Does this actually work? I mean have you tried it yourself?

---

