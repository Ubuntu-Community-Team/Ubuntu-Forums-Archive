---
title: "Locked Partition"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by JamesF on 2006-12-03
I'm trying to uninstall Ubuntu from my laptop and am unsure how to go about this. I used Partition Magic under XP to create a partition for Ubuntu so I could dual boot. I've now installed Ubuntu solely on my desktop and need to turn the laptop back to a full XP machine (it needs a repair and the warranty  will probably not like what I've done).

I thought simply booting to XP and using Partition Magic to delete the Uvbuntu partition would do the trick but it doesn't. I keep getting an error notice saying *"I can't lock a locked partition"* Can anyone advise me please?

---

### Post by taurus on 2006-12-03
If you still have the Ubuntu LiveCD, boot from it and use gparted to remove the partitions.  Then, convert that one big harddrive to ntfs.  Now, just install your XP from the CD...

---

