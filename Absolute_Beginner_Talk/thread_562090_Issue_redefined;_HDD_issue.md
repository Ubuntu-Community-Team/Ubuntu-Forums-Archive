---
title: "Issue redefined; HDD issue?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by macg.dev.null on 2007-09-28
Ok I stated in my other post, probably long since /null'd by an admin because of inane ramblings, and for that I apologize.

My linux OS Flavor: Ubuntu/feisty 7.04

Having now gotten a better look at the actual error, I'll briefly restate the issue.

Installed WoW via Wine. Rebooted and got the following error when trying to load xserver:

kinit: name_to_dev_t (/dev/disk/by-uuid/136cbbcf-7dda-4df0-90b0-d1827c63d5b9) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/136cbbcf-7dda-4df0-90b0-d1827c63d5b9
kinit: No resume image, doing normal boot...

Ubuntu 7.04 QuantumLeap tty1

QuantumLeap login: _




Now as much of a retarded monkey as I am,I can surmise that this is something to do with the hdd.

Loading up the live cd and running Gpart yeilds the following for my hdd parition tables:

sda1 = primary (/)
sda2 = extended
 >sda5 = logical (swap)

As I stated previously this is my first forray into Linux, so any and all help would be appreciated, thank you in advance

Edit: Found previous thread: [(clicky)]("http://ubuntuforums.org/showthread.php?t=561777")

---

### Post by Natr0n on 2007-09-28
> **macg.dev.null said:**
> 
kinit: name_to_dev_t (/dev/disk/by-uuid/136cbbcf-7dda-4df0-90b0-d1827c63d5b9) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/136cbbcf-7dda-4df0-90b0-d1827c63d5b9
kinit: No resume image, doing normal boot...


This problem has been reported in several other places: [[COLOR="Blue"]Bug #103148 in Ubuntu[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/103148"), [[COLOR="Blue"]Bug #105316 in linux-source-2.6.20 (Ubuntu)[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/105316"), and [ [COLOR="Blue"]kinit: No resume image[/COLOR]]("http://ubuntuforums.org/showthread.php?t=385869&page=4")
Unfortunately, it seems as though the issue remains unresolved. Hopefully, some of the information in the other threads will be useful to you. You might also want to have a look around  the wine website at [[COLOR="Blue"]http://www.winehq.org/[/COLOR]]("http://www.winehq.org/")

---

### Post by USPB on 2007-09-28
I agree experienced this firsthand

---

### Post by macg.dev.null on 2007-09-28
Thanks for the replies folks, looks like I'm just going to repartition and throw XP back on in the meantime until I can find a distro that will *work* for me. I can't afford to have downtime while I deal with inane bugs etc. I am keeping a 6GB slice reserved on the drive however for the eventual linux install.

---

