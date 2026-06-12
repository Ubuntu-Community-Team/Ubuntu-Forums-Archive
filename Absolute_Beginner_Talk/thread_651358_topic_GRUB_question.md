---
title: "topic GRUB question"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by reality_hunter on 2007-12-27
Hi, I have been using UBUNTU for almost a year and always learning something new about it whenever testing it out if not working on it.
The other day I did a clean Install of Gusty and XP and I noticed something which I want some help/advice for.

my computer setup is:
2 harddisk (HD) - one is 250GiB '/dev/sda' and the other 40GiB '/dev/hda'
-I installed XP first on the 250GiB HD - clean install, format.
-then I used "gparted-live cd" and partition the HD as:
	/dev/sda1 - has windown
	/dev/sda2 - mount pt "/" ext3 - this is set at the begining 
	/dev/sda3 - swap
- after that I used the UBUNTU live cd for the gusty and finally installed everything and it went smoothly

But now in the BIOS I said to boot from the HD sda (250 GiB) one, and it gave a grub error, where as if I had said to boot from the HD hda (37 GiB) one ...it loaded the grub and I can run UBUNTU and XP.  
question is that why did it installed the grub loader on the smaller HD and not the one where both OS are? The reason for posting this is because I was going to take out the 40GiB HD out the computer and replace it with 500GiB external USB HD that I got for christmas.  If it makes any difference, the hda (40 GiB) also have XP installed on it and if I am not mistaken before the clean install, I was booting from this smaller drive and it was loading GRUB from there also -- because before on the SDA (250 GiB) HD UBUNTU was the the only OS.
How do I install and load grub from the main (250 GiB) HD as this will be the only HD left once I uninstall the 40GB hd ???
I wish I would have taken out the HD first before doing fresh install ....but there has gotta be an easier way to this, please help.

thanks :)

---

### Post by gn2 on 2007-12-27
Since 7.04 Grub goes where you put it.
Where it's installed isn't important because you can easily re-install it using a SuperGrub CD: 

[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)

Main Page (site down at the moment) [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Hermanzone SuperGrub instructions: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by meierfra on 2007-12-27
Supergrub won't be able to solve you whole problem. You will also have the edit "menu.lst". But  the whole thing is fairly easy to do. and if  you post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

I can give you detailed instruction.

---

