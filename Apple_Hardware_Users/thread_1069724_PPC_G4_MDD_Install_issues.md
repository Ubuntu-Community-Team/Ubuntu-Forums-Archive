---
title: "PPC G4 MDD Install issues"
date: 2009-02-14
forum: Apple Hardware Users
---

### Post by louv on 2009-02-14
I have a G4 MDD 1.25GHz dual-PPC , which will not install any 7,8 Ubuntu's.
I have successfully used each of the burned ISOs on a G4 800MHz single, so I know the CDs are good.

Further, I have installed, but with trouble, 8.10 alternate (low res graphics only, ATI-rage problem) in a PPC-dual 450. Works good just sucky colors. 

There are several symptoms for the MDD PPC-1.25-dual
.
1) A hd erased with Apple Disk Utiltiy and 2X partitioned as HSF+ , hangs after the first set of text from the boot loader. 

2) Getting ready for a OF boot attempt, I copied the four files, ( yaboot, yaboot.conf, vmlinux, intrd?) to each partition of case 1) and the install CD (8.04-live, 8.04-alt & 8.1-alt) no success.
2a) Now a normal hold-C install gives only a white screen, never any text, etc.

3) there is a comment in the forums that the CD needs to be in the ATA33 connection, this is the stock location, done.

4) I stole the HD from the G4800 with a good install for U-8.10-alt, updated. I understand this probably won't boot but at least the partitions will be correct. Now the First Stage Ubuntu bootstrap menu recognizes both the hd and cd with menu choices of (l,c). 
    A 'l' choice goes to, Loading second stage bootstrap ...
and hangs, ( this what I expect since it was an install from the G4-800 machine)
    A 'c' choice goes to, Booting CDDROM . . .  and hangs

The installs for the G4-800 and G4-450-dual each failed to find the CDROM on install, and I had to break out to a terminal and execute a modprobe ide-scsi. 

Is this a related observation?
What is the next step for the MDD?

---

### Post by louvann on 2009-02-15
How do I modify the yaboot which was installed for the G4-800 to be appropriate for the G4-dual-1250?  OR is this going down a rat-hole?

---

### Post by louv on 2009-02-17
bump

---

### Post by tiresia on 2009-02-18
Just a couple of questions: 
When you try to boot from the CD holding down C, do you get any yaboot prompt?
Did you change anything in the MDD's Hardware (PCI Cards, etc)?
Do you still have a Mac OS X on the MDD?

---

### Post by louv on 2009-02-19
I have two MDD computers.

A) stock, except the DVD drive,
B) stock, except the video card.

Yes, each has a 10.4.x OS on a separate drive.
Each has same / similar results at boot.

Both, A & B, with one extra 'empty' HD for installation, halt at the white screen which is prior in sequence to the yaboot prompt.

For the 'hold C' question, as noted above, I stole a formatted 'Ubuntu' drive from a third computer G-800-single, unplugged all apple OS drives, and then I get to the choice of (l,c) but both hang, but it eventually cycles back to the yaboot menu and optionally without input will do the default choice, only to cycle again.

Additionally, new information, using the 'hold option key' for computer B) (A) is unknown) gives the standard icon menu for bootable volumes. The 1)CD/linux penguin and 2) macOS icons are present indicating the CD and OSX hd respectively. Choosing the CD causes some activity, but it cycles back to the icon menu, but this time the icons are damaged, but the UI is functional. It will cycle back again.

I will be out of touch for the extended weekend Fri,Sat,Sun. I do not want this thread to go stale but cannot reply for those days.

---

### Post by louv on 2009-02-23
Any _last_ thoughts as to the problem hanging on install?

---

### Post by tiresia on 2009-02-24
Let's try focusing only on one machine, that one with the extra video card. 
I would do following: remove the video card, download ubuntu 8.04 (alternate and LiveCD) and burn both at low speed with the Apple Disk Utility on the same Computer where you want to install Ubuntu.
Try to start from one of the CDs. As always, if you experience video issues, boot using 'video=ofonly nosplash'
Let me know, what happens.

If you still have the same issue, we can try to install from an USB memory stick. But it would be important to understand where the problem come from.

---

### Post by louv on 2009-02-24
Thanks for sticking with me.
To clarify, the MDD has a 'different' video-card than stock, not two cards. It is an ATI 9000 Radeon Pro. ( I think this is actually the original now that I did a hardware scan)

I have many install CDs of Ubuntu from installing on many machines throughout time, including Hardy 8.0.4.1 Live and 8.0.4 alternate.

I am using the 8.04.1 LIVE CD which I have used to successfully install on two other PPC computers (ppc-G4-450-dual and ppc-G4-800-single).

The target MDD-G4-1250-dual computer has had its parameter ram reset opt-com-p-r.
The CD is installed in the stock ATA33 - port.
Two hard drives are in the stock HD port, OS 10.4.11 and a data drive.

A warm restart a prior boot of OSX with the 'c' depressed yields:

-the result is an unusable screen with blue vertical bars, alternating 2-3 pixels of black and 2-3 pixels of pure blue. no mouse or kbd response.

This is different than prior runs earlier last week where it hung with a white screen, again prior to the yaboot menus.  I did this three time same blue result.

The video card, ATI 9000 Pro, has two video DVI connectors. I am using the 'D' connector rather than the 'O' connector, since this is the adapter I currently had available for going to a VGA connector, multi-sync analog NEC monitor.

I am almost certain that the video cabling is same. I had taken the setup apart at the end of last week for other work I was doing. 

I wish I could get to the menu for the video-ofonly but not ever succeeded with this machine.












BTW i went through another thread to create a memory stick of 8.0.4 Live. But have not done the open firmware part yet.

---

### Post by louv on 2009-02-24
New Update.

I used the memory stick and OF boot described in URL
[http://ubuntuforums.org/showthread.php?t=780320&highlight=ppc+live+usb+stick](http://ubuntuforums.org/showthread.php?t=780320&highlight=ppc+live+usb+stick)

I can now boot a Live CD on memory stick at the rear usb1 port.

thanks for all the effort from tiresia

Summary:
G4 Mirror Double Door G4-1.25GHz-dual PPC
500 MB ram.
Live boot was possible by moving the 8.04.1 to a memory stick and then open-firmware boot described in the above URL.

An install and all that goes with that is next. I need to clear out the extra drive so I can have a OSX drive and a Ubuntu drive. for dual boot.

Please consider this thread closed for my needs.

---

