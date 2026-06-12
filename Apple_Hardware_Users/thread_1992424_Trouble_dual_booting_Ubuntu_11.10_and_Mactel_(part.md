---
title: "Trouble dual booting Ubuntu 11.10 and Mactel (partitions won't sync)"
date: 2012-05-31
forum: Apple Hardware Users
---

### Post by sournotessx on 2012-05-31
EDIT: These are the original instructions I followed:
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#Dual-Boot:_Mac_OSX_and_Ubuntu)

So I have tried to dual boot Linux multiple times on my MBP, and every time have run into troubles that lead me to settle for a virtual machine. However, now one of my classes requires a native running version of Ubuntu 12.04 (I planned to upgrade to 12.04 after I got 11.10 running) to learn parallel processing. I just wiped my computer clean and tried to dual boot. I got the Ubuntu 11.10 disc to boot after using boot commands "nomodeset xforcevesa". I installed everything on my hard drive and everything seemed to go smoothly. I rebooted everything and tried to run rEFI's partition tool but got something like:
     Analysis inconclusive, will not touch disc.
     Error not found gptsync.efi

I then booted into the LiveCD and installed gptsync and tried to sync the partition table. I got some output like "Analysis inconclusive, will not touch disc" again.

I then tried to do this:
[http://mac.linux.be/content/problems-refit-and-grub-after-installation](http://mac.linux.be/content/problems-refit-and-grub-after-installation)

Nothing seems to be syncing my partition tables and I cannot boot into the Ubuntu partition.

I have a late 2008 15" MBP:
[http://www.everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-aluminum-15-late-2008-unibody-specs.html](http://www.everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-2-duo-2.4-aluminum-15-late-2008-unibody-specs.html)

I also upgraded to 8gig of RAM if that matters.

I am going to uninstall and reinstall Ubuntu 11.10 right now, and see if anything changes.

Any ideas how to sync my partition table?

UPDATES ARE BELOW IN SUBSEQUENT POSTS.

---

### Post by sournotessx on 2012-05-31
UPDATE: I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)
just without doing anything for windows. I did not get a syncing error, but when I tried to boot from rEFIt I had 2 linux options... Boot Linux from HD and Boot Linux from partition 4. I tried both and neither worked. I then used rEFIt partition tool and it let me sync the table. I then tried both partitions again, and partition 4 started to boot, went to grub, and the froze (crooked purple screen) at boot up. I tried again, and and hung on a black screen with a blinking cursor.

---

### Post by sournotessx on 2012-05-31
And finally this:
[http://askubuntu.com/questions/97007/ubuntu-11-10-hangs-while-booting-and-goes-black](http://askubuntu.com/questions/97007/ubuntu-11-10-hangs-while-booting-and-goes-black)

Think it works now.

---

### Post by sournotessx on 2012-05-31
And now grub says "no such partition" when I try to boot into Ubuntu.

---

