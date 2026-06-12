---
title: "Can't erase Linux ext2 partition on my Mac"
date: 2009-02-18
forum: Apple Hardware Users
---

### Post by Hagablog on 2009-02-18
I have on a USB external a Linux partition in ext2; I can't erase it from within Linux because it wont boot ([See here]("http://ubuntuforums.org/showthread.php?t=1062702")) hence the reason I'm doing it. My goal is to have a single partition that I can reinstall linux onto. Disk Utility used to be able to repartition over the ext2 but now won't, saying

[FONT="Courier New"]Disk Erase failed with the error:

Operation timed out[/FONT]

This happens when creating the partition map. I think I've narrowed the problem down to the Linux partition which when I try to erase says

[FONT="Courier New"]Disk Erase failed with the error:

Could not unmount disk.[/FONT]

I find this a bit funny because the disk isn't mounted because OS X can't read ext2 (I couldn't get ext2fs to work), see my puzzle?

Thank you in advance

---

### Post by cyberdork33 on 2009-02-18
boot the Ubuntu LiveCD and run the partition editor (gparted). It will allow you to completely reformat the hard drive. 

You will have issues trying to install and boot from an external hard drive anyway. See the Apple Intel FAQ at the top of the forum.

---

