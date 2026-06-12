---
title: "64bit to 32bit"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Jexel on 2007-06-26
Currently I have 64bit Ubuntu, since there's all these incomaptiblities around and I don't really want to go through a tutorial to get every little thing working, I would like to go back to 32bit Ubuntu.

How would I go about in doing this? Currently I'm also dualbooting with Vista so would that complicate matters?

Thanks for the help.

---

### Post by starcraft.man on 2007-06-26
Reinstall Ubuntu from a 32 bit CD of your choice (alternate or Desktop, whichever worked first time around).

[You can find a good mirror here with all the versions.]("http://releases.ubuntu.com/7.04/")

Download and burn, then make sure when your doing the installer you manually set the partitioner to overwrite the / (root) directory you used before. It's fairly straight forward, any problems or you need me more specific just ask.

There isn't any easier way, you can't just apt-change the architecture unfortunately. Good luck with that.

---

### Post by Jexel on 2007-06-26
wow didn't know it would be that easy, would that overwrite everything?

Also, how would I be able to allocate more space to my Ubuntu partition? Cause currently only 10 gigs is allocated to it, I want to allocate another 10 gigs just to be safe. I followed the guide from here: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by starcraft.man on 2007-06-26
> **Jexel said:**
> wow didn't know it would be that easy, would that overwrite everything?



Yes, it is that easy. Do make sure you back up any data or custom things in the Ubuntu partition, it will _FORMAT_ the partition and overwrite almost everything.

> Also, how would I be able to allocate more space to my Ubuntu partition? Cause currently only 10 gigs is allocated to it, I want to allocate another 10 gigs just to be safe. I followed the guide from here: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

GParted Live CD. [Download it here (middle link).]("http://gparted.sourceforge.net/download.php")

Burn, and boot to it. Will let you edit any partitions. If you need more explanation how it works read over the documentation section, its well written with pictures of what to do. You can easily then resize any partition.

One word of warning, resizing Vista partitions with it (assuming you don't have spare space) has caused problems for some people, your supposed to use the vista partitioner apparently... Oh and IMO, 10 GB for the root partition is more than enough. What I would recommend is giving yourself a /home partition/folder for storing media/files. A typical root install will never exceed 8 GB, its only really the home folder that gets really really big with media and downloads.

[Link about home partition.]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Jexel on 2007-06-27
i managed to install 32bit ubuntu successfully, however, i can no longer set my resolution to what it was before which was "1680x1050" it now peaks at 1024x768.

Nevermind got it working by editing xorg.conf

---

