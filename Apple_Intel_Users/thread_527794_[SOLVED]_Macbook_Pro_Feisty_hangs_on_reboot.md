---
title: "[SOLVED] Macbook Pro Feisty hangs on reboot"
date: 2007-08-17
forum: Apple Intel Users
---

### Post by soonaboom on 2007-08-17
I've attempted to research the problem on my own (googled for days) but I am unable to reboot.  The system shuts down ok but fails to boot once it has exited the OS.  I can hear the cd drive load like it does when you turn it on but then it hangs.  Any help, encouragement, free beer, would be much appreciated.

---

### Post by ronocdh on 2007-08-17
> **soonaboom said:**
> I've attempted to research the problem on my own (googled for days) but I am unable to reboot.  The system shuts down ok but fails to boot once it has exited the OS.  I can hear the cd drive load like it does when you turn it on but then it hangs.  Any help, encouragement, free beer, would be much appreciated.
Is Ubuntu the only OS installed, or are you double or triple booting? Also, is there any kind of verbose output while the system is going down that would help you know where the failure or hang is occurring, or is it just the Ubuntu logo and progress bar?

I wouldn't hesitate to reinstall if I encountered this problem on a new system... just remember to only do it on an installation CD whose checksum you've verified.

---

### Post by soonaboom on 2007-08-18
> **ronocdh said:**
> Is Ubuntu the only OS installed, or are you double or triple booting? Also, is there any kind of verbose output while the system is going down that would help you know where the failure or hang is occurring, or is it just the Ubuntu logo and progress bar?

I wouldn't hesitate to reinstall if I encountered this problem on a new system... just remember to only do it on an installation CD whose checksum you've verified.

I am dual booting OS X and Ubuntu, the system shuts down completely and begins to initiate a reboot then just hangs after the cd-rom starts up, the screen is completely black and there is no error output while it is shutting down.  I'll re-download and create an iso to make sure I have a proper install and post my results.  Thank you for the reply.

---

### Post by soonaboom on 2007-08-18
I checked the iso I used to install ubuntu and it was the proper checksum.  This is the second time I installed the OS on my Mac, kinda surprised no one else experienced this problem.  Going to go with a different install, maybe Xubuntu, or Kubuntu.  I'll post my findings.

---

### Post by ronocdh on 2007-08-18
> **soonaboom said:**
> I checked the iso I used to install ubuntu and it was the proper checksum.  This is the second time I installed the OS on my Mac, kinda surprised no one else experienced this problem.  Going to go with a different install, maybe Xubuntu, or Kubuntu.  I'll post my findings.
Which version were you using? I've run Dapper, Edgy, and Feisty on my MBP (2nd gen), and while I've certainly had my fair share of issues, I don't recall this being one of them. I encourage you to reinstall and see whether that helps. I certainly don't think the answer lies in choosing Xubuntu or Kubuntu instead of Ubuntu. (I encourage use of both variations, but for their respective advantages, not in the name of an inchoate suspicion that installing them might avoid a poorly documented and perhaps merely incidental bug.)

---

### Post by soonaboom on 2007-08-18
Just went through reinstalling 7.04 alternate cd, ran checksum and installed.  X failed (like it does) updated, installed fglrx driver and shut down.  I booted up into Ubuntu and tried to reboot, no dice.  Same symptom as before, the operating system completely shuts down goes to a black screen with no errors.  I hear the cd-drive start up like its going to boot into reffit but it stays with the black screen, waited about 10 minutes this time for it to boot.  I'm going to try 6.06 tomorrow to see if I get different results, not really sure if that will make a difference.  Is there a log that I could check that might have some information as far as an error code?  Should I attempt to use grub as my boot loader instead of reffit?  Not sure if that's the right terminology but if you have any ideas I'm willing to give them a shot.  Either way, I appreciate your help.

---

### Post by cyberdork33 on 2007-08-18
I am going to have to say that I don't think it is an issue with Ubuntu. Maybe reinstall / update rEFIt? 

rEFIt is not a bootloader, and you will not be able to use Grub in its place (well i guess you could but not in your situation). You actually do not have to use rEFIt at all, but am guessing that it is stalling on bootup while rEFIt tries to detect bootable volumes. 

Do you have a disc in your cd drive when trying to bootup?

---

### Post by soonaboom on 2007-08-19
I just reinstalled for the third time this week, still having the same problem.  Haven't touched reffit so I'll give that a go next.  You say I may not need reffit, is that the case if I'm dual booting with OS X and Ubuntu?  I'll start looking into updating reffit and post the events that follow.  Thanks for the help.

No I don't have a disc in the drive when trying to reboot.

---

### Post by cyberdork33 on 2007-08-19
> **soonaboom said:**
> I just reinstalled for the third time this week, still having the same problem.  Haven't touched reffit so I'll give that a go next.  You say I may not need reffit, is that the case if I'm dual booting with OS X and Ubuntu?
Yes, rEFIt is not a bootloader. It is just a menu system that uses the EFI bootloader. You can use the Mac/Bootcamp default way to select the volume to boot, but usually rEFIt makes things a bit easier. There is no reason to get rid of it, I was just making a point that it is actually not required to dual boot.

---

### Post by soonaboom on 2007-08-20
Decided to start all over, completely reformatted my hard drive and reinstalled OS X.  I used diskutil to resize my hard drive 30G for linux 2G for swap and the rest for OS X.  I then installed linux with 7.04 alternate cd.  Next I installed refit in OS X made sure to enable-always.sh and booted into Ubuntu.  So without going further ran sudo reboot and got to the same black screen  (although I did hear the mac starup chime this time)  and no forward movement.  I'm at a loss, really don't know where to go from here.  Any suggestions?  I'll try whatever you think is best.  I love, absolutely love having Ubuntu on my Mac.  Once again thanks for the help.

---

### Post by cyberdork33 on 2007-08-20
> **soonaboom said:**
> Decided to start all over, completely reformatted my hard drive and reinstalled OS X.  I used diskutil to resize my hard drive 30G for linux 2G for swap and the rest for OS X.  I then installed linux with 7.04 alternate cd.  Next I installed refit in OS X made sure to enable-always.sh and booted into Ubuntu.  So without going further ran sudo reboot and got to the same black screen  (although I did hear the mac starup chime this time)  and no forward movement.  I'm at a loss, really don't know where to go from here.  Any suggestions?  I'll try whatever you think is best.  I love, absolutely love having Ubuntu on my Mac.  Once again thanks for the help.

have you checked that you have installed all the OSX updates (firmware)

---

### Post by soonaboom on 2007-08-20
Boot ROM Version:	MBP22.00A5.B01
  SMC Version:	1.12f5

Yep its up to date.

---

### Post by soonaboom on 2007-08-21
Shot in the dark:
So I formatted my hard drive, reinstalled OS X, updated and installed BootCamp.  Resized my hard drive (32G for Ubuntu) and booted with Ubuntu 6.06 Live CD.  I installed gparted and resized the 32G portion to allow for swap, formatted the linux partitions and rebooted.  One thing I thought was odd, it did the same thing with the Live CD and just hung there with a black screen and the apple startup chime.  Argh.   I booted back up with Feisty Alternate CD and installed and rebooted, same thing blank screen.  Looks like I'm going to have to live without the reboot option on my macbook pro.  What gets me is that even the Live CD wasn't able to reboot properly.  Didn't even have reffit installed, was just using bootcamp.

---

### Post by cyberdork33 on 2007-08-21
> **soonaboom said:**
> Shot in the dark:
So I formatted my hard drive, reinstalled OS X, updated and installed BootCamp.  Resized my hard drive (32G for Ubuntu) and booted with Ubuntu 6.06 Live CD.  I installed gparted and resized the 32G portion to allow for swap, formatted the linux partitions and rebooted.  One thing I thought was odd, it did the same thing with the Live CD and just hung there with a black screen and the apple startup chime.  Argh.   I booted back up with Feisty Alternate CD and installed and rebooted, same thing blank screen.  Looks like I'm going to have to live without the reboot option on my macbook pro.  What gets me is that even the Live CD wasn't able to reboot properly.  Didn't even have reffit installed, was just using bootcamp.
Have you tried other bootable media? Like another distro? A windows Cd when you reboot? something? I am really starting to think that it is not a Ubuntu issue at all, but if other live cds work OK, then I would file a bug report on it.

---

### Post by soonaboom on 2007-08-21
Heh, I had hoped that it wouldn't come to this.  I have a windows cd I will go ahead and load it up and reboot, then remove it right away.  I'll let you know whether it boots properly or not.  I saw a tutorial on the forums on using grub soley for your bootloader, looks like a lot of work but I think it would be worth it to get Ubuntu to work.

---

### Post by cyberdork33 on 2007-08-21
> **soonaboom said:**
> Heh, I had hoped that it wouldn't come to this.  I have a windows cd I will go ahead and load it up and reboot, then remove it right away.  I'll let you know whether it boots properly or not.  I saw a tutorial on the forums on using grub soley for your bootloader, looks like a lot of work but I think it would be worth it to get Ubuntu to work.
I don't know that it would help because the EFI bootloader still has to hand control over to the emulated BIOS. Can't hurt to try I guess.

---

### Post by soonaboom on 2007-08-21
Well I had windows installed and it attempted to reboot but got stuck on the same black screen.  Must be a problem with my computer.  Thanks for your help with this guess I'll have to stick with OS X or deal with Ubuntu not restarting.  Either way I really appreciate your help.

---

### Post by cyberdork33 on 2007-08-22
> **soonaboom said:**
> Well I had windows installed and it attempted to reboot but got stuck on the same black screen.  Must be a problem with my computer.  Thanks for your help with this guess I'll have to stick with OS X or deal with Ubuntu not restarting.  Either way I really appreciate your help.
Since we have narrowed it down to something that would occur even with just windows, I would check in the Apple support forums and see if there is anyone experiencing the same issues.

I couldn't find much, I think this might be a good thread to watch. No solution yet, but there are others with the issue out there. If enough people complain, maybe Apple will issue a fix:
[http://discussions.apple.com/thread.jspa?messageID=5119552](http://discussions.apple.com/thread.jspa?messageID=5119552)

This is not really any help, but someone had a similar issue: 
[http://forums.macrumors.com/archive/index.php/t-218423.html](http://forums.macrumors.com/archive/index.php/t-218423.html)

---

