---
title: "Need help on installation..please"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by darkcyber on 2007-01-09
Need additional help here please!

I've run another installation of ubuntu 6.10 64 bit and finished installing it and i'm back to the black screen where it shows ubuntu and says to remove the cd and press enter to continue. I've done this and nothing happens.

This is the same thing that happened to me yesterday and it never rebooted...so I had to press the reset button and then when it rebooted I got the "missing operating system".

Does anyone have a clue why it will not reboot from this screen?

---

### Post by kidders on 2007-01-09
Hi there,

I seem to remember that happening with my Mac (the failing to reboot part), but the "Missing operating system" message probably comes from your BIOS. Are you sure your primary boot device corresponds to the location Ubuntu put your bootloader?

---

### Post by darkcyber on 2007-01-09
I got the same results after pressing the reset button and rebooting my pc.  It comes up and says "missing operating system".  So, I used the Super Grub bootable cd.  I selected Windows XP and it did start booting XP up and then ran chkdsk on the hd.  It finally did boot all the way into XP.  I rebooted again and was looking for anything to dual boot my pc between ubuntu, which I just installed, and Windows XP and there is nothing.  My pc boots straight up into XP.

So, what makes for the dual boot or what makes the pc come up with the option for dual boot?  I'm lost here. ](*,)

---

### Post by darkcyber on 2007-01-09
> **kidders said:**
> Hi there,

I seem to remember that happening with my Mac (the failing to reboot part), but the "Missing operating system" message probably comes from your BIOS. Are you sure your primary boot device corresponds to the location Ubuntu put your bootloader?


Well, I have a 34 gig WD serial Raptor hd, which I have my Windows XP installation on as well.  It is set in my bios as my primary boot drive.  It works fine booting up XP, I just start having these problems after I install ubuntu.

---

### Post by kidders on 2007-01-09
To run more than one OS, you should install a bootloader. Ubuntu does this by default, since Linux likes bootloaders ... even when it's on a PC by itself. Ordinarily, it resides in the MBR of one of your hard disks. That disk should be your primary boot device.

**Edit:**

> Well, I have a 34 gig WD serial Raptor hd, which I have my Windows XP installation on as well. It is set in my bios as my primary boot drive. It works fine booting up XP, I just start having these problems after I install ubuntu.Is that where your bootloader is?

---

### Post by darkcyber on 2007-01-09
> **kidders said:**
> To run more than one OS, you should install a bootloader. Ubuntu does this by default, since Linux likes bootloaders ... even when it's on a PC by itself. Ordinarily, it resides in the MBR of one of your hard disks. That disk should be your primary boot device.

**Edit:**

Is that where your bootloader is?

Well, I hate to sound completely stupid here...but where (was) is the option to place the bootloader on a certain hd?  When I went through the installation...I selected C: drive, which is my 34 gig raptor drive.  That's where I installed ubuntu to.  So, I assume everything should have installed there.  But I'm not getting anything that gives me an option to boot Linux or Windows.  After running Super Grub, it just boots right into Windows.  Is there a way to fix or put the bootloader on there now to make it dual boot?

---

### Post by kidders on 2007-01-09
Maybe you deleted your bootloader. :confused:

In any case, it doesn't matter, because you can easily put one back on. :-) Pick one (grub & lilo are the usuals) and either grab yourself a Windows-based installer for it, or boot into Ubuntu with a boot CD and do it there.

If it were me, I'd install grub from Ubuntu (to keep it happy, and make life easy). Thankfully, there are plenty of step-by-steps on here for how to do it, in case you run into trouble. Remeber to note which disk you're putting it on, so you can make sure your BIOS is correctly configured, when you reboot. Using Ubuntu's bootloader makes things like system updates more straightforward in the long term.

**Edit:** Sorry... I forgot to answer one of your questions: > Where (was) is the option to place the bootloader on a certain hd?Rather stupidly, that option wasn't available in the standard installer, last time I checked! Checking which disk it's on only requires 20 or 30 seconds of trial and error, but imo it's still irritating.

---

### Post by darkcyber on 2007-01-09
Would you mind directing me to where I can install the bootloader from in ubuntu?

Do you mean use the bootable cd and boot all the way into the desktop (i.e. using the live cd)?  Or is what you're talking about listed in the menu options when the cd first boots to that first menu?

Again...total noobie here and just learning where everything is at.

Thank again!

---

### Post by kidders on 2007-01-09
Hey again,

You can install grub from any Linux environment ... it doesn't even need to be Ubuntu. The only wrinkle that I've seen happen occurs where you have both IDE and SATA hard disks plugged in together, where device numbering can get a little screwy on occasion. Let me know if that applies to you, and I'll go into more detail.

There are probably plenty of convenient little tools around for installing grub, but I always use the underlying console utility directly.

[LIST=1]
[*]Take a look at **/boot/grub/menu.lst** to make sure it seems sensible. In particular, lines that start with the keyword "root" need to have the right disk/partition numbers in them. Also, in in lines that start with the "kernel" keyword, make sure you're happy with the bits that come after the kernel's name.
[*]Then, open the "grub" tool (by typing "grub"), and enter something like this:
[/LIST]```
root (hdx,y)
setup (hdx)
quit
```

Once you're done, just reboot. The worst thing that might happen is that it won't work the way you expected (ie it's quite hard to cause any actual damage), in which case, you can start again, correcting your mistake.

Since you're not all that familiar with grub, I suggest you read a little about it before reinstalling it. Making sense of things like the contents of menu.lst is easy, but you'll need to read how, because small mistakes make a big difference!

**Edit:** I forgot to mention that the point in doing all this is to install a small bootstrap into the master boot record of one of your hard disks, allowing you to select the OS you want to use at boot time, based on the contents of the "menu.lst" file.

---

### Post by darkcyber on 2007-01-09
Well, I guess that applies to me :) 

I have the 34 gig serial raptor for my C: OS drive and then I have an ide 200 gig and 300 gig hard drives for storage.  So, I do have a mixed bag.


Also, will that Super Grub do what you're talking about?

---

### Post by kidders on 2007-01-10
Oh. :-|  Well in that case, you *might* find that the way your disks are ordered after boot doesn't tally properly with the way they're numbered beforehand. I'm not sure whether it's down to faulty SATA controller implementations (of which there are a great many) or something else, but the upshot of it is that grub will screw up on you. The solitary advantage lilo has over grub is that it doesn't use any silly, made-up numbering schemes for identifying disk partitions.

Anyhow, it's entirely possible this was the reason your bootloader installation didn't go to plan to begin with.

> Also, will that Super Grub do what you're talking about?I have no idea, I'm afraid. I don't know anything about Super Grub. Even if it can however, I'd still be much more inclined to configure & install grub myself. Installing a bootloader is a convenient thing to know how to do (especially if you're a windoze user, because microsoft products *love* to sabotage other operating systems!) ... and after all, it's not terribly hard. If you have trouble with automated bootloader installers, manual installation is way simpler imo.

---

### Post by darkcyber on 2007-01-10
kidders,

Well, I finally just got tired of messing with it...tried alot of things and still didn't get the dual boot up.  I did get my XP boot back up, but no way to boot Linux.

So, if I'm crazy enough to try this again ](*,)  and it does the same thing...again.  Then you're saying that I still could get it to work by manually fixing the bootloader?

By fixing it, would that be doing it the way you were talking about earlier in your post?  Using grub?

---

### Post by kidders on 2007-01-10
Yeah, maybe. Windows tends to screw up bootloaders from time to time anyway, so you'd probably have to do it every time you perform a major update or make organisational changes to either OS. It shouldn't be a major hassle though ... once you're booted up, installing a bootloader manually normally takes less than 30 seconds. :-)

> Tried a lot of things and still didn't get the dual boot up.What have you tried? What's going wrong for you?

If you really don't like bootloaders, there are other ways of running multiple OSs, but they're a bit hacky, and not really to be recommended.

---

### Post by darkcyber on 2007-01-10
Well, I've installed ubuntu twice and get the same results...pc says missing operating system after installation.  I've used Super Grub and was able to boot into XP after the second installation.  I also used Super Grub to try and fix the bootloader.  After that, I did get the boot menu, but once I selected the linux kernel I got error 22:  something about no partition or something like that.

So, I've gotten it installed, but just can't boot into ubuntu...able to get into XP after using Super Grub, but not ubuntu.  

Is there any other way I can do this?  if I get ubuntu installed again...what steps do you recommend to fix the bootloader?  I think it's the issue with me having 1 SATA hd and 2 ide hd's.

---

### Post by kidders on 2007-01-10
I'm afraid it's hard to be any more specific than my previous posts ... there is no way for me to guess your disk/partition configuration, or what Ubuntu's installer might be doing wrong. A little trial and error will solve everything for you though. Don't forget that grub provides a nice console for use at boot time, so finding the right partition numbers is quite fast.

> if I get ubuntu installed again...what steps do you recommend to fix the bootloader?There's no need to re-install Ubuntu though ... once is almost always enough.

---

### Post by darkcyber on 2007-01-10
Got another question for you.

Why is it when I install ubuntu and select the partition to install it to that ubuntu uses every last ounce of free hd space? Like on my C: drive I had like 220 mb's left once I installed ubuntu. When it came up in the installation about the partition size I slid the little slider back all the way to the left, but it still used all my free space. Can't have that. Is there a way to set an exact size you want it to us?

I do not want it using ALL of my free space on my C: partition.

---

### Post by Sef on 2007-01-11
Select manual partition and you can set the size of the partition.

---

### Post by darkcyber on 2007-01-11
1.  Can I resize a partition once it's done?  i.e. take away some from the Linux partition and add it back to the NTFS? I did select the manual partition, couldn't figure out how to set it.

2.  Here's another question.  I just installed ubuntu on another pc (without a SATA) and went through the install and I'm exited from the desktop and it's back at the black screen that shows ubuntu with a logo beside it and the progress bar below it.  It says 'Please remove the disc, close tray (if any) and press ENTER to continue'.  I did this here and pressed enter numerous times.  I even left it like that over night to see if it would ever go past that screen never does.  Still stuck there this morning. This is the same thing it did on my SATA system.  I had to press the reset button to get it to reboot.  Don't know if that's what screwed up the bootloader on the SATA or not. How do you get it to get off that screen other than pressing reset?


UPDATE:  I finally got it to install on a second pc that is running XP.  This system has only ide hd's in it. Progress...finally :)

I was able to boot into ubuntu, but now when I select Win XP from the boot menu I get this error:  Windows could not start because the following file is missing or corrupt:  <Windows root>\system32\hal.dll.  Any suggestions here?

---

### Post by darkcyber on 2007-01-11
Bump...no one has a suggestion on this dual boot problem I mentioned above?  Here it is again:

I finally got it to install on a second pc that is running XP. This system has only ide hd's in it. Progress...finally

I was able to boot into ubuntu, but now when I select Win XP from the boot menu I get this error: Windows could not start because the following file is missing or corrupt: <Windows root>\system32\hal.dll. Any suggestions here?

---

### Post by darkcyber on 2007-01-12
> **Sef said:**
> Select manual partition and you can set the size of the partition.


How do you do this?  I've selected manual partition and then I select the hd and then click on resize, but the button at the bottom right is grayed out and is non-clickable.  So, can someone explain exactly how to do manual partition of your hd? Because every time I use automatic and no matter where I slide that slider bar to, it always using ever bit of free hd space and that leaves my Windows partition with like 200 mb's of space.

Thanks!

---

### Post by darkcyber on 2007-01-12
Finally got it fixed.

Here's what I did I disconnected my 2 ide hd's and only had my SATA hd connected. I then installed the 32 bit version of ubuntu. This time when I installed it the little ubuntu splash screen was in color. When I used the 64 bit version it was always black and white. Also, when I finished the installation and it exited off the desktop it went back to that splash screen which was in color again and it opened the cd tray and said to remove the cd and press enter. This time when I pressed enter the computer did reboot.

So, I don't know if it was the 64 bit version or the ide hd's. I did try the 32 bit version with the 2 ide hd's connected and it didn't work. So, could have been a combination.

All my network stuff was detected and all I did was click on FireFox and it accessed the net right off...very sweet.

---

