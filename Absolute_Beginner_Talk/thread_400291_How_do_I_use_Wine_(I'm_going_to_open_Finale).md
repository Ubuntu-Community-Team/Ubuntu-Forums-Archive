---
title: "How do I use Wine? (I'm going to open Finale)"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by ArnsteinK on 2007-04-03
Can anyone give me a step-by-step guide to how to open Wine and install and use Finale(a music notation application)? Thanks in advance!

---

### Post by Ted D. on 2007-04-03
> **ArnsteinK said:**
> Can anyone give me a step-by-step guide to how to open Wine and install and use Finale(a music notation application)? Thanks in advance!

Go to the link below.

[http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)

---

### Post by xopher on 2007-04-03
This one's pretty good: [https://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54](https://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54)

---

### Post by bodhi.zazen on 2007-04-03
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by ArnsteinK on 2007-04-03
I tried to install it, but when it came to the end of the installation the installation-thing closed! the exe-file was there though, and I tried to open it but it didn't work! What can I do?

---

### Post by Verbatim9 on 2007-04-03
If Finale installed correctly, you should find it listed in your applications menu...a separate folder for all of your Wine apps should have appeared automatically...is that where you're trying to launch it from?

You may also want to look at the info on [using Finale w/ Wine](http://appdb.winehq.org/appview.php?iAppId=454) from WineHQ's application database. The comments about Finale 2006 say you need to install a specific DLL before Finale will work correctly, and give some directions for doing so...there's a little info on all the other recent versions, too...at least one also needs an extra font pack that you can download from the Finale site. It looks like most people who left comments have been able to get Finale running, albeit not 100% perfectly.

---

### Post by ArnsteinK on 2007-04-04
Thanks, I've done that now! Now it's two problems:

1. Finale closes when I try to save
2. No sound

How do I fix this?

---

### Post by ArnsteinK on 2007-04-04
And I get this message when I start Finale: Failed to start VST engine. VST services are unavailable.

---

### Post by ArnsteinK on 2007-04-04
I have given up! So now I'm wondering: does it work fine to install Windows XP on the machine and still have Ubuntu? Or will it affect it? Maybe I will install Windows 2000 instead of XP. Do you think that will work fine?

---

### Post by Warpnow on 2007-04-04
You can do that with vmware. It runs one OS inside of another.

You can also dual-boot, but you'd have to reinstall.

---

### Post by Verbatim9 on 2007-04-04
You can install both Ubuntu and Windows on the same machine, but I think it's usually easier to install Windows first...Linux utilities are fairly good at stealing free space from a Windows partition to make a Linux partition, usually without data loss (though you should back up your data beforehand even in that case). I'm not sure what the situation is like trying to steal space from a Linux partition to make an NTFS partition, and installing Windows on it, but you should definitely back up any data you care about first.

Unless you already have an empty partition, or plan to add a second hard drive, you'll need to use Linux utilities to reduce the size of your Linux partition, and then add a new NTFS partition (I'm not sure whether Linux utils can create an NTFS partition...you might need to use your XP CD or a third-party utility...you should be able to create a new NTFS partition on a drive that has unpartitioned space during the XP or 2K install, but be careful, since you could wipe out your Linux and swap partitions if you choose the wrong option). If you can get an NTFS partition without destroying your Linux partition, you should be able to install Windows on it without destroying your Linux install, again, provided you're careful to make the right choices during the Windows install process.

Once the Windows install is complete, you may not be able to boot into Linux without restoring your boot sector (which can be done using the Ubuntu install disk)...once you restore the Ubuntu boot sector, since your Windows partition didn't exist when you installed Ubutu, you'll find you can't boot into Windows...you'll have to manually modify GRUB to make Windows available in the boot menu. (I'd point you in the right direction for info on how to edit GRUB...but I haven't gotten around to figuring it out myself yet...shouldn't be too hard to track down, though).

---

### Post by kygil on 2007-04-04
I've downloaded wine via the repository, now what steps do I take to get citrix to work?

---

