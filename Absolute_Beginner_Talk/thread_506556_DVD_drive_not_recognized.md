---
title: "DVD drive not recognized"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by TL_Mechanic on 2007-07-21
I have read (and tried) a number of threads on this topic without success.  I'm hoping that posting some of my specific information will get a few leads to help me solve my issue.

As noted above, my DVD drive is not recognized.  This is a new install of Feisty 7.04 from the live CD.  The DVD drive is recognized and works with the live CD.  Looking at device manager prior to running the install, the DVD is recognized as a SCSI device /dev/scd0.  After running the install, the DVD is no longer recognized in device manager.  The live CD has kernel 2.6.20-15.  Updating to 2.6.20-16 has no effect.

There is an icon in File Browser for CD-Rom 1.  Attempting to mount this results in an error message "Mount: special device /dev/scd0 does not exist".

There is a line for the drive in fstab:
   /dev/scd0   /media/cdrom0   udf,iso9660 user,noauto    0     0

There is no entry for the DVD in mtab.  There is no scd0 item in /dev.

Everything else on the system is working fine.  The hard drive and ethernet are ok.  The system recognized a USB flash drive.

This unit currently has only Ubuntu installed.

Any help would be appreciated.

Tony

---

### Post by kyphi on 2007-07-21
The entry in your fstab file looks normal.

Have you looked in System -> Administration -> Disks if your DVD is listed?

Have you tried just putting a music CD in and letting it autoplay?

---

### Post by TL_Mechanic on 2007-07-21
A music CD does not play.  The disk spins up and the LED on the drive lights, but no music and no recognition of the drive.

I don't see a "Disks" under System -> Administration.  Could that be part of the problem?

It does not show up under System -> Preferences -> Hardware Information.

Tony

---

### Post by kyphi on 2007-07-22
Did you install the optical drive?  It obviously has power to it.  If you did, you may like to recheck your connections.  A fault there seems unlikely because Feisty installed OK.

What make is it?

I have an Intel 965 board which would not recognise either of my optical drives so I switched them both to SATA.  I am using Dapper Drake 6.06.  I had noticed that Feisty recognised both optical drives while they were connected via IDE - too late for me because I had only just taken delivery of the new SATA drives.

Can you run the installer again without losing too much?

Disks Manager you will find in the Alacarte Menu Editor under Administration.  It will list all yout drives including your partitions.and the capabilities of your optical drives.

---

### Post by TL_Mechanic on 2007-07-22
I did install the drive (actually a ground-up build of the computer).  It's an LG GSA-H62NK  DVD+- RW on SATA.  I'm using a BioStar TF7050 MOBO.  I was considering swapping drives, but I don't have an extra sitting around right this minute.  I'm not ready to pull one out of a working computer just yet, but getting closer.

I did a full re-install (Guided Partition - entire disk) from the live CD with the same results.  Optical drive works fine for live CD but disappears after running the install.

Thanks again for your help with this.  I really want to make this work.  If nothing else, it's the best how to do Linux lesson I've ever had.

Tony

---

### Post by kyphi on 2007-07-22
I just ran a Feisty installation via VirtualBox and then realised that there is no Alacarte Menu Editor in Feisty.

I also checked out your main board but could not determine with certainty who made the SATA controller.  The chipset generally seems to be Nvidia who are supposedly Linux friendly.

One of my optical drives is an LG GSA-H62NBBK (the BK means black) and it works fine.

I assume that your hard drive is also SATA.

The only ideas that I can come up with at the moment are:

1.  Switch the optical drive to another SATA port assuming that there are more than one SATA controller and that the one SATA controller does not host all four of the ports.

2.  Try the LG in another machine to check that it works as it should (but I don't think that is it)

3.  Substitute another SATA DVD drive to see if it is a Feisty problem (perhaps you can borrow one).

4.  Try an optical drive and connect via IDE (mind the master/slave settings there).

5.  Try another version of Ubuntu - I run 6.06 (supported until 2009).

I have checked launchpad for bug reports but found none for SATA controllers.

I would like to follow this through, so would you keep me up to date please.

Addendum:
Which version of Feisty have you installed?  64 bit or 32, AMD or 386 or 686

---

### Post by TechieZero on 2007-07-23
> **TL_Mechanic said:**
> ...my DVD drive is not recognized.  This is a new install of Feisty 7.04 from the live CD.  The DVD drive is recognized and works with the live CD. 


Wow this sounds like my problem exactly. I have installed on an older Sony Vaio desktop that has a CD & DVD-RW drive. I booted and installed using that drive but now when I try to burn an ISO using CD/DVD Creator --- the DVD-RW drive does not appear in the pull-down list --- however the CD drive *does* (but it's not a burner...). 

This is as far as I got and I am not home to look at the other stuff mentioned here --- but most likely I am in the same boat as you are.

---

### Post by Mornedhel on 2007-07-23
I had this problem back in Dapper, was fixed when I switched to Feisty. The most curious part was that everything would run fine (burning and all) if I had gone through the entire booting sequence with a CD or a DVD in the tray, but the system would claim that /dev/scd0 did not exist if I hadn't.

Oh, and kyphi : Alacarte is still there, it's just called Main Menu now. It's in Preferences.

---

### Post by TL_Mechanic on 2007-07-23
Just to see what happens, I switched around the SATA cables for the hard drive and the optical drive.  The original set up had the hard drive on SATA1 and the DVD on SATA2.  I made DVD #1 and HD #2.  At start up grub loaded and Ubuntu tried to start.  It got as far as the thermometer bar and stalled out.  I assume that somewhere in the start up process it stopped recognizing the SATA2 port, but it worked at least long enough to begin booting.  I restarted and at grub selected recovery mode.  It spit out - alot- of text, but stalled out at where it appears to be doing something with the SATA configuration.  I returned the cables to their original order and I am back to where I started (working system - no DVD).  I'm convincing my self that somehow Ubuntu and SATA are not playing nice together.

In the mean time, I'm scrounging around for a PATA drive to tryout.  I'd really like to get this work though.

I hope this makes sense to somebody.

Tony

---

### Post by kyphi on 2007-07-23
And what happens if you leave the hard drive on SATA1 and put the DVD on SATA4?  After doing that have a look in your BIOS to see that the swapped connections are registered.

---

### Post by TL_Mechanic on 2007-07-23
Moved the DVD to SATA4.  The change does show up in the BIOS no problem.  Still no recognition after boot, however.  Just for good measure I also tried SATA3.  Same results.

Also, from your previous question.  I started with the AMD64 version and had the issue with the DVD.  I re-installed the 32-bit version (i386 - desktop) to see if that was my problem.  Same issue with DVD on both.  I currently have the 32-bit installed and I am inclined to stay with that.

Thanks again.

Tony

---

### Post by deadlikeoscar on 2007-07-23
A lot of people that have had trouble with drives have had success changing /dev/scd0 to /dev/cdrom in fstab.

---

### Post by TL_Mechanic on 2007-07-24
I am very happy to report a success.  After much stumbling around, I went back to my SATA setup in the BIOS.  The default setup was IDE.  I changed it to AHCI and my optical drive sprang to life.  Apparently the IDE setting worked well enough to boot the live CD but nothing else.

I'll have to try and figure out why some day.

THANK YOU...THANK YOU...THANK YOU to everyone who helped my out with this.  I'm more convinced than every that I'm done with windows.

Tony

---

### Post by kyphi on 2007-07-24
Great news, Tony.

The AHCI is your Advanced Host Control Interface for SATA drives.

Now there will be no stopping you....

And ... a message to Mornedhel, who said:
> Alacarte is still there, it's just called Main Menu now. It's in Preferences
Thanks for pointing that out.

---

### Post by TechieZero on 2007-07-25
> **TL_Mechanic said:**
> I am very happy to report a success.  After much stumbling around, I went back to my SATA setup in the BIOS.  The default setup was IDE.  I changed it to AHCI and my optical drive sprang to life.  Apparently the IDE setting worked well enough to boot the live CD but nothing else.

I'll have to try and figure out why some day.


I have to say that my situation reflects yours once again with the exception that my BIOS is not as fancy and no changes to the settings are possible as it is an old machine. I can read the live CD in my DVD-RW but can do nothing else with it.

Maybe it's a formatting issue? Are ppl able to read windows formatted CD/DVDs on their drives?

---

### Post by TechieZero on 2007-07-26
:guitar:

Hello..hello...hello...

Is there anybody out there?

Just nod if you can hear me...

---

### Post by TechieZero on 2007-07-26
I am all fixed! :)

I went out to here [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) and figured out what fstab was all about and saw that my configuration was NOT set to auto in order to detect the type of file system/medium was in the drive. A quick change and it is all working.

:popcorn:

---

