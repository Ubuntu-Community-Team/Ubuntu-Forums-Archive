---
title: "First Time Install - Busy Box error?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by squirrel_f13 on 2007-02-07
Hey all - first time linux user here. Very impressed at how easy Ubuntu was to install (except for this one issue) and how customizable and responsive it is.

Anyway - the issue:

I get this error if my 3rd SATA drive is attached on boot:

BusyBox
/bin/sh: can't access tty; job control turned off
(initramfs)

3 400Gb SATA drives are installed:

sda
sdb
sdc

I installed over a Windows Vista RC2 install - formatting the Vista partition and reformatting it as ext3 during the Live CD install. Once the install was complete and I rebooted I got a "Operating System Not Found. Insert Disk and Hit Any Key" error.

So I unplugged the SATA drives until I found a combo that allowed me to boot up - which is currently:

sda1 - ext3 boot partition
sda2 - extended
sda3 - Swap

sdb1 - NTFS (mounted through fstab addition)
sdb2 - ext3 partition of extra space (mounted)

So my 3rd SATA drive is the problem - it is a 400 gig drive with only about 18 gig free on it (movies and music) formatted in Vista as NTFS. If I reconnect it the system throws a BusyBox error after post/Ubuntu splash.


What should I be looking to do to be able to hook up and mount the 3rd SATA drive?

EDIT: Also I have searched around to try and understand - just not sure if it's media.lst or another file I should be investigating?

---

### Post by riven0 on 2007-02-07
Try posting your fstab file here. I'm not sure if I can help, but it may be some kind of naming conflict between your drives. So open the terminal and copy and paste this:

> cat /etc/fstab

---

### Post by confused57 on 2007-02-07
For what it's worth, I left a reply in your other thread:
[http://www.ubuntuforums.org/showthread.php?t=355208](http://www.ubuntuforums.org/showthread.php?t=355208)

---

### Post by squirrel_f13 on 2007-02-07
Thanks gents, have posted more info in that other thread as it seems a more appropriate forum.

---

