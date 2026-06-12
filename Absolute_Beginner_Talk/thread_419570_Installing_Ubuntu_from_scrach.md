---
title: "Installing Ubuntu from scrach"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Big_Kiwi on 2007-04-23
I am totally new to this, and may need a bit of help even with the basics, so feel free to give me pleanty of advice.

I have for some time been looking at coming over to a Linux system but never made the jump untill now, I have downloaded Ubuntu 7.04 for AMD processeor.

Ihave a 100gig HDDx2x50 patitions + 10gig currently running win XP, with 512 meg ram.

to install windows on a HDD one would have to format the disc, Is this still true for Ubuntu? I would like to keep the 10gig drive on windows and put the 100gig drive on to Ubuntu is this possible and how do I start installing Ubuntu?

And can I set some thing up so when I boot my PC it will ask me which drive I want to boot to?

Thanks for your help
Big_Kiwi

---

### Post by nsleiman on 2007-04-23
Just boot up your system with the Feisty CD (the live CD will run first) after that you will find a Shortcut on the desktop called Install or something. the rest will be done automatically :)

About the dual booting, you will have the option to install GRUB so you can choose between Windows or Ubuntu.

---

### Post by BaffledMollusc on 2007-04-23
> **Big_Kiwi said:**
> I am totally new to this, and may need a bit of help even with the basics, so feel free to give me pleanty of advice.

Welcome to the club!
> 
I have for some time been looking at coming over to a Linux system but never made the jump untill now, I have downloaded Ubuntu 7.04 for AMD processeor.

Just so you're aware, the AMD64 version of Ubuntu is the 64-bit version of the operating system - it doesn't mean it's the Athlon 64 version. It will also work with 64-bit capable Intel CPUs.

The 64-bit version doesn't have as many drivers as the 32-bit version, and it's a bit flakier. If there's no specific reason you want a 64-bit OS, you might be better off with the i386 version. Just a thought.

> 
Ihave a 100gig HDDx2x50 patitions + 10gig currently running win XP, with 512 meg ram.

to install windows on a HDD one would have to format the disc, Is this still true for Ubuntu? I would like to keep the 10gig drive on windows and put the 100gig drive on to Ubuntu is this possible and how do I start installing Ubuntu?

And can I set some thing up so when I boot my PC it will ask me which drive I want to boot to?

In theory all you have to do is put the CD in the drive and boot, then choose the live CD option. You'll end up on the Ubuntu desktop so you can try things out. If you want to install permanently to the hard drive, click on the install icon and follow the prompts. You don't have to do any formatting in advance; this will be handled during the installation process.

---

### Post by petersjm on 2007-04-23
You just have to remember to pick the correct HDD when you install, but that shouldn't be hard if one disc is 10Gb and the other is 100Gb (the installer tells you their sizes, so you can pick the right one).

---

### Post by tact on 2007-04-23
> **Big_Kiwi said:**
> 
to install windows on a HDD one would have to format the disc, Is this still true for Ubuntu? I would like to keep the 10gig drive on windows and put the 100gig drive on to Ubuntu is this possible and how do I start installing Ubuntu?

And can I set some thing up so when I boot my PC it will ask me which drive I want to boot to?

Thanks for your help
Big_Kiwi

Hey there Big_Kiwi.  You r in Brisbane? I was born there but living overseas now for 8 or more years.

As others have said, give the intel x86 live CD a try.  Once you downbload the ISO file and burn it to a CD you will have a bootable CD in yout hands.   Slip it into the CD drive and press any hot key needed to boot the CD.

Once its booted (yes it will be slow cos CD drives are not as fast as HDD's) you should have a fully working ubuntu running on your machine.  And it didnt change ANY part of your existing HDD...  its all running off the CD and in RAM only.    You can now try out all the sample music, video, documents, etc in the samples folder to see your video, sound, keyboard etc all work great.   You can also surf the net if you have a network connection to see all your network stuff functions as it should.   All this with NO RISK at all to your existing system, your HDD's not even touched!

If everything is to your satisfaction then you can consider double clicking the "install to HDD" icon.   Selecting appropriate options will see ubuntu installing itself on some freespace on whatever drive you tell it to use.  It will also only use the amount of HDD drive space that you tell it that it can use.   In doing the installation if it detected you have Windows installed - it will automatically install a boot manager for you.  When its all done and you reboot the first thing you see after the BIOS screen is a menu - choose to boot Ubuntu or Windows.

lovely.  ;)

---

### Post by Neil Purling on 2007-04-23
If you want to try the Ubuntu Live CD you will have to go into the BIOS and change the 1st boot device from Floppy to CD-ROM.
That done it will boot up, although don't expect serious speed.
The issues I had when starting were Internet access and printing to start with and then access to the Windows partition/windows HDD when in Ubuntu. 
Whatever hitch you have it will probably have been asked by someone else.
I am running 6.06 Dapper Drake and use a ADSL router for internet access.

---

### Post by Big_Kiwi on 2007-04-24
[FONT="Arial Black"]**\\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ \\:D/ :KS **[/FONT]

[FONT="Arial Black"][COLOR="RoyalBlue"]Here goes nothing[/COLOR][/FONT]

---

### Post by Big_Kiwi on 2007-04-24
Hi all I am back

need more help please

trired all your surgestions but still can not boot in to Ubuntu i386 cd, changed boot drive in bios, tried f8 key on boot up but mt silly system keeps booting in to win XP, WHY?

---

### Post by vanadium on 2007-04-24
It is really a matter of telling your system to boot from CD in the bios. It sounds like you have been into your bios, but perhaps, you did not manage to properly apply or save the change you made to the boot sequence.

Try it again, and look carefully at the hints given how to proceed. Once finished, you must choose an "Exit and save" option to exit Bios, else, your changes will not be saved. The details depend on the bios you have. On my system, I need to press F2 during startup to enter bios. I need to press F10 and reply yes to a prompt to exit and save settings.

---

### Post by Big_Kiwi on 2007-04-26
Finaly got Ubuntu booting a big Thanks to all that helped me out

---

