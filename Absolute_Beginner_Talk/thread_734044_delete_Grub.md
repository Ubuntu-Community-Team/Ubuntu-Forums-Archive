---
title: "delete Grub"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by El French0 on 2008-03-24
I have had the worst time with ubuntu, there aren't any suitable drivers for my laptop's speakers, webcam, microphone, videocard, and mic/headphone jack.....  I have uninstalled ubuntu and am trying to reinstall windws but GRUB woln't let me boot any windows cds, even when holding r and everything, the only thing it will let me boot is fedora and ubuntu live cds.  There has to be a way to delete grub....

Please, help me out of this linux hell!!

---

### Post by LowSky on 2008-03-24
GRUB shouldn't be messing with your Windows Install CD,in fact it cant mess with it as your computer's  BIOS is what boots the Windows CD go into BIOS and make sure that you are booting from DVDROM

---

### Post by jan quark on 2008-03-24
> Please, help me out of this linux hell!!

please do not hurt our feelings, if you want our help

---

### Post by kellemes on 2008-03-24
> **El French0 said:**
> I have had the worst time with ubuntu, there aren't any suitable drivers for my laptop's speakers, webcam, microphone, videocard, and mic/headphone jack.....  I have uninstalled ubuntu and am trying to reinstall windws but GRUB woln't let me boot any windows cds, even when holding r and everything, the only thing it will let me boot is fedora and ubuntu live cds.  There has to be a way to delete grub....

Please, help me out of this linux hell!!

If the Ubuntu livecd does boot and the Windows setup cd doesn't.. there is something wrong with the Windows setup cd. So you need to make sure you have a healthy disk.
A fine collection of info.. [http://www.users.bigpond.net.au/hermanzone/p18.htm]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by |2A|N on 2008-03-24
I had that problem one time and you need to delete your partition and reformat the drive then it will work.... and yes make sure to boot from cd afterwards~

---

### Post by El French0 on 2008-03-24
I didn't change the boot order in the bios.  ha ha ha....  My recovery CD boots now, and I am in the process of reinstalling windows..  

Linux isn't that bad, I used to use ubuntu 5 on my old laptop and it beat win XP, it messed up my new one though.  Thanks for your help

---

### Post by El French0 on 2008-03-24
now grub is preventing me from starting my computer, when it starts up and in the upper left corner there is the text "GRUB _"   AAAAAhhhhh will it end?

---

### Post by Oldsoldier2003 on 2008-03-24
> **El French0 said:**
> now grub is preventing me from starting my computer, when it starts up and in the upper left corner there is the text "GRUB _"   AAAAAhhhhh will it end?

boot from a windows cd and run the recovery console then fixmbr. or alternatively boot from cd or floppy and run fdisk /mbr

---

### Post by El French0 on 2008-03-24
I have the acer "enhanced" cds, they woln't let me do that..

---

### Post by waspbr on 2008-03-24
hey french dude, I know you have jumped ship on the whole ubuntu thing but I have done a small search on the forums and found this guide on the Acer Extensa 4620Z Laptop(I assume that is the computer you are talking about):


[http://ubuntuforums.org/showpost.php?p=4229258&postcount=17]("http://ubuntuforums.org/showpost.php?p=4229258&postcount=17")


if you ever decide to come back to ubuntu.

this is part of a larger thread on the Acer 4620z laptop:

[http://ubuntuforums.org/showthread.php?t=598626]("http://ubuntuforums.org/showthread.php?t=598626")

But in any case try running a live CD and using partition editor to delete the ubuntu partition and swap, this should take care of grub. Then use your recovery disks to reinstall windouze

---

### Post by xeth_delta on 2008-03-24
> **El French0 said:**
> I have had the worst time with ubuntu, there aren't any suitable drivers for my laptop's speakers, webcam, microphone, videocard, and mic/headphone jack.....  I have uninstalled ubuntu and am trying to reinstall windws but GRUB woln't let me boot any windows cds, even when holding r and everything, the only thing it will let me boot is fedora and ubuntu live cds.  There has to be a way to delete grub....

Please, help me out of this linux hell!!

I do believe you that you have had problems with Ubuntu on your machine, but I also believe that, had you asked for assistance on the issues you mentioned, here in the forum, people would have been keen on helping you out.

That being said, drivers/modules exist for almost all hardware found in current systems. May I ask what are your hardware specs, even if it is only for couriosity's sake? Speakers, hadphone/microphone jacks, microphones do not require separate drivers. What most likely you need is drivers for the sound card, and if that does not work out of the box (as it usually does) can be made to work in different ways, even recompiling alsa drivers.

Depending on your video card, you will have the option to use proprietary drivers (ATI/nVidia) or open source drivers, so I will have to slightly disagree. Taking into accout that your system is relatively new, I have to say that here are drivers for your graphics card. :)

As stated earlier, grub should not be able to prevent you from booting a CD. I recommend you to calm down and go to the BIOS and try to enable CD booting from there.

In any case, good luck!

---

### Post by El French0 on 2008-03-24
It keeps me from booting the windows, not cds, and I have completly reformated my hard drive, its still there

---

### Post by waspbr on 2008-03-24
Then it hasn' t really formated ur hardrive, something is still there, use the liveCD to check it out

---

### Post by xeth_delta on 2008-03-24
Haven't used any windows cd in a very long time, but as far as I remember, when you boot from it and it detects a windows installation, it will offer you a "repair" option by pressing R, once in the installer / blue screen. From there you should be presented with a command line.
If your CDs won't allow for this,that would be a matter of user restriction / locking, and one of the many many reasons I don't like or use that operating system. This is of course a matter of preference, so anyone is free to use the OS they prefer and feel more comfortable with.

---

### Post by xeth_delta on 2008-03-24
Forgot to mention one thing. Once in that command line, I mentioned in my previous post, follow the instructions from post #8. That should get it working.

Should you decide to try Ubuntu or another Linux distribution in the future, don't hesitate to ask for help, should you face problems with it :) I am sure the community will be glad to help.

Good luck, and let us know how it goes.

---

### Post by El French0 on 2008-03-24
When I typed "fdisk /mbr" it told me there was no such file or directory as mbr...

---

### Post by waspbr on 2008-03-24
The command is fixmbr, not fdisk/mbr.

---

### Post by forrestcupp on 2008-03-24
If fixmbr doesn't work for you, download the [Super Grub disk](http://supergrub.forjamari.linex.org/), burn the image to a cd, boot to it, and choose the option that allows you to fix the Windows boot loader.  That worked for me once.

---

### Post by Oldsoldier2003 on 2008-03-24
> **waspbr said:**
> The command is fixmbr, not fdisk/mbr.

actually both commands work. you just need to have  fdisk from a dos/windows 95/98 boot disk to do fdisk /mbr and actually of the two commands fdisk /mbr  is the faster easier method

---

### Post by El French0 on 2008-03-24
oh yeah, It works, I'll put a new partition on it for ubuntu soon, if I can get ubuntu to support everything it would be great, especially with that redmond theme.... sorry.

Thanks for all your help.

---

