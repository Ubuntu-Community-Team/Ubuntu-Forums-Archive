---
title: "Unable to mount the selected volume:mount: /dev/scd0 is not a block device"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Rajagopal S on 2007-06-14
I'm a complete beginner to Linux. I installed the OS only today and havent gone through any of the documentation.
When I insert a CDROM/DVD into my combo drive nothing happens.
If I go to the filesystem and double click on the cdrom0 icon it says:
Unable to mount the selected volume:mount: /dev/scd0 is not a block device

Please tell me how to solve this problem...

There was a similar question in some other post but I tried all that was given there and it did not work for me...

I badly want to get this thing solved by today...SO kindly help me out...

---

### Post by shearn89 on 2007-06-14
hey, just did a quick google for it, got this:
[http://linuxmafia.com/faq/VALinux-kb/cdrom-not-valid-block-device.html](http://linuxmafia.com/faq/VALinux-kb/cdrom-not-valid-block-device.html)
sounds fairly similar.

Basically, first check the cable. Then i'd recommend doing the bit about /dev/cdrom: go "places -> filesystem" then click "dev" and see if there is an icon saying "cdrom" with a little blue arrow in the corner (like a windows shortcut emblem).
If that still doesn't work, you could try checking dmesg: applications -> accessories -> terminal, then type "dmesg" and scroll through the output looking for "cdrom recognised" or something similar....

I'm afraid i'm not as knowledgeable as others on this forum, but i'll do my best!

---

