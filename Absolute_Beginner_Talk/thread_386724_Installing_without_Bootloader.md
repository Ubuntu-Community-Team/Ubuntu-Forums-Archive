---
title: "Installing without Bootloader"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by squimmy on 2007-03-17
Hi,

I am going to be installing Ubuntu Ultimate 1.3 soon, and have looked at some videos and screenshots of the Ubuntu installation process. Anyway, I am currently using Vista as my OS and would really not like to install GRUB as I would much prefer to use vista's bootloader(using EasyBCD).


Please tell me there is an option to not install any bootloader. If there isn't, well, that's kinda rediculous.


Thanks.

---

### Post by Rexbron! on 2007-03-17
I believe that you can use vista's bootloader, but you will need to find that info on your own. IMO, grub does everything I need it to and will also autodetect other linux and window installations, something Microsoft's bootloader will not.

---

### Post by squimmy on 2007-03-17
I know I can use GRUB, but i'd prefer it not to overwrite the Vista bootloader.

Don't get me wrong, GRUB's a great bootloader, but I've heard of incompatibility issues with Vista and frankly, i'd just prefer to stick with windows.

So I don't want Ubuntu to rewrite me an MBR, if this is possible.

---

### Post by mcduck on 2007-03-17
If you install with the Alternate CD it should ask you if you want to install Grub. Just say no, and continue the install. After that your real battle begins, to get the Windows bootloader load Ubuntu..

Biggest problem (after figuring out how to make Windows bootloader load any other OS than Windows) would be that after every kernel update you'd have to manually edit the Windows bootloader again to load the new Ubuntu kernel..

---

### Post by Bachstelze on 2007-03-17
Yes but you must use an Alternate CD for that. When it asks you where you want to install GRUB, install it on the boot sector of your Ubuntu partition instead of the MBR.

---

### Post by dstew on 2007-03-17
Here are the instructions to dual-boot Vista and Linux using the Vista bootloader:

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

As mentioned above, install grub into the bootsector of the linux partition, and not into the disk MBR.

One caution: From the Microsoft point of view, Linux is a competitor, and you can be fairly certain that Vista updates will crash your dual-boot capacity, probably in the name of security.

---

### Post by squimmy on 2007-03-18
Okay, but how would I install it onto the boot sector of the linux partition? All the screenshots and videos I've seen of an ubuntu installation seem to suggest that it overwrites the MBR with grub without asking at all. Is this true, or is there a dialog asking where to install it?

Thanks.

---

### Post by louieb on 2007-03-18
> **squimmy said:**
> Okay, but how would I install it onto the boot sector of the linux partition? Thanks.
At some point in the installation most distros ask "Where do I install the boot loader?".  and you give it the answer in GRUB speak. For example In GRUB speak the MBR of the first hard drive is (hd0). A second number is added to refer to a partition on the drive ie. (hd0,2)  would refer to the third partition on the first hard drive.   There is no answer set in stone, the answer would depend on your particular setup.  

First time setup of a dual boot system is not for the squeamish.   You have to do your homework and pay attention to what your doing. Vista hasn't been around long enough to find out how many ways it can be screwed up.

---

### Post by squimmy on 2007-03-18
This isn't the first time i've set up a dual boot system, in the past i've had XP dual booting with:

Suse
SLED
Mepis
Ubuntu (a very old version)
Fedora

So i've tried my fair share of Linux distro's.

But this is the first time I'm doing it with vista, which is making me a little more nervous. I'm not installing it on the same HDD as Vista anyway, so i'm not quite sure how I can screw vista up beyond repair.

My plan is: 

Install Ubuntu on second HDD, install grub to the bootsector of that partition, (hopefully, my comp will still boot into windows at this stage), install EasyBCD, add Ubuntu to the windows bootmanager.

---

### Post by dstew on 2007-03-18
That might work. Try it. You are one of the pioneers of the Vista/Ubuntu dual boot frontier.

---

### Post by squimmy on 2007-03-18
lol, that doesn't make me feel nearly as comfortable as I'd like. Anyway, for now, I can't do anything 'Cos the live DVD doesn't even boot!

I've made a new thread about it here:
[http://www.ubuntuforums.org/showthread.php?t=387560](http://www.ubuntuforums.org/showthread.php?t=387560)

---

