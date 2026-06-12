---
title: "File Disappeared"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by stueycaster on 2007-10-31
I have Ubuntu 7.10 AMD64 set up in a dual boot configuration along with XP x64. I've only been using Ubuntu for a couple weeks. This computer has two hard drives, one of which is set up in Raid 1. I think Ubuntu reads the partitions on the raid drive as one because it shows only one partition for each. 

I copied some music into a file on one of these partitions. After I rebooted the file had disappeared. It was there and I was able to play songs out of it before the reboot. I'm a complete newby to Ubuntu and I have no clue why it disappeared. Does someone have any idea why this could have happened?

---

### Post by HereInOz on 2007-10-31
Never encountered this before, but my guess would be that it would be in some way related to the way that the raid is being read by Ubuntu, particularly after the reboot.

Perhaps it wrote to only one of the raid HDDs, and is now reading from the other.

It would all depend on whether it is a hardware or software raid, and how you have configured it.

Sorry I cannot be of more assistance.

---

### Post by stueycaster on 2007-11-01
I am under the impression that if Ubuntu isn't reading the raid correctly it shows each partition as two separate partitions. Mine shows only one partition for each. When I set up the Raid it was done with the bios. However MSI does give you software to control the Raid. I don't know if it is real or fake or what.  How do I find out if it's working right?

Is there no other reason why the file would disappear?

---

### Post by stueycaster on 2007-11-01
Amarok shows my partitions as being two separate. I guess Ubuntu is reading my raid wrong. On doing a little research I've found that I need to do a lot more learning about using Ubuntu before I even dream of tackling something as complex as configuring it to read my raid.  I can't write commands at all. Oh well, Later on I guess.

---

