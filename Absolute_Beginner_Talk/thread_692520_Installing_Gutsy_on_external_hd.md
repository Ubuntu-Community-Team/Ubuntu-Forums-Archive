---
title: "Installing Gutsy on external hd"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by roscal on 2008-02-09
Hi Linux people!
I have two desktops, one is XP, this one I'm on is Kubuntu Feisty.
I love the kubuntu machine and am trying to install Gutsy onto 
a external 320 gig drive which is currently hooked up to the XP machine.
My objective is to dual boot the Xp machine, using the external drive for Gutsy.
The external drive is brand new.
I booted up the XP machine,and pluged in the external drive,
Then, I rebooted with the Gutsy live CD.
I chose install, pointed the install to the external drive (use entire drive)
The drive was sdb1.
I've been sitting here half an hour, lots of flashing led drive lights going on throughout
that time. 
Now, the XP machine is just a black screen, nothings happening, no joy.
I think I might have messed up big time?

Any pointers?

I'm kind of stuck here, don't know what to do.
Should I unplug the external drive or try rebooting or sheesh , I really don't know.
I hope I haven't toasted the XP machine or I'm gonna get toasted when my wife gets home
:popcorn:

---

### Post by roscal on 2008-02-09
Progress report.......
Well, this is absolute beginner talk after all...
My screen was black I just moved the mouse and screen came on
and told me installation was successful.
:)
Shut down the machine, removed the Live CD and am about to try to boot.
I'm sweating, .....if I trashed the XP machine I'm trash, my wife is home in 2 hours 
and she's gonna have a bird.

---

### Post by roscal on 2008-02-09
On booting I'm getting 
Grub error 18?????

I think I'm in the doghouse, can anyone help?

---

### Post by gate on 2008-02-09
I did this before I knew enough to fully switch to Linux back a few years ago. The problem I hit was that GRUB pointed to the external HDD and the internal now waited for it, if you leave the drive in it will boot and with it out it won't. (My experience in the 6.06 days). Windows will be undamaged as long as you didn't wipe that drive, so fixing the boot sectors will be all you have to do. (and wow, I did it on a 40GB)

  Good luck!

---

### Post by roscal on 2008-02-09
Oh wow, now I have Grub error 21 on rebooting with the external unplugged.
Can't seem to boot off the internal hard drive in the XP box
Trying now to boot with the external plugged in and the live cd.
I think I did a major boo boo,.
Anyone here, please help me save my marrage lol:guitar:

---

### Post by roscal on 2008-02-09
Now I'm really lost.
I think I have Gutsy installed on the brand new external 320 gig HD.
However it is unplugged at the moment, while I try and recover my wife's files on
the XP machine (oh.. I'm in trouble here, lol). 
I think I might try the external drive on this machine (dedicated Fiesty machine) and see what happens?

---

### Post by gate on 2008-02-10
Fix for windows, if you have a windows install CD you can run it with 'repair' and do a fixboot. Otherwise, you can try using the 'boot from first hard disk' option from the Ubuntu disk. Finally, you can use the Ubuntu disk (liveCD is easiest here) to fix the GRUB stuff to work properly.


   Question: does the grub error happen before or after the menu?

---

### Post by gate on 2008-02-10
If you want help with some better response time, I am in an IRC room, #ubuntu-us-ut on freenode

---

### Post by roscal on 2008-02-10
Windows is toast and  now I can't even install Kubuntu on the machine.
I keep getting Grub errors.
Trying all kinds of terminal commands but hey, I'm a noob.
:(
Been at this for 8 hours now lol:)
I think I have to put Grub in the right place somehow????
The disc won't install...help!

---

### Post by roscal on 2008-02-10
I think I have installed/rebuilt Grub to the Root directory.
(Sure hope so I'm at 41% installed for Gusty).
Haven't been able to install anything, Grub errors all night.

Wife's comp is toast (all backed up though).
No XP, no Linux, nothing will install ,grub errors.
I have talked her into trying Linux on her machine,
I just have to install it somehow.:guitar:

---

### Post by jan quark on 2008-02-10
hm sry that I barge in  the middle of the battle so to speak

but when you managed to boot again try this guide to install ubuntu on an external drive

in the meantime I will think how to rescue your nuked system

[http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/2007/11/13/installing-ubuntu-to-a-usb-hard-drive/)

---

### Post by roscal on 2008-02-10
Thanks jan quark!
I've saved that info for tommorow.
I'll try and boot from the external usb drive then.
I think I've overheated the wifes machine, and my own brain tonight.
I'm not getting anywhere now, no install of anything
and the computer (and my brain), is overheated and spinning wildly.
Time for some sleep eh...? 
Thanks..

---

### Post by roscal on 2008-02-10
There's no option in Bios to boot from USB????

---

### Post by rkd on 2008-02-10
Older computers did not have the option to boot from USB. If your computer is not very old, perhaps you are just overlooking how to select boot from USB. 

If you have the owner's manual for the computer or for the motherboard in the computer, that should tell you whether it can boot from USB and how to set it up, if it can. 

If you don't have the manual, many of them are available online at the manufacturer's web site. If you can't find it online, tell us the computer make and model or make and model of the motherboard and one of us might be able to find it.

Even if your computer doesn't have a BIOS option to boot from USB, it usually is possible to use a utility program to boot from the USB drive. I believe Super Grub and maybe ordinary Grub can do that. But let's not look into that unless we find the BIOS really doesn't have the option.

Unless you slipped up somehow, the Windows installation on your computer will be intact. The problem that is causing the errors is because the Ubuntu installation tried to set up a menu to let you choose between booting Ubuntu and Windows, but the fact that the Ubuntu is on the USB drive makes that tricky. Unless something you did while trying to correct that booting problem damaged the Windows installation, it is pretty simple to get things back to where you can boot Windows normally. Super Grub is probably the easiest (though the documentation is hard to follow, if someone just tells you the steps, it is easy).

So DON'T PANIC. The Windows installation probably is still there and can be brought back rather easily, once you know the trick. If you want directions on doing that, post here to ask for that and I (or someone else) will tell you how to do it.

---

### Post by gate on 2008-02-10
well, no matter what you did with the USB drive, once you take it out the Linux install should work fine.

---

### Post by rkd on 2008-02-10
gate:

Not if Grub is trying to find its menu on the USB drive.

---

### Post by gate on 2008-02-10
what I meant is the linux install*er* :) should work fine. The process that it took for me to get mine working back in the day was install to the USB drive, remove the drive and use a windows disk to fixboot windows, then set the BIOS to prefer the USB drive which had GRUB on it.

---

### Post by smartboyathome on 2008-02-11
My suggestion would be reinstalling Window's bootloader with the USB hard drive unplugged, and then if you can remove the hard drive from the laptop and install Ubuntu on the USB drive. Otherwise I would recommend still reinstalling windows bootloader like previously mentioned, but instead of removing the hard drive follow [this guide]("http://ubuntuforums.org/showthread.php?t=678146"). I got Ubuntu installed on a similarly sized hard drive using that guide.

---

### Post by roscal on 2008-02-11
I fixed it sort of.
The mbr was corrupt on the machine, I couldn't load anything.
I booted the XP disc and in recovery mode used fixmbr command.
Couldn't figure out how to do it in Linux.
Anyway, the machine then was able to load Gutsy no problem. I've had it with windows, 
and my wife seems to like it, so far so good (it was her machine)
:)
Lol, now I have a fresh 320 gig external with gutsy installed also.
Thanks for your help everybody.

---

