---
title: "Trouble with formatting external usbdrive [resolved]"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by szf on 2007-01-14
I just was entreated to the opposite of "it just works" experience trying to format an external usb drive to ext3.

The base problem was that on every attempt to commit the gparted operation, the drive would be remounted and the operation would fail. I would unmount the drive and try every permutation allowed in gparted - only to get the same end result. I finally thunked down to tty1 and performed cfdisk and mkfs.ext3 on /dev/sda. So much for gui apps making life better.

Some searching after the fact show that my [experience]("https://launchpad.net/gparted/+bug/37768") is a known [bug]("http://bugzilla.gnome.org/show_bug.cgi?id=324220") in gparted version < 0.3. Edgy has gparted 0.2.5 in the repositories, so be aware that trying to check "I've done a fresh backup" off the to-do list will be a *software sucks* experience.

---

### Post by Sef on 2007-01-14
Download [GParted]("http://gparted.sourceforge.net").   It is on version 0.3.3.

---

