---
title: "xp after ubuntu"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by spamcollector6 on 2008-03-10
Hello Everyone,

So i just installed ubuntu and now i want to install xp. I am pretty new to this so I was wondering how I would go about doing this.

Thanks

---

### Post by acirilo on 2008-03-10
Are you wanting to remove Ubuntu or dual boot, run a virtual xp?

---

### Post by Duck2006 on 2008-03-10
This one is on vista but can be done with win xp to.

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by spamcollector6 on 2008-03-10
I already have ubuntu (7.1) installed. so I want to install windows xp on another partition. but i dont really have any idea how to do that. 
sorry if it was unclear

---

### Post by Duck2006 on 2008-03-10
You have to use a partition editer to partition the drive for your xp install.
pmagic is a good partition to edit your drive.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Once your got the space for your win xp install it.
You will have to reinstall grub so you can boot both win and ubuntu and then add the win line to your menu.lst so your can chose witch os you want. This link will help in installing grub and the menu.lst.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by LuisGMarine on 2008-03-10
Ok , so lets get this scenario correct.  You already have ubuntu 7.10 installed on your computer, but you want to install Windows XP on the same hard drive, but different partition?

Go ahead and install xp, to the current partition, make sure you don't select any options where it's going to erase and format the whole hard drive.  After you have installed windows on that partition, you Master Boot Record ( MBR ) is going to be overwritten with the one windows uses.  

Follow this guide:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

 .. to get Ubuntu and windows XP back.  This guide is going to show you how to install GRUB ( Ubuntu's boot manger ) and how to add the option to dual-boot with your old installation of Ubuntu, and your new installation of Windows XP.  I'm going to have to do this for college, so if you run into any troubles I'll monitor the thread and probably can lend you a hand ... or two ;)

Good lUck!!!!!

---

### Post by Duck2006 on 2008-03-10
> **spamcollector6 said:**
> I already have ubuntu (7.1) installed. so I want to install windows xp on another partition. but i dont really have any idea how to do that. 
sorry if it was unclear

Ok this was the link i was looking for as to the how to for install win xp after linux.

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by spamcollector6 on 2008-03-10
okay ill try this. Thanks everyone :)

---

### Post by SunnyRabbiera on 2008-03-10
just remember XP is a hog, so it might want to wipe ubuntu off your drive.

---

### Post by Elastoman on 2008-03-10
I'm facing a similar issue, but I'll have Xubuntu and XP on separate physical drives - can I use GRUB with Xubuntu (primary drive) to allow me the option of booting to XP on the second HDD?  It seems like it should work without a hitch, but everything seems that way until your eyeballs deep in hitches.

Thanks!

---

