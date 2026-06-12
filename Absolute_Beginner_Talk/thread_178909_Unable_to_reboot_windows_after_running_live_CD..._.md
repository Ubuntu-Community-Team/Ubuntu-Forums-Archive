---
title: "Unable to reboot windows after running live CD... Help!!!"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by dckirba on 2006-05-18
Hey everyone,

I am an absolute beginner so I hope I'm posting this in the right place. I ordered free CDs from Shipit, eagerly waited for 4 weeks and was extremely delighted when they arrived on the promised fouorth week :) I ran the live CD at work, everything went beautiful. I ran the live CD at home and everything went even better because I have a faster system at home. I love the interface, am thoroughly impressed. I was so impressed I had to show off so I took the CD with me to my friend's house and ran it on her computer. Now, I didn't check the configuration of her system before I ran the live CD but it ran and it started albeit extremely slowly. Once everything was up, I tried clicking on the menus but nothing would open. I couldn't log out so I shut down the system and took out the CD when I restarted it. But the system keeps looking for a system disk in the CD drive and refuses to boot from the hard disk. I entered the BIOS and changed all the boot options to hdd0. but it still asked for a system disk in the CD drive. Any suggestions? I have to fix it before her sister gets back :) Bit of a fix here. HELP!!!!

Thanks in advance, 

I actually have some questions about getting my modem to work when I run UBUNTU from the live CD. I want to make sure everything works well before I try installing it and running a dual OS thingy. But I'll save those for later.

Cheers,

David K

---

### Post by gerbman on 2006-05-18
As a last resort, you might try restoring the master boot record on the Windows drive. Boot into
the Windows installation CD, and select the "Fix MBR" option (or something like that, I don't remember 
exactly what it's called). I can't imagine why the LiveCD would corrupt your MBR, but who knows.

I've only done this with XP.

---

### Post by Sef on 2006-05-18
A Live CD shouldn't be able to change the boot master.  What has happened it seems there is some corruption in it.  I would try Gerbman's suggestion.  If you don't have the Window's CD, then download this rescue cd.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by r4ik on 2006-05-18
To get your windows back,
Boot from cd choose R(recovery)
In step one the suggested default is oke.
Step two adminpasswrd if you got one type it and hit enter or else just hit enter.

Command is fixmbr answer y(es) and hit enter again.

Abourt and reboot.

Good luck !

---

### Post by redistributer on 2006-05-18
That all depends on the system. Go into the bios first and make sure that the system is detecting your HDD. Look at the primary channel of the IDE or SATA on the standard settings, if it shows no device.... well the hdd just happend to go out when you ran the CD not your fault. Unless of coarse a cable came loose or something in that case you can look inside and make sure the cables are firmly attached to the drive and the board. 

If it does show up in the bios do as stated above then the configuration is damaged and will need to be repaired. Ubuntu live cd cannot cause this issue due to the fact that the mbr for the live disk is on the live disk so it will not come in contact with the mbr on the hard disk, it will however try to make space on the disk for virtual RAM if the RAM of the system is not sufficant (1 Gig will hold the entire program) this could have caused a cluster if the HDD was low on space to begin with. 

Run the windows install disk, Press F8 to pass the EULA, go to the Repair (option R) as stated above, when it promps you tell it you would like to go to the console (option C). Once in the console pick the install dir (if none is show the disk is damaged) Once at the prompt use the command  "chkdsk /r" to check disk and repair, this will fix most issues and resolve cluster (at least that is what MS wants you to believe) then run FIXBOOT command. type exit and the computer will reboot hopefully you get windows, if you do not check in the bios to insure HDD-0 is in the boot load sequence. If it is, well you might have to re-install windows. 

Good Luck 

-Red

---

### Post by dckirba on 2006-05-18
Thanks a lot everyone. Will try this over the weekend. Do you think we've lost data on the disk?

I have no idea why this happened because i tried the live CD at home again and all worked well. Strange. I will post again to let you know what happened.

Thanks again,
David K

---

### Post by catlett on 2006-05-18
Did you put the live cd in her setup again? She might have a slow computer and you pulled the plug too soon. Since you have nothing to loose I would put the live cd in and boot. Hopefuly that is what it is looking for. Maybe the bios program to boot to the cd is in a loop (I know that isn't the right word but it makes my point I think)
Hopefully  it will boot. Give it plenty of time to boot. (What kind of mouse does she have? usb or ps2 I've had problems with usb mouses not being detected in other linux distros) With luck you can boot and shut down properly. With more luck it will get the boot process out of trying to find a disk in the cd.
The fixmbr couldn't hurt. If it works it probably will have more to do with a bootable cd being in the drive than the mbr. Because I don't think the mbr is corrupted. I think the boot process is stuck somehow on looking for a disk in the cd drive. Good luck either way.

---

### Post by confused57 on 2006-05-19
Does sound like a bios corruption, especially if you did a hard shutdown...you may be able to go into bios and reset the boot options to "default" values or something to that effect.  I'd be sure to write down the current settings, before making any changes so you can change things back if you need to.  

May want to try booting up with the CD drive cables disconnected to see if it will boot to the hard drive.

---

### Post by S{yndrom}e on 2006-05-19
will setting the bios to boot hard disk before cd have any effect? I guess u could try that

---

### Post by dckirba on 2006-05-21
Hey everyone,

I haven't done anything about this yet. But the day it went cuckoo on me, I did try rebooting with the live CD. It started after ages but once I got to the startup screen there was no way I could use any of the menus to exit. They just wouldn't work The only thing that did work was right-clicking on the desktop. I also did try making all boot options hdd0. That didn't work either. Will try windows recovery and let you knwo what happens. Thanks a lot for your help.

Cheers,
David K

---

### Post by bigken on 2006-05-22
if the fdiskmbr dosent work try **bootcfg /rebuild** in repair console ;)

---

