---
title: "Switching Computers"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Billium on 2007-03-31
Having issues with my wife and "her" computer. To resolve , I am going to remove the HD on "her" computer that has Ubuntu on it, And put it into "my" computer.

Can I just take the HD out and put it into the other computer and have it give me the dual boot choice, or do I have to re-install from The CD?
I seem to remember with the original install that I had to make a choice to have that screen to come up.
There is nothing else on the HD.
Also after I remove the HD from "her" computer, will the dual boot screen still come up if XP is the only OS on that computer.
Another option would be to install Ubuntu on the same HD with XP on my computer, that's easy, but I would really like to get it off her computer altogether.

Hope that's enough info for someone to help me.  Thanks.

---

### Post by scxtt on 2007-03-31
if they have the exact same hardware - i suppose you could do that, but you'd have to edit /boot/grub/menu.lst to be able to boot XP ... it also depends on where you put the drive in relation to other drives in "your" computer and which drive is actually booted from (unless you want to edit your BIOS any time you want to boot off a different drive that has its own bootloader) ...

the opening line is funny - it almost reads like "[i'm] having issues with my wife . . . and "her" computer."

:p

---

### Post by laidback on 2007-03-31
I have moved Ubuntu ide hdd's from 1 pc to another with success, but I've not tried it with dual booting systems.  Since dual booting requires different info in grub/lillo I suspect that at the very least these will need adding/changing/altering to accommodate the new OS. That's beyond me I'm afraid, but no doubt some clever reader will know the answer.

Good luck

---

### Post by Billium on 2007-03-31
Issues are with my wife and me using her computer to learn Ubuntu.

HD on new computer is SATA 250GB. The drive with Ubuntu is IDE 40GB. Same as the one it's on now. I don't know how to edit anything yet but am trying to learn. Can you direct me to a site or give some info on how to do that?

I'm usually fine if I don't touch her computer.

---

### Post by scxtt on 2007-03-31
i think you'll save yourself some potential headache if you just remove the drive, put it in its new home, then install ubuntu again ... once you do that, it'll pick up on your already installed XP and allow you to boot either one when it installs grub ...

---

### Post by jvc26 on 2007-03-31
If Ubuntu is all there is on that drive it would save you a lot of effort, and probable issues, to take the drive to your computer and reinstall Ubuntu on it and set it up freshly. Mainly because the likelihood of having the same hardware setup is unlikely, and certainly it will have different UUIDs for the drives (applicable from edgy ->) which may well cause you issues with booting and with fstab. Setting up ubuntu shouldnt take that long and it will save you a potential headache.
Il

---

### Post by SentientFluid on 2007-03-31
> **Billium said:**
> Having issues with my wife and "her" computer. To resolve , I am going to remove the HD on "her" computer that has Ubuntu on it, And put it into "my" computer.

Can I just take the HD out and put it into the other computer and have it give me the dual boot choice, or do I have to re-install from The CD?
I seem to remember with the original install that I had to make a choice to have that screen to come up.
There is nothing else on the HD.
Also after I remove the HD from "her" computer, will the dual boot screen still come up if XP is the only OS on that computer.
Another option would be to install Ubuntu on the same HD with XP on my computer, that's easy, but I would really like to get it off her computer altogether.

Hope that's enough info for someone to help me.  Thanks.

First step is to back up everything that you don't want to risk losing.  Do this for the Windows drive as well as the Ubuntu drive.

Next you want to find out if your Ubuntu drive will work on the new computer without any changes to the software.  Remove your Windows hard drive and connect the Ubuntu drive.  Make sure all the cables are seated correctly and then start up the computer.

Possibility #1:  If your computer and your wife's computer have different hardware (especially if it's the logicboard, video card, or processor), then this will most likely give you errors before you even get into Ubuntu.  The only way I know to bypass this is to reinstall Ubuntu, though someone else may know of a way past it.  If you have to reinstall Ubuntu, then make sure both hard drives are installed and recognized by your computer and when you go through the install process Ubuntu (it's worked for me with Hoary or better) will automagically find and add your Windows partition to the boot loader.

Possibility #2: If you and your wife's hardware is the same, or uses the same drivers, then Ubuntu should run fine.  If this is the case, then all you really need to do is set Grub as the boot loader and get it to recognize the two OSes.  [This post]("http://www.ubuntuforums.org/archive/index.php/t-24113.html") may help out.

---

### Post by Billium on 2007-03-31
I'm going to remove the Hd from the other computer, add it to my computer and then re-install Ubuntu. When I do this I think it will allow me to upgrade to EDGY, which is probavly a good thing.

Thanks for the help, I'll come back tomorrow and let you know how it went.

---

### Post by Billium on 2007-04-01
I think I really messed up.
Put HD in other computer. Made sure BIOS was set to boot from CDROM. Got the correct first screen then the s... hit the fan.Got an entire page of text. Everything says OK until I get to

[4294669.386000] checking if image is initramfs...it isn't (no cpio magic); looks like an initrd

Looks good for few lines then:

ACPI: Looking for DSDT in initrd... not found!
[4294669.591000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
                           ...trying to set up timer (IRQ0) through the 8259A ... failed
                           ...trying to set up timer as Virtual Wire IRQ... failed
                           ...trying to set up timer as ExtINT IRQ .... failed
[4294669.610000] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the  'noapic' option [4294669.610000]

Now I am in panic. I think my kernel just popped. All this so my wife wife can have her windows back. Sheessh.

Help me please. Panic mode. I'm heading to the Gin.

---

### Post by h0ax on 2007-04-01
No worries, you're merely booting into the OS.
When you boot from CD and haven't done anything, Ubuntu is just loading from the CD, it hasn't changed anything with your hardware.

It looks like there's something wrong - and it wants you to declare noapic before you boot.

Boot from the cd - then type "noapic" without quotes at the prompt that comes up, then hit enter and let it go - see if that works.

Hope that helps

---

### Post by Billium on 2007-04-01
Everything appears to be frozen. I can't type or turn the computer off, or reboot or anything. What if I unplug the computer, would that start things over again?

---

### Post by SentientFluid on 2007-04-01
> **Billium said:**
> I think I really messed up.
Put HD in other computer. Made sure BIOS was set to boot from CDROM. Got the correct first screen then the s... hit the fan.Got an entire page of text. Everything says OK until I get to

[4294669.386000] checking if image is initramfs...it isn't (no cpio magic); looks like an initrd

Looks good for few lines then:

ACPI: Looking for DSDT in initrd... not found!
[4294669.591000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
                           ...trying to set up timer (IRQ0) through the 8259A ... failed
                           ...trying to set up timer as Virtual Wire IRQ... failed
                           ...trying to set up timer as ExtINT IRQ .... failed
[4294669.610000] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic=debug and send a report. Then try booting with the  'noapic' option [4294669.610000]

Now I am in panic. I think my kernel just popped. All this so my wife wife can have her windows back. Sheessh.

Help me please. Panic mode. I'm heading to the Gin.


Are you booting to a LiveCD?  6.06? 6.10?  I don't think any of those errors have anything to do with your hard drive(s) (though I could be wrong).  Did you try booting using the "noapic" option like it said?  Press F1 at the LiveCD boot menu and try using the noapic option.  If that doesn't work, try some of the other options: nolapic, noacpi, etc.

Otherwise, check out [this article]("http://ubuntuforums.org/archive/index.php/t-77021.html").  It seems you're not the only one who has gotten the "MP-BIOS bug: 8254 timer not connected to IO-APIC" message while booting, and it may be related to a mismatched kernel/processor, to a bug, or to both.

> **Billium said:**
> Everything appears to be frozen. I can't type or turn the computer off, or reboot or anything. What if I unplug the computer, would that start things over again?

It doesn't sound like you've started any install yet so pulling the power shouldn't affect anything.

---

### Post by Billium on 2007-04-01
it's version 5.10. i entered noapic, nolapic and nocpi. All come back Could not find kernel image.
It gives me several options for boot (F3 thru F7) 
Boot methods for special ways of using this cdrom
Special boot parameters, overview
.................................. for special machines
.................................. for selected disk controllers
.................................. for the install system
 I'm a real nubie and don't know anything.
Thanks, i'll put the gin away.

---

### Post by Billium on 2007-04-01
i entered linux vga=771 noapic nolapic. and got to the next page that asks for language.
I think I'm making progress.

---

### Post by SentientFluid on 2007-04-01
Did you read through the link I provided?  Did you try running with all the above options () at the same time?  Did you try booting with the **notsc** option?

What hardware is your computer running? Specifically the processor and motherboard...

Do you have a 64-bit processor?  Are you using a 32-bit version of Hoary (5.10)?  If yes to both, can you download and try a 64-bit version?

Can you try using Dapper (6.06 LTS)?  Newer versions will often have most of the older bugs worked out.

---

### Post by Billium on 2007-04-01
Everything seems to be installing fine now.
 I have an AMD FX64 4000 cpu. 1.0 gb ram
At this time it is installing packages. i feel good now. the grub boot loader recognized all my other OS, Windows media center and Nt.  I hope it gives me the option to download a newer version of Ubuntu. EDGY or something. I get the feeling that 5.10 is old now.
You have really been a calming force and helped me a lot.
Thanks.

Please check back to see if everything goes well, I hope this post will help other nubies to try Ubuntu.

---

### Post by Billium on 2007-04-01
I'm at a screen"breezy badger' bill tty1
expressing no warranty on the install
Asking bill@bill:~$

What do I put in?

---

### Post by Billium on 2007-04-01
Here is where I am now.

I got a little sleep and started reading some more. I think the installation problems come from the version that I tried to use. (5.10) It installed really well on my older AMD Semoron 2800 cpu. This computer is a AMD Athlon 64 4000. I find that it makes a difference between 32bit and 64bit. Told you I was new at this.

I have gone to Ubuntulinux.org and am downloading 6.06 for desktop AMD 64 cpu. About 7 hours at current speed. Hawaii is actually a third world country when it comes to technology.

I need to learn how to use the information on this site, searching threads and such.

I will be back when I get finished with the install and give a report. If you can think of anything I need to do before installing, please let me know. Everything is already backed up.

Thanks. The Ultimate Nubie.

---

### Post by h0ax on 2007-04-01
Once you get to the command prompt "bill@bill:~$
Try to load the X environment with the command: startx

Def good decision to DL the newer version -- Definitely search threads here when you need help.
So many good pockets of information.

---

### Post by Billium on 2007-04-01
Downloaded:
 Ubuntu 6.06.i desktop AMD64 iso

Burned as a bootable disk.
Made sure to set boot loader to CD
rebooted computer and Get the following text:

1. FD 1.44MB System Type-(00)
Starting Caldera DR-DOS
EMM386 3.27 Copyright (c) 1992, 1998 Caldera, Inc All rights reserved

I don't even have a floppy disk. I checked in BIOS and there is not one recognized.
I can't do anything with the screen at all, except Ctri+Alt, Delete then the process starts all over again. 

Wrong Disk, did I burn it wrong, what did I do. 
Searched the forums under boot, ubuntu, disk, CD. All the problems mentioned there have to do with at least the boot process starting. Mine won't start.

Beginning to feel that this was not ment to be. I know there is a learning curve, but can I just get to the place where I can start learning.

Frustrated Nubie. (actually, I know that I am already learning, but you know what I mean)

---

### Post by confused57 on 2007-04-01
Here's how to burn an iso:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

You have to burn an iso as an "image", not as a bootable disk, burn it on a low speed(I use 8x & haven't had any problems).

---

### Post by Billium on 2007-04-01
Can you hear the scream of Joy in North Carolina?

it is installing as we speak.

Hopefully things will go well from here on out'

Thanks again for all the help. Maybe this thread can be of help to other green nubies like myself.:) :) :) :)

---

### Post by confused57 on 2007-04-02
I thought I heard something, but the wife was yelling at me, so I couldn't discern very clearly what it was.  Sorry you have to live in such a technology-challenged place such as Hawaii.  Do you need someone to mow your grass, wash your vehicles, be a chaffeur?  I could work for room & board, you could even claim me as a dependent on your Federal taxes.

Hope your install goes well...good luck.

---

### Post by antoz on 2007-04-02
[COLOR="Red"][B]Confused57
[/B][/COLOR]You make so many people happy all around the world, keep up the good work.
Have a great day,A[COLOR="DarkOrchid"][COLOR="DarkOrchid"][COLOR="Blue"][/COLOR][/COLOR][/COLOR]

---

