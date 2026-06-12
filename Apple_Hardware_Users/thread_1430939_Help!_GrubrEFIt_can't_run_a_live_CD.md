---
title: "Help! Grub/rEFIt can't run a live CD"
date: 2010-03-16
forum: Apple Hardware Users
---

### Post by Jheric on 2010-03-16
I decided that I wanted to take Arch for a spin for the next week or so (I've had Ubuntu installed for a while) and so I thought the logical thing to do was to erase my partitions and start over with a new live cd...

Well.. that didn't work. I tried to do it from Disk Utility in OS X which succeeded in deleting most everything... EXCEPT grub is still in the mbr (or whatever it runs from through rEFIt). But all I see when I start up in the non-OS X partition is:  

```
GRUB
```

At any rate, no Live CDs work, I can't delete the partitions from OS X (including after booting up from the OS X Install disk).

If I hit F1 I can get the "grub>" prompt. But I can't figure out how to launch a live cd. To my knowlege, there's not a "bios" for rEFIt where I can force it to boot from CD, is there?

Ugh... Any help is GREATLY appreciated!

---

### Post by Jheric on 2010-03-16
Is there a way to uninstall grub manually? I have no OS to boot too besides OS X, grub isn't working, and live-CDs are not starting up. :<

---

### Post by Jheric on 2010-03-16
This is crazy... I think the only way I can fix this is either to buy iPartition (which I don't want to do) or reformat my entire computer... all do to 1 900k partition that has GRUB on it...

I really don't want to do that, but there doesn't seem to be any way to reformat these partitions without a live-cd and I can't get one to work. There's no "BIOS" to force a live CD... and I've tested about 5 different distro disks with no success. 

The OS X disk can boot up... but even it can't delete the boot partition that's causing the problem. Neither can a root instance of Disk Utility.

I also upgraded to the latest rEFIt. After re-syncing, that didn't effect the problem either. What a pain in the butt...

An evening experiment just turned into an all-night mess and a future weekend project :<. 

Of course... I guess I could just stay on OS X... but... meh... dislike....

---

### Post by linuxopjemac on 2010-03-16
[http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot-anymore](http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot-anymore)

You can also do it from within Linux:
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18)

---

### Post by Jheric on 2010-03-16
> **linuxopjemac said:**
> [http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot-anymore](http://mac.linux.be/content/remove-grub-under-osx-if-osx-wont-boot-anymore)

You can also do it from within Linux:
[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=18)

Finally @_@... that worked. Tanks so much for the link!!

---

