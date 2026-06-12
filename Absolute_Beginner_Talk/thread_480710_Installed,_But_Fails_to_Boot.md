---
title: "Installed, But Fails to Boot"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by grgramps on 2007-06-21
Downloaded 7.04, burned disk and installed on a separate hard drive that was empty.  When I boot, I am taken to WinXP.  I am not given the option of Ubuntu.  If I boot with the disk, I get to Ubuntu but it wants to install again.   (I have no experience with Linux, although I worked briefly with Venix many years ago, before switching to Win3.1)
Don't know if this could be an issue, but the IDE drive with Ubuntu is connected to a Promise controller as the motherboard has only one IDE connector.
One reference that I read mentioned that the "bootable flag" should be turned on.  I saw no such option during partitioning or installation.  Any help will be much appreciated.

---

### Post by overdrank on 2007-06-21
> **grgramps said:**
> Downloaded 7.04, burned disk and installed on a separate hard drive that was empty.  When I boot, I am taken to WinXP.  I am not given the option of Ubuntu.  If I boot with the disk, I get to Ubuntu but it wants to install again.   (I have no experience with Linux, although I worked briefly with Venix many years ago, before switching to Win3.1)
Don't know if this could be an issue, but the IDE drive with Ubuntu is connected to a Promise controller as the motherboard has only one IDE connector.
One reference that I read mentioned that the "bootable flag" should be turned on.  I saw no such option during partitioning or installation.  Any help will be much appreciated.

Hi it might be the promise raid device. Try and change your bios to boot to the raid device first and see if ubuntu is there. :-k

---

### Post by paparucino on 2007-06-21
> **grgramps said:**
> 
One reference that I read mentioned that the "bootable flag" should be turned on.  I saw no such option during partitioning or installation.  Any help will be much appreciated.
Are you sure you installed GRUB, the boot loader?

---

### Post by grgramps on 2007-06-22
Was I incorrect to assume that the GRUB would have been included with the installation?  What's next?  Now you see why I'm posting in the "Absolute Beginner" portion of this forum.

---

### Post by overdrank on 2007-06-22
> **grgramps said:**
> Was I incorrect to assume that the GRUB would have been included with the installation?  What's next?  Now you see why I'm posting in the "Absolute Beginner" portion of this forum.

Hi yes the grub should have been installed with ubuntu. Did you have any luck with the booting to the raid device? If your motherboard does not have raid choice does it have a choice like other?
You may also try the live cd and reinstall grub using this thread
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by grgramps on 2007-06-22
Overdrank, it's not a raid controller- it's just a controller to offer additional connections for a motherboard offering only one IDE connector, but lots of SATA connectors.

The instructions clearly state that the "bootable flag" should be turned on.  Since I did not get the option, I wonder if these instructions are for an earlier version of Ubuntu?

The referenced thread, [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) goes on for 15 pages.  Very interesting but I did not succeed.  I have serious doubts that I have a GRUB anywhere on the disk.

So now I am wondering if one of the earlier versions might be easier for me to install or if there is another distro that you might recommend for a beginner.  I actually expected that this would be an easy install since I had a drive to devote exclusively to Ubuntu.

---

### Post by overdrank on 2007-06-22
> **grgramps said:**
> Overdrank, it's not a raid controller- it's just a controller to offer additional connections for a motherboard offering only one IDE connector, but lots of SATA connectors.

The instructions clearly state that the "bootable flag" should be turned on.  Since I did not get the option, I wonder if these instructions are for an earlier version of Ubuntu?

The referenced thread, [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) goes on for 15 pages.  Very interesting but I did not succeed.  I have serious doubts that I have a GRUB anywhere on the disk.

So now I am wondering if one of the earlier versions might be easier for me to install or if there is another distro that you might recommend for a beginner.  I actually expected that this would be an easy install since I had a drive to devote exclusively to Ubuntu.

Ok I understand it is not a raid controller. But the motherboard bios has a boot sequence that it has to choose from ie floppy, cd, hd. since you install on that controller that is where the grub is. Ubuntu see it but the motherboard is not booting to it. So that is why I was asking if the motherboard has a extra choice to boot from like other. If not then you can use the live cd and install the grub on the ide hard drive that way you can boot to ubuntu. :(

---

### Post by grgramps on 2007-06-22
Overdrank, I appreciate your continued efforts, but I don't seem to be making any progress.  I have gone into bios and could see the controller card and the 40 Gb drive on which I have installed Ubuntu.  However, I was unable to change bios to allow booting from that disk.  The WinXP drive is a SATA drive and I believe I read somewhere that the sata drive had to boot before others?  (The MB is an Intel DG965RY)

My C:\ drive (SATA) is partitioned, with XP on the first part and the other partition is free.  Would you suggest that I use D:\ , the remaining partition to try installing Ubuntu?

I have the feeling that you don't like to give up?;)

---

### Post by grgramps on 2007-06-22
Oh my, it's starting to look serious.  The internet has much to say about loading linux to SATA hard drives and more info on the use of the Promise Ultra100 TX2 controller.

No idea where this leaves me.  Perhaps I should put one of these IDE drives in the old computer, add a floppy, cd drive and try that.

Anyone have a better idea?

---

### Post by grgramps on 2007-07-15
One kind individual got on the phone with me and talked me through the installation.  GRUB is placed and I have a dual boot that works.  Thanks for your assistance.

---

### Post by overdrank on 2007-07-15
> **grgramps said:**
> One kind individual got on the phone with me and talked me through the installation.  GRUB is placed and I have a dual boot that works.  Thanks for your assistance.

Glad to hear! :popcorn:

---

