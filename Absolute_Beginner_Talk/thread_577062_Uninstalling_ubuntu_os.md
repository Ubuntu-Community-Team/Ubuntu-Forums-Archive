---
title: "Uninstalling ubuntu o/s"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by herbie_g on 2007-10-15
Hi guys,

I previously had winXP and Ubuntu 7.04 installed, and was really keen to try out the new 7.10 version out. However, after finding that 7.10 wasn't installed over top of 7.04 (rather re-partitioned itself), and that none of my previous settings had been transferred - even tho I asked - I'd now like to find a way to uninstall the 7.10 version and would like to know how to do so in simple terms. There appears to be no documentation within Ubuntu.

Any help would be greatly appreciated!!

Cheers,
Herb.

---

### Post by bodhi.zazen on 2007-10-15
What do you want to do exactly ?

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by MatthewPlanchard on 2007-10-15
Was your original Feisty partition deleted during the process of installing Gutsy?

If not you can just go into Feisty, unmount the Gutsy partition with umount and then use GParted to delete the partition.

Just make sure that once you've updated your partition you update your /etc/fstab file and your /boot/grub/menu.lst

Let me know if you need more detail.

---

### Post by Jive Turkey on 2007-10-15
if I understand correctly you installed 7.10 onto different partitions than your existing 7.04 installation, but you actually intended to overwrite it.

To fix this I think you should boot up your live cd agian and delete the partitions that you didn't actually want and possibly expand the partitions you do want to cover that space, and possibly do a fresh install/format on all but the windows partition and your /home partition 

Don't format your home partiion or your windows partition obviously.  Your settings from before should stay intact as they are stored in your /home folder.

You may also need to edit your grub file and remove any references to the deleted installation, not too sure.

---

