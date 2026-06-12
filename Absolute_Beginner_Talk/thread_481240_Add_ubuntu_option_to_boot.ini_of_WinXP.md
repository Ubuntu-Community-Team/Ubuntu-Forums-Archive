---
title: "Add ubuntu option to boot.ini of WinXP?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by Daevius on 2007-06-22
Hi,

I have installed Windows XP and Ubuntu 7.04
I can only boot Windows XP, so I wondered how I can modify boot.ini to let me choose to boot ubuntu or windows.

Is this possible or only possible with GRUB?

This is the line for my windows in boot.ini, what should it be for Ubuntu? I should set rdisk to 1, but what should \WINDOWS be?

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

Thanks in advance!

Daevius

---

### Post by Happy_Man on 2007-06-22
Please don't try. You may end up not being able to boot ANYTHING. Just stick with GRUB. It's safe, tested and secure.

---

### Post by phr0ze on 2007-06-22
I've done this and it works fine. unfortunately it was a while ago with a different flavor, but it should still work. I did a quick google search and came up with the following page: [http://highlandsun.com/hyc/linuxboot.html](http://highlandsun.com/hyc/linuxboot.html)

I have not tried this exact proceedure but it seems similar.

---

### Post by Daevius on 2007-06-22
Thank you for the article :), but the problem is that I cant boot in Ubuntu anymore or can even access it! Perhaps with a tool to view ext3...

Daevius

---

### Post by 5-HT on 2007-06-22
> **Daevius said:**
> ...the problem is that I cant boot in Ubuntu anymore or can even access it! Perhaps with a tool to view ext3...

Daevius
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
Or just boot up a liveCD, mount your partitions, and make the required changes.
cheers,

---

### Post by LaRoza on 2007-06-22
With the Ubuntu boot disk you would be able to install Grub and view all the partitions.

I do not suggest using the boot.ini, use Grub.

---

### Post by LaRoza on 2007-06-22
If you have boot problems, you might want to have the Super Grub Disk on hand, it works for many operating systems, including XP and Vista.

---

### Post by phr0ze on 2007-06-22
Here, this article talks about a windows utility to grab the linux boot. It's also more up-to-date.

[http://www.linux.com/articles/113945](http://www.linux.com/articles/113945)

using boot.ini method is less risk for your windows config and more risk for ubuntu. But there is really not a lot of risk either way since there are tools to recover. Using some of this method you can set up a floppy to boot your linux partition. Almost like a key. Floppy in the drive you get linux. No floppy you only get windows.

---

### Post by michaelzap on 2007-06-22
When I had trouble getting grub to run on a partitioned XP/Ubuntu disk, I used wingrub (which adds an option to the Windows boot.ini that searches for grub installs) with no problems at all, so you might also try that.

---

### Post by ckempo on 2007-06-22
Hi all.

There is a thread here that I have contributed to that outlines how to use a utility called bootpart to setup the boot.ini file for Linux. 

It's not difficult, and I am planning on writing it up properly for the wiki - but you may want to refer to this thread in the meantime: [http://ubuntuforums.org/showthread.php?t=476855]("http://ubuntuforums.org/showthread.php?t=476855")

---

### Post by Daevius on 2007-06-22
Ah thanks for all the replies :D

I used phr0ze's link...but its not yet finished lol. I downloaded bootpart, saved the bootsect.lnx to my windows main folder and added the correct line to boot.ini.

Now when I select linux from the boot loader of XP, it gives me a beep and restarts the machine. What could this possibly be? That ubuntu hasnt got any boot loader installed (grub)?

Thanks in advance :D

Daevius

---

### Post by oilchangeguy on 2007-06-22
> **Daevius said:**
> Hi,

I have installed Windows XP and Ubuntu 7.04
I can only boot Windows XP, so I wondered how I can modify boot.ini to let me choose to boot ubuntu or windows.

Is this possible or only possible with GRUB?

This is the line for my windows in boot.ini, what should it be for Ubuntu? I should set rdisk to 1, but what should \WINDOWS be?

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

Thanks in advance!

Daevius


you're making something that's really easy. needlessly hard. if you're trying to setup a dual boot system, install windows first, then ubuntu. i'd suggest starting over, and do this correctly.

---

### Post by logos34 on 2007-06-22
No need to reinstall the whole thing...All you need to do is reinstall grub to the mbr.  You installed windows second, so the windows bootloader overwrote grub.  Now just overwrite it with grub.

See '**Using the Desktop/LiveCD and Overwriting the Windows bootloader**' section in this [link]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub"):

---

### Post by Daevius on 2007-06-22
I wish I could, but installing windows takes so long, when I have to set up my complete workspace and everything. I installed windows first, but thats on the second drive, the slave one. I wish I could just choose something in the ubuntu installation according to this problem...well, this way I will learn a little more about it ;)

However, it doesnt starts up ubuntu anyway, when I change the jumper on the drive, ubuntu should start but it gives me that it has a disk failure or no boot thingy found. And when I have the jumper as I have now, windows will start, but when I choose ubuntu from the bootloader, it doesnt start up. Really, its getting a bit confusing :P. I think its something simple...as usual.

Or should I reinstall ubuntu? That should be no problem, but perhaps it will overwrite the MBR AGAIN??? :(

Thanks anyways...

Daevius

---

### Post by Daevius on 2007-06-22
Okay thank you logos34, I will try it right now :D!

Daev

---

### Post by logos34 on 2007-06-22
> I installed windows first, but thats on the second drive, the slave one...
...when I change the jumper on the drive, ubuntu should start but it gives me that it has a disk failure or no boot thingy found. And when I have the jumper as I have now, windows will start, but when I choose ubuntu from the bootloader, it doesnt start up. *Really, its getting a bit confusing :P. I think its something simple...as usual.*

yeah, I'll say. Umm, this is the first mention you've made of second drives, changing jumpers, etc.  Need to try to post all of this up front the first time instead of popping this on us at the end.

---

