---
title: "Grub disappeared??"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by madhartigan on 2007-04-07
Hi there!!

This is my first time posting here and I'm glad I found this forum.

I'm very interested in Ubuntu/Linux and all there is to learn about Open Source operating systems.

First off, let me describe my system:

OCZ GameXStream 850W
DFI Lanparty UT nF4 SLI-DR Expert (Merlin's BIOS)
Opteron 165 (310MHz x 9) 2790MHz s/Thermaltake Big Typhoon 120mm
OCZ Platinum Edition 2GB (2 x 1GB) 184-Pin DDR SDRAM DDR 500 (PC 4000)
IDE Channel 1 Master - Maxtor 300GB
IDE Channel 2 Master - NEC ND-6750A DVD-RW
SATA Disk 3 WD Raptor 74GB 
SATA Disk 4 WD Raptor 150GB
SATA Disk 1 WD 500GB  
SATA Disk 2 WD Raptor 150GB
eVGA 7900GTX x2 SLi Mode
Creative X-Fi Elite Pro
Logitech G15
Kensington Expert Mouse
Razer Copperhead Mouse

I guess the best way to present my question is to narrate the steps I've gone through to get to where I am now.

1) I installed Windows Vista Ultimate on a 40GB partition of the 74GB Raptor.

2) I installed Ubuntu 6.06.1 x64 on the remaining space of the 74GB Raptor.

3) At the end of the Ubuntu install I rebooted and Grub loaded, no problem.

4) I edited my menu.lst in /boot/grub so Windows Vista would load.  I did this by adding the following entry to the top of the list of Ubuntu load commands:

title               Windows Vista
root               (hd0,0)
makeactive
chainloader     +1

I then saved menu.lst.

5) I rebooted the system to ensure I could load into Vista and Grub loaded, I hit ESC, selected the Vista line and everything booted with no problems.

6) I was then able to go back and forth between Vista and Ubuntu with no problems.

7) THEN, yesterday, Grub just stopped loading.  I made no changes to the Ubuntu partition, I made no changes to menu.lst.  Essentially, I made no changes except for . . . installing all of the Vista updates.  From what I read of the Vista updates none of them had anything to do with the MBR or booting in any capacity.

So, I'm wondering where did Grub go?  How do I get it back?  Whenever I load the Ubuntu Live CD I'm unable to access the partition on which I've installed Ubuntu so I can check the menu.lst file, I'm not even able to enable it.

I'd really love to use Ubuntu and learn more about it but, these types of issues (I'm was also having trouble getting the latest nvidia drivers loaded) are a source of frustration.

I'm dedicated to this so I'll definitely stay patient and keep plugging away but at this point I can't even get to Ubuntu to work with it.

Any help would be greatly appreciated.

-hartigan

---

### Post by dstew on 2007-04-07
When you boot the computer, do you see messages from grub, or does it just go straight to Vista?

---

### Post by madhartigan on 2007-04-07
Thank you for the prompt reply!!

It goes right to Vista, there's no evidence of grub.  It's like it just disappeared.

-hartigan

---

### Post by caffienefree on 2007-04-07
You can try this process to restore grub.

[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by madhartigan on 2007-04-07
Using the method you mention caffeinefree, once I get to step 4, I don't see how to mount /, /root and swap.  I've attached a screenshot to reference.

[img]http://ubuntuforums.org/attachment.php?attachmentid=29185&stc=1&d=1175958765[/img]

I'm not sure what to do using the restore grub method.

Sorry for my n00bness.

-hartigan

---

### Post by Maestro23 on 2007-04-07
Don't forget SuperGrub: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by confused57 on 2007-04-07
You can use the live cd to restore grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I agree, making a Super Grub Disk is a good idea.

---

### Post by madhartigan on 2007-04-07
Thanks to all for the help!!

I went ahead with the method suggested by confused57 and that worked!!

I'm still curious as to what exactly caused this issue but, I'm happy enough to move on from here.


Now, I'm off to battle the attempt to install the latest nvidia drivers.  Wish me luck.


Thanks again to everyone for their assistance.

-hartigan


PS - If you have any suggestions for loading the nvidia drivers before I go slogging through this effort, I'm open to anything.

---

### Post by Maestro23 on 2007-04-07
> **madhartigan said:**
> Thanks to all for the help!!

I went ahead with the method suggested by confused57 and that worked!!

I'm still curious as to what exactly caused this issue but, I'm happy enough to move on from here.


Now, I'm off to battle the attempt to install the latest nvidia drivers.  Wish me luck.


Thanks again to everyone for their assistance.

-hartigan


PS - If you have any suggestions for loading the nvidia drivers before I go slogging through this effort, I'm open to anything.

Glad you got that worked out.  Here's some links to get you started with Ubuntu:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by dstew on 2007-04-07
> I'm still curious as to what exactly caused this issue but, I'm happy enough to move on from here.


Maybe a Vista update does mess with the MBR of the first disk. I am sure we will find out as more people dual-boot Vista and Linux. My guess is that Vista does not respect the presence of another operating system or boot loader on "its" system.

---

### Post by Maestro23 on 2007-04-07
> **dstew said:**
> Maybe a Vista update does mess with the MBR of the first disk. I am sure we will find out as more people dual-boot Vista and Linux. My guess is that Vista does not respect the presence of another operating system or boot loader on "its" system.

Seems like I have read this somewhere as well.  Man, that is bad for dual-boot people if it's true.

---

### Post by madhartigan on 2007-04-07
*update*

I got through the nvidia install with minimal problems.

My biggest obstacles were figuring out that I needed to replace the word "generic" with the entire string returned from uname -r in this line:

```
sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config
```

The other thing I had to figure out was exiting out of x-server while I was in the console (Alt-Ctrl-F1)

I used:

```
sudo init 3
```

and once the driver was installed and I was ready to return to gdm, I used:

```
sudo init 5
```



I mention this, not so much for those of you who helped me but, for beginners who may be reading this thread and installing the nvidia driver is their next step.

Thanks again for all the help.

-hartigan

---

