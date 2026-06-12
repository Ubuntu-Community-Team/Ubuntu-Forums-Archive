---
title: "[SOLVED] Question on multiple hard drives"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-08-18
I am having a little problem. I installed Ubuntu as a dual boot with Windows XP on a single hdd. I also have a second hdd that I use for all my storage. My problem is that when I first installed Ubuntu it could read, but not write, both partitions and hdd's.  I then installed NTFS Configuration Tool so that I could also write to my storage drive.  It worked for a couple of weeks, but then all of a sudden Ubuntu can't see the Windows partition or the second hdd.  Does anyone have any ideas as to why that happened and how to fix it?

---

### Post by HermanAB on 2007-08-18
You can mount it manually, if you know what the device name is.

$ ls /dev
will show all devices

$ mount
WIll show all mounted devices

The trick is to figure out which device is the unmounted one, then do something like this:
$ sudo mount -t ntfs /dev/hdc /mnt/windows

Google a bit on mounting disk drives to clue yourself in.  Look for the Linux HDD howto on tldp.org.

BTW, you could also try:
$ sudo mount -a

and see if that mounts the missing drive.

Cheers,

Herman

---

