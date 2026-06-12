---
title: "install ubuntu on existing winxp partition"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by pastrami on 2007-03-06
Hey guys, I'm going through my first install with ver6.10 and I'm running into some issues.

I'm mainly following this guide to install on an existing windows partition.
[http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted](http://www.hezardastan.org/breezy_xp_dualboot/en/index.html#createnewpartgparted)

I run into two issues, I'm okay up to creating partition #2, but when creating partition #3, it seems like the guide was able move the "extra" space up one level but I'm able to do that.  The min and max for my extended drive is the same and cannot be changed.

So I create a 3rd partition under it, so under /dev/sda1, I have my 3 new partitions.  When I continue and go to the next screen to mount, I select new partition #1 to be my /home, #2 to be /swap and #3 to be / .  When I click forward it says I need to select a boot partition, although / has to been assigned to partition #3 already.

Hope I'm making sense :)  Any help is greatly appreciated.

---

### Post by dstew on 2007-03-06
Help me understand what you want to do. You have a computer with Windows XP on it, and you want to install Edgy 6.10, correct? When you begin the partitioning process, you have one big partition, /dev/sda1 that is NTFS, right? And you want to make some new partitions out of this space, right?

---

### Post by bks on 2007-03-06
I lost my NTFS partition when I installed 6.06. I'm not sure what happened, but I had to wipe out the entire partition table and start again.

---

### Post by OBnascar on 2007-03-06
I would recommend using the **Gparted Live CD** to set up your partitiions before you install things again. The Live CD is much more user friendly then the install partitioner.

See my signature for downloading the ISO.

---

### Post by pastrami on 2007-03-07
thanks for the replies guys.

I've attached two screenshot of the install, one is the prepare_partition screen and the mount screen.  The exact error I'm getting is "No root filesystem".

The other thing that worries me is, when I hit back to take a screen of prepare_partition, it shows the newly created partitions as unknown but before it was showning ext3 and linux-swap.

Thanks!

I wanted to add that, the /dev/sda1 is my main xp boot partition and I'm installing ubuntu from the free space off of /dev/sda5

---

### Post by dstew on 2007-03-07
I think you have to click the check box to the right of each partition you want to install.

---

### Post by bks on 2007-03-07
You might try a program like Partition Magic to set up you partitons first and then format and install.

---

