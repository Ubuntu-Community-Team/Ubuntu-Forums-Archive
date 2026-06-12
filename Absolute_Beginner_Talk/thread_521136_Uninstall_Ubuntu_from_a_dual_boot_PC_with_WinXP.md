---
title: "Uninstall Ubuntu from a dual boot PC with WinXP"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Baby Boy on 2007-08-09
Now that I have my new laptop with Ubuntu, I don't need my desktop, which I gave to my parents. But they don't need Ubuntu, just WinXP, so they want me to uninstall it.
I have the HD partitioned and Ubuntu Feisty Fawn 7.04 installed on one partition and Windows XP on the other. How do I do it without removing the WInXP?

---

### Post by ZipoTe on 2007-08-09
Download this: [gparted live CD]("http://gparted.sourceforge.net/livecd.php") and remove the partitions with it ^^ :)

If you have any troubles, ask here ;)

---

### Post by ZipoTe on 2007-08-09
****, its website does not work... i read the admin can't support gparted live cd anymore!! :-| anyone can post here a link to a mirror or something?

---

### Post by Baby Boy on 2007-08-09
> **ZipoTe said:**
> ****, its website does not work... i read the admin can't support gparted live cd anymore!! :-| anyone can post here a link to a mirror or something?
What are you talkin' about, the site does work :)! Must be something wrong with your internet :p. Now I'll just have to download it and try it.

---

### Post by forestpixie on 2007-08-09
have a look on here for similar threads.

Once you've nuked the Ubuntu partition - you'll be needing an XP disc - or one of the utility discs to sort the MBR before you can get win to start.

---

### Post by Baby Boy on 2007-08-09
Now that I am here, can anyone tell me how to install WinXP onto a Ubuntu only system? 
Actually, it isn't Ubuntu only, my Dell laptop came with FreeDOS preinstalled so I just installed Ubuntu on top of it. How do I delete the FreeDOS and install WinXP? Thanks

---

### Post by Trab on 2007-08-09
easy. grab that XP disc of yours, pop it in, and away you go (shudders....).

just make sure you know which partion is which for the windows partion manager, otherwise you'll be a sad duck.

it may be easier to use your ubuntu partion to REMOVE the FreeDOS partion (gparted or gnome-partion editor will be able to do this) so that windows can just be installed on the unpartioned space (meaning no worries about wiping out ubuntu.

---

### Post by Dedoimedo on 2007-08-09
Hello,
Boot from a live CD, remove the Ubuntu partitions and convert them to free space.
Fix the MBR (insert Windows CD, Recovery Console, fix /mbr at command prompt).
Dedoimedo

---

### Post by Baby Boy on 2007-08-09
> **Trab said:**
> easy. grab that XP disc of yours, pop it in, and away you go (shudders....).

just make sure you know which partion is which for the windows partion manager, otherwise you'll be a sad duck.

it may be easier to use your ubuntu partion to REMOVE the FreeDOS partion (gparted or gnome-partion editor will be able to do this) so that windows can just be installed on the unpartioned space (meaning no worries about wiping out ubuntu.

Help, I am stuck in WindowsXP! I did what you said and just installed WinXP on the other partition but now there is no way to boot Ubuntu when the system starts. I also only see the WinXP partition from the My Computer menu, there is no other part of the HD. :confused:

---

### Post by forestpixie on 2007-08-09
assuming that you stil have the Ubuntu installation you probably need to reinstall grub.

I've seen mention of supergrub - download, copy to a disc. It can be done from the Ubuntu LiveCD as well. Have a look at these

[http://ubuntuforums.org/search.php?searchid=25118670](http://ubuntuforums.org/search.php?searchid=25118670)

Edit - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Edit 2 - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Baby Boy on 2007-08-09
> **forestpixie said:**
> assuming that you stil have the Ubuntu installation you probably need to reinstall grub.

I've seen mention of supergrub - download, copy to a disc. It can be done from the Ubuntu LiveCD as well. Have a look at these

[http://ubuntuforums.org/search.php?searchid=25118670](http://ubuntuforums.org/search.php?searchid=25118670)

Edit - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Edit 2 - [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I did as mentioned in the post from your Edit 2 and now I can only boot Ubuntu :lol:. There is that message 'press escape for GRUB menu in 3,2,1 seconds' on system startup, but in the menu there is only ubuntu. How can I get that nice dual boot menu I got when I installed Ubuntu over WinXP? :(

---

