---
title: "New to Linux"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by dev on 2006-07-24
Hello.

I have been a windows user for many years and have heard good things about ubuntu, that it is easy to setup for a newbie linux user like me. i would like to give this operating system a try but i have no idea where to begin. what my overall goal is to have windows and ubuntu on the same computer to dual boot; however, i would like to have these OS's on 2 different hard drives (not the same hard drive with 2 partitions). Is this possible to dual boot with windows on a SATA master and Ubuntu on an IDE master??

also, i have heard that the drivers can be an issue for linux users. does ubuntu support dual-core processors?

any help would be appreciated. i would like to have a lean mean computer that does whatever i want it to (as in faster and stable compared to windows).


*edit -  i am very familiar with C / C++ so if there is any programming involved i may be able to do it myself.

---

### Post by reacocard on 2006-07-24
Ubuntu does support dual processors, although not out-of-the-box (it's easy to add). I've seen lots of people on these forums have trouble with Ubuntu and Windows on separate harddrives, but I think it's possible. 

I've never had to do any programming just to get something to work in Ubuntu. If you're looking for a C/C++ IDE for Ubuntu, Anjuta is pretty good.

---

### Post by dev on 2006-07-24
> **reacocard said:**
> Ubuntu does support dual processors, although not out-of-the-box (it's easy to add). **I've seen lots of people on these forums have trouble with Ubuntu and Windows on separate harddrives, but I think it's possible. **

I've never had to do any programming just to get something to work in Ubuntu. If you're looking for a C/C++ IDE for Ubuntu, Anjuta is pretty good.

I really want to use Ubuntu for my first linix distro. The biggest thing that I want to know though is the dual boot. If anyone could help me out with that it would be amazing (as I'd like to install it tonight on my main machine).

---

### Post by MrHorus on 2006-07-24
> **dev said:**
> If anyone could help me out with that it would be amazing (as I'd like to install it tonight on my main machine).

It's easy.

Plug your other drive in and boot off the Ubuntu CD.
Once the isntaller loads, tell it to install Linux onto the spare hard drive and the boot loader will detect your Windows istallation and that's about it :)

---

### Post by dev on 2006-07-24
Very cool, thanks alot! Now the big question I have is do i need to install some kind of third party software in order to have the choice of which hard drive to boot from or should I just tell my bios to load the drive that has Ubuntu only and will that give me a choice to load Ubuntu (on one drive) or Windows (on another seperate drive) ?

---

### Post by Sart on 2006-07-24
> **MrHorus said:**
> It's easy.

Plug your other drive in and boot off the Ubuntu CD.
Once the isntaller loads, tell it to install Linux onto the spare hard drive and the boot loader will detect your Windows istallation and that's about it :)

I did just the same. Now I boot WinXP from C: and Ubuntu from D: Those are differenr HDDs, even manufacturers are different.

---

### Post by Sart on 2006-07-24
> **dev said:**
> Very cool, thanks alot! Now the big question I have is do i need to install some kind of third party software in order to have the choice of which hard drive to boot from or should I just tell my bios to load the drive that has Ubuntu only and will that give me a choice to load Ubuntu (on one drive) or Windows (on another seperate drive) ?

If the installation was OK, GRUB loader will ask you which OS to boot. You do not to alter BIOS.

---

### Post by Christmas on 2006-07-24
Grub Boot Loader will automatically detect Ubuntu and Windows and will give you the option to choose which one you want to load at each start-up. You can even edit the grub configuration file to select which OS should be the default (the default is automatically loaded after a number of seconds, I remember it was 5?).

LE: Here is the wiki page explaining how to put Windows the first option in Boot Loader (Ubuntu is default): [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS").

---

### Post by MrHorus on 2006-07-24
> **dev said:**
> Very cool, thanks alot! Now the big question I have is do i need to install some kind of third party software in order to have the choice of which hard drive to boot from or should I just tell my bios to load the drive that has Ubuntu only and will that give me a choice to load Ubuntu (on one drive) or Windows (on another seperate drive) ?

The bootloader (GRUB) will detect this and configure this automatically - you don't need to configure anything at all.

---

### Post by dev on 2006-07-24
Thank you all very much!!! I will install Ubuntu tonight and hopefully it goes smoothly! :)

---

### Post by Frank Golden on 2006-07-24
GRandUnifiedBootloader. GRUB. Welcome to the world of linux terminology
and Ubuntu. Good Luck and keep an open mind.

---

### Post by confused57 on 2006-07-24
If you want a possible alternate install option:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by VirtuAlex on 2006-07-24
> **dev said:**
> i would like to have these OS's on 2 different hard drives (not the same hard drive with 2 partitions). Is this possible to dual boot with windows on a SATA master and Ubuntu on an IDE master??
That was exactly the setup I used when I first tried Ubuntu. I installed it on IDE. The only small problem was that after I first reboot there were no signs of Ubuntu. Windows started as if nothing happened. I realized that for some reasons it installed boot loader on IDE too, so I had to go to BIOS and specify it to boot from IDE drive. However, as I understand this is exactly what you want - separate disks for separate systems. But it was Breezy. Dapper may behave differently. After I got familiar with stuff I downsized windows partition and moved linux to much faster SATA - my IDE is old and slow and slave to DVD drive because of too short cable for too huge case.
> **dev said:**
> will that give me a choice to load Ubuntu (on one drive) or Windows (on another seperate drive) ?
Yes, Grub boot loader should detect your Windows installation and make an entry in the boot menu. You do not need any third party software. If for some reasons it won't work for you post your problem here and people will help you.
> **dev said:**
> also, i have heard that the drivers can be an issue for linux users. does ubuntu support dual-core processors?
Drivers can be an issue for any system, but if your live CD works then you're okay. Most problems are usually with wireless. I can not say about dual-core. If you have AMD64 you may prefer to install regular 32bit Ubuntu if you do not want to deal with flash/java thingy for firefox, wine and many more 32bit-only apps, but personally I do prefer to deal with issues than go easy way and downgrade.
> **dev said:**
> i am very familiar with C / C++ so if there is any programming involved i may be able to do it myself.
Good for you, I am programmer too, but you do not have to program anything to run linux. It will help, though and I hope you'll enjoy programming in linux. You will. Good luck.

---

### Post by dev on 2006-07-24
Thank you very much **VirtuAlex**!! That is a great help and now I cannot wait to get home and install Ubuntu! You are all proving to me that the Linux community is a great place to learn and help. I appreciate it all immensely! :)

---

### Post by krazyd on 2006-07-24
If you do run into the problem described by VirtuAlex, there is a small free app here which I used in order to use the NT bootloader. It allows you to add other operating systems / boot partitions.
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

Also, it is important not to overwrite the system partition if you don't want to go through complicated and scary stuff in order to not lose your windows installation (I had to do this :( )
This is what MS knowledgebase has to say: 
> The system partition refers to the disk volume that contains the hardware-specific files that are needed to start Windows (for example, Ntldr, Boot.ini, and Ntdetect.com).

NOTE: On dynamic disks, this is known as the system volume.

On Intel 186-and-higher-based computers (only the "x86" line), the system partition must be a primary partition that is marked active. On this line of Intel computers, this is always drive 0: the drive that the system BIOS searches when the operating system starts.

The system partition can, but is not required, to be the same partition as the boot partition.(from: [http://support.microsoft.com/kb/314470/](http://support.microsoft.com/kb/314470/))

I believe this is part of the reason that it is recommended to install Windows first when running dual boot. Ubuntu's installer is smarter I guess. :)

From what I can see, however, you should be fine. I'd guess that the SATA master would be disk 0, though you may want to check it in the BIOS..

---

### Post by arkangel on 2006-07-24
hey dev !

please  tell us how did it go,  you looked so excited ;)  and welcome

---

