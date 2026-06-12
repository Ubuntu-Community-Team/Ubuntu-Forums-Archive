---
title: "Yet another dual boot question"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-02-13
I'm a bit concerned about reinstalling ubuntu after my mobo failed, and I was hoping y'all could help, as I don't know much about hardware. I have:

1 40GB IDE HD w/ XP
1 30GB IDE HD to reinstall Ubuntu
1 IDE DVD-ROM 
1 IDE CD-RW
A brand new mobo w/ 1 IDE channel
A PCI to IDE Adapter card (Siig UltraATA 133)

If the optical drives are connected to the card, I cannot boot from them. I was thinking I could hook one optical drive and my XP HD up to the IDE on the board, and hook my Ubuntu HD up to the controller card, so I can boot from the Live CD and install GRUB to the MBR on my XP drive, and install Ubuntu to the drive on the PCI card. I then plan to move both HD's to the IDE channel on the board and both optical drives to the PCI card (I'm hoping not to have to do it the other way around).

My questions:
Does Ubuntu generally recognize adapter cards?
Will there be any problems switching the drives around after the install?
Anything else I need to know or keep in mind whilst doing this?

Man, this is like one of the problems I had to do in Finite Math. Rearrange your computer's  drives subject to the following constraints... :)

---

### Post by louieb on 2007-02-13
Don't know about the adapter card. But after you switch your drives around. My wild guess  of the day is your will get a GRUB error 21 (drive not found). Probably fixable but I can't guess how. 
I think you are going to have to have the Ubuntu drive and the optical drive on the IDE channel during the install and install GRUB to the MBR of the Ubuntu drive. 
The you can install the XP drive as slave on the IDE channel and add an entry in /boot/grub/menu.lst to boot XP on the slave drive that looks something like this:
The map commands are there to make XP think it is installed on the primary drive.
```

title Win XP 
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1

```This way the XP drive is untouched and you can check how Ubuntu and XP works with the PCI card. 
It makes it interesting (harder) when you have to change where drives are plugged in to after the install.

Was Ubuntu install on the second drive prior to the motherboard going out? 
If so is GRUB installed in the MBR of the XP drive?
My answer might change depending your answer to these questions.

---

### Post by Hitchhiker42 on 2007-02-15
Yes, Ubuntu was on the second HD before my mobo died. However, I reinstalled 98 on the first drive, in hopes of fixing some problems with it and the new mobo (turns out the mobo drivers only work on XP, hence my recent upgrade). The original first drive has 98 reinstalled on it. XP is currently on a third (very old) drive, but is about to be moved to the drive that currently has 98. ETA: Once I move XP, the third HD will no longer be in my computer.

The upshot of all this? If my MBR wasn't overwritten already, it certainly will be by the time I get finished jumping through hoops making Windows happy. (I need it for school, otherwise I would seriously consider not bothering.)

I'm crossing my fingers, hoping maybe I can boot the HDs from the controller, and not have to change anything, (Yeah, I wanted to connect the HDs to the mobo, but I'm kinda tired of dealing with this.) but I don't know as yet.

---

### Post by confused57 on 2007-02-15
> **Hitchhiker42 said:**
> Yes, Ubuntu was on the second HD before my mobo died. However, I reinstalled 98 on the first drive, in hopes of fixing some problems with it and the new mobo (turns out the mobo drivers only work on XP, hence my recent upgrade). The original first drive has 98 reinstalled on it. XP is currently on a third (very old) drive, but is about to be moved to the drive that currently has 98. ETA: Once I move XP, the third HD will no longer be in my computer.

The upshot of all this? If my MBR wasn't overwritten already, it certainly will be by the time I get finished jumping through hoops making Windows happy. (I need it for school, otherwise I would seriously consider not bothering.)

I'm crossing my fingers, hoping maybe I can boot the HDs from the controller, and not have to change anything, (Yeah, I wanted to connect the HDs to the mobo, but I'm kinda tired of dealing with this.) but I don't know as yet.

I don't really know what a viable solution would be, but PCI to IDE(or SATA) adapters do not support Ubuntu, therefore you'll have a lot of trouble with Ubuntu recognizing it.

You "might" be able to connect your drive you'll be installing Windows to the master controller and your cd drive to the slave, set your bios to boot first to the slave drive...install Windows, once you have(hopefully) Windows up and running...disconnect the Windows drive & reconnect the drive you'll be installing Ubuntu to(set as master)...install Ubuntu, once you have it installed & working OK, disconnect the cd drive on slave & connect the Windows drive as slave.

The Windows entry louieb gave should be added to your /boot/grub/menu.lst to boot Windows, see this link:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I'm just throwing out a suggestion, since Ubuntu may not be able to "recognize" your PCI to IDE adapter, you probably won't be able to use the cd drive in Ubuntu, unless you disconnect your Windows drive & reconnect the cd drive to your slave controller, if you need to use the cd drive in Ubuntu...Windows should have no problem with the cd drive connected to the adapter, since it probably came with Windows driver support.

I'm mainly speculating here, none of this may work; but I wanted to point out problems I've seen other people have with this kind of adapter.

I'm not sure what you're planning with Windows, reinstall or move; but you should still be able to connect it to the slave drive, after you install Ubuntu as I described above.

---

