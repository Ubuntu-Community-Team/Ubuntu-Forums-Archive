---
title: "Does Ubuntu 6.10 auto resize Windows partitions?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Bob_12 on 2007-03-01
Does Ubuntu 6.10 auto resize Windows partitions? I have Windows on a machine that I dont want to completely reformat. Will Ubuntu straight up resize my partitions/add a linux one automatically?

---

### Post by kelbizzle on 2007-03-01
you'll want you probably defrag your hard drive in safe mode a couple times.  Ubuntu has done a good job for me because I just back up XP, Reinstall XP,Restore the backup and then when I Install ubuntu... I just have it resize the partition and install on the free space.

---

### Post by HereInOz on 2007-03-01
During the installation process, the Ubuntu installer will detect the presence of the Windows partition and there will be options presented to you as to what you want to do with the existing partition and the free space that can be created.

It is easy to get this wrong, if you answer incorrectly, if you do not understand what is being asked, so tread carefully grasshopper, but yes, it is quite achievable to have a dual boot scenario and get the Ubuntu installer to sort the partitions out for you.

However, if this is the first time you have been down this track, and being the careful type I am, what I would suggest is:  Disconnect your current HDD, and get hold of another hard disk - it only needs to be an old 30 or 40GB type of thing - plug it in and do a quick install of Windows (version of your choice) on it.  Don't bother updating or anything like that; just get a working Windows installation on the temporary HDD.   

Then install Ubuntu on it, and see what goes on through the install process, and make sure that you know what you are doing before you unleash yourself on the real Windows installation.  Once you are comfortable with what you are going to do, and you know that you are not going to mess up the real Windows installation, replace the original hard disk and go for it.  I would still back up any irreplaceable data though, just in case. 

Hope this helps.

---

### Post by kelbizzle on 2007-03-01
Just to add. It might not install on your xp partition depending on how fragmented your drive is. I've just setup dual boot partitions on both of my friends machines. With out any defrag whatsoever from me or I'm sure my friends. Ubuntu would not resize the partition of either of the hard drives. It said it had failed and wanted to completely erase the drive. So I did what I normally do just retrieved their Cd key and reinstalled XP, and installed Ubuntu on a fresh install.

---

### Post by Bob_12 on 2007-03-01
Thanks for all the help. I was hoping to avoid reinstalling XP, but it might just be unavoidable. I have two HDs, if I just choose to reformat and reinstall XP and the Ubuntu on one it wont affect the other, correct?

---

### Post by Kateikyoushi on 2007-03-01
You do not have to reinstall XP because you installed ubuntu. You have to defrag your XP partition, depending on how fragmented it is, maybe deactivate swap and hibernation then defrag turn them on, but that should do it.

Here is a link to a dualboot installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

Before you resize the partitions do not forget to backup important data, better late than sorry.

---

### Post by Bob_12 on 2007-03-01
Thanks, I'll read the guide. Sorry for my ignorance.

---

