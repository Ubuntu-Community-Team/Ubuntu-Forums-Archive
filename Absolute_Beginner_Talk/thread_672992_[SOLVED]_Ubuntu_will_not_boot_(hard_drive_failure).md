---
title: "[SOLVED] Ubuntu will not boot (hard drive failure?)"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by apunc1 on 2008-01-20
I have Feisty on my desktop pc and it is the only operating system on the hard drive. 
there are three partitions: /, /home and swap

things have been going fine until this morning. i leave my computer on all the time. so i woke the monitor up, and opened firefox. it opened fine. i clicked the gmail link and things froze. not only did they freeze, but my screen started to fuzz and things get all blurry. attempts to ctrl+alt+backspace were unsuccessful. so i switched off the computer manually with the power button. waited. turned computer back on. grub loads to stage five but then just goes to black screen. sometimes the splash screen with load and then freeze, but mostly just black screen.

i have tried the fesity and pclinuxos live cds. both have given the same result. they boot up to the "welcome screen" and when i choose to install to get to the live environment, kernel seems to load but then black screen and nothing more.

no new hardware has been added to this computer. the only software added was the recent xorg update. i had the same problem with it everyone else had, but i waited a day, updated again, and the xorg update was able to update. 

is it hard drive failure? as I can't even load a live cd it seems it could be hard drive but i'm not sure. is there anything else it could be or more things i should try?

thanks

---

### Post by Trebaruna on 2008-01-20
The graphical artifacts you mention do -to me, a mere layman- suggest a hardware failure, especially if now nothing seems to work.
However, I'd be more inclined to look at other parts of the PC for the culprit: the memory, processor or the videocard. For a start, perhaps you could try to run [Memtest]("http://www.memtest.org/") for a while, see how that does. If that fails you're sure to have a hardware problem.

Note: this is by no means an expert opinion, but just where I'd look.

---

### Post by torgrot on 2008-01-20
I don't think it is a drive problem they usually show up before grub loads.  Check this page for some troubleshooting tips regarding grub.[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Have you tried to run efsk or whatever its called on the drive?

torgrot

---

### Post by apunc1 on 2008-01-20
> **Trebaruna said:**
> The graphical artifacts you mention do -to me, a mere layman- suggest a hardware failure, especially if now nothing seems to work.
However, I'd be more inclined to look at other parts of the PC for the culprit: the memory, processor or the videocard. For a start, perhaps you could try to run [Memtest]("http://www.memtest.org/") for a while, see how that does. If that fails you're sure to have a hardware problem.

Note: this is by no means an expert opinion, but just where I'd look.

that is a good idea. i will try to run memtest if i can get the live cd to load to that point again.
thanks

---

### Post by apunc1 on 2008-01-20
> **torgrot said:**
> I don't think it is a drive problem they usually show up before grub loads.  Check this page for some troubleshooting tips regarding grub.[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Have you tried to run efsk or whatever its called on the drive?

torgrot

fdisk? i can't get to a command line. i may be able to with the live cd. i'll try again.

---

### Post by jnorthr on 2008-01-20
are you a mac user ? have you considered that perhaps a heat load buildup may have blitzed something. Try to power down your machine for 10 - 15 minutes to let it cool off. This may be heat related.

why do you use the install choice from your live cd ? i'm wondering too if your install has been blitzed that is why it does not boot past that point.

---

### Post by apunc1 on 2008-01-20
> **jnorthr said:**
> are you a mac user ? have you considered that perhaps a heat load buildup may have blitzed something. Try to power down your machine for 10 - 15 minutes to let it cool off. This may be heat related.

why do you use the install choice from your live cd ? i'm wondering too if your install has been blitzed that is why it does not boot past that point.

yes my other computer is a mac. 

i chose the install option because that would take me to a live environment on the live cd. i was not trying to install ubuntu again. i was just trying to get to a place where i could see my hard drives and data.

this machine has never had heat problems, but i am letting it rest now. i try to de-dust the innards every few months but it has been almost six months now since i've done this.

UPDATE
the machine will boot into pclinuxos live environment when i choose to boot into safe mode.
i'm guessing this means some hardware has died, such as the video card.

---

### Post by torgrot on 2008-01-20
> **apunc1 said:**
> fdisk? i can't get to a command line. i may be able to with the live cd. i'll try again.

NO, not fdisk, the command to check your drive, I am experiencing acute brain farts at present and don't remember the command.  It is below zero F here and early in the morning.  It is efs*** something.  I will try to find the command.

Just remembered e2fsck  

torgrot

---

### Post by apunc1 on 2008-01-20
new development:
i let the computer sit for about 30 minutes and now when i boot, there is nothing but a blinking red screen. blinking red with + symbols. i think there was a little white in there too. ;)

earlier i was able to boot with a live cd in safe mode, but this red blinking thing is new. bad video card?

---

### Post by torgrot on 2008-01-20
Can you get into the bios?  Hit F2 or whatever your comp requires.  If it can display the bios screen it probably isn't your video card.  

torgrot

---

### Post by sowelie on 2008-01-20
I would say it's almost definitely a video card problem.  Do you have on board video or another video card you could try?  Is your card AGP, or PCIX?  If so the slot could have fried, that happened to me once.  If it were memory, you'd probably be seeing freezing, but probably not graphical artifacts.  Unless it's an onboard video card, in which case your memory could cause graphical atrifacts because your onboard video most likely uses your memory.

---

### Post by apunc1 on 2008-01-20
> **sowelie said:**
> I would say it's almost definitely a video card problem.  Do you have on board video or another video card you could try?  Is your card AGP, or PCIX?  If so the slot could have fried, that happened to me once.  If it were memory, you'd probably be seeing freezing, but probably not graphical artifacts.  Unless it's an onboard video card, in which case your memory could cause graphical atrifacts because your onboard video most likely uses your memory.

thanks. i'm probably going to have to take it to the shop. i'm not very good with hardware troubleshooting.
i don't have another video card to try. i think mine is a nvidia nforce2 something

---

### Post by apunc1 on 2008-01-21
Thanks for everyone who replied. It was not a hardware problem, but a grub problem.
I reinstalled grub and the system works normally. 

I followed the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

i guess i could have used supergrub disk too, but i found mine about the time i got the ubuntu live cd to load, so i just did it inside ubuntu live environment.

---

