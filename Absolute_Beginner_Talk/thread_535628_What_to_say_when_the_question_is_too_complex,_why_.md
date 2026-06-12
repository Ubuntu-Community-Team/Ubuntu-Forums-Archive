---
title: "What to say when the question is too complex, why has hda been made sda?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-08-26
Is there an explanation of how to fix the disk problems caused by the developers renaming devices in fstab as though they were/are scsi hardware?

For months now I've posted on and off trying various things, like renaming the fstab devices, adding a lne to grub ide=generic or some such and nothing and I repeat nothing has worked. viz:

[http://ubuntuforums.org/showthread.php?t=531261](http://ubuntuforums.org/showthread.php?t=531261)
[http://ubuntuforums.org/showthread.php?t=531390](http://ubuntuforums.org/showthread.php?t=531390)
[http://ubuntuforums.org/showthread.php?t=499282](http://ubuntuforums.org/showthread.php?t=499282)
[http://ubuntuforums.org/showthread.php?t=498948](http://ubuntuforums.org/showthread.php?t=498948)
[http://ubuntuforums.org/showthread.php?t=485337](http://ubuntuforums.org/showthread.php?t=485337)
[http://ubuntuforums.org/showthread.php?t=475086](http://ubuntuforums.org/showthread.php?t=475086)

( I hear you: "Enough Already! )

If I leave a cd-rom in my cd-rw it will work fine at boot or power-up. I can even switch cds and the drive is OK. The dvd player never works. But it is listed in Places/Computer/cd-rom/dvd and other parts of the OS.

Can anyone really address this issue? I mean besides reworking the kernel? Device names and model #s below.

---

### Post by kyphi on 2007-08-26
Checking out the Dell Dimension 4100, I noted that it comes with a 200W power supply.  The standard is 350W which is usually enough to run the peripherals that are in use today and that includes CD and DVD drives. (I use a 550W PSU)

It is possible that the machine does not have enough power available to run the CD player as well as the DVD.  That it will run the CD player at startup supports this theory.

Of course, if you have replaced the power supply and upgraded to a higher capacity unit then all the above does not apply.

You might also check your BIOS and if there is a choice for running your CD and DVD see if altering a specification there will effect a change.

---

### Post by cwrann on 2007-08-26
upon uploading ubuntu onto my computer all of my partitions were titled sda and not hda I never thought twice about it, should I try to change them to hda?

---

### Post by Mark_in_Hollywood on 2007-08-27
Don't change anything WHATSOEVER. I believe this is a bug and have found such at Launchpad. I haven't seen a solution at those bug reports so I didn't put them in this post. My best guess is to wait for gutsy gibbon. It may have some fixes.

As for the power supply stuff. I will unpower the cd-rom and re-boot and get back here to this post to report. Why does the drive light flash in the dvd player when a disk is inserted? If there weren't enough power, the motherboard or pci cards should be failing as well.

Can you show what research you did on the power supply issue? I can't find anything to corroborate this. Not at the forums, not on the net. At least not about hda being renamed sda and from my /etc/fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

which is the more likely problem, and not the lack of power to the peripherals.

---

### Post by kyphi on 2007-08-27
I was surprised, Mark_in_Hollywood, that you were unable to find any information regarding the power needs of computers.  Try Google - computer power needs.

Basically, power supplies have  two or more supply rails to meet the different voltage requirements of computer components.  The components that need power are -

1.  CPU
2.  Motherboard and its controllers
3.  Sound card
4.  Graphics adapter
5.  Ethernet card
6.  WiFi card
7.  RAM
8.  Optical drives
9.  Hard drives
10. Modem (internal)
11. Case cooling fan
12. Power supply cooling fan

When you add extra components or change some of them, you need more power.  Elementary, dear Watson.  Even the extra stick of RAM needs power.

As to the light flashing in your CD drive, that just shows that there is power to the unit and enough power to run a light emitting diode but does not signify that there is sufficient power to actually run the unit.

---

### Post by Mark_in_Hollywood on 2007-08-28
You are reading this far too literally. My searches are for:

"dvd player" failure or troubleshoot" "ubuntu fesity" "power supply" and variations on those as themes. Nobody is reporting such.

Next: have you any idea of why the drive can open/close while the computer is powered? If there is a lack of power, why is the computer selectively "removing" the dvd player? Why not ram, wireless card or a harddisk?

Meanwhile I checked out my power requirements:

[http://www.journeysystems.com/?powercalc](http://www.journeysystems.com/?powercalc) (click the Start the Calculator) and I'm well within spec with my measly 200 W Foxconn ps.

As for removing the power cable to the cd-rw and rebooting, I've decided against that as I can't know what the OS would think, when an installed peripheral didn't show up at boot. Would the OS write it out and cause me a OS reinstall. No way jose.

---

### Post by kinematic on 2007-08-28
The device renaming is **not** a bug. The kernel devs started using libata for IDE devices and as such everything is now recognized as a SCSI device. It has no negative effect on the performance (in most cases there is an increase) of your devices. The only bug is that the system is not updated automatically for everyone, some have no problems and others have to make the changes themselves to reflect the new naming scheme.

---

### Post by kyphi on 2007-08-28
Often there is more than one answer to a problem, Mark_in_Hollywood.

My suggestion re your power supply stated that it is a "possibility" that your supply is not up to the tasks required.  There may be other solutions.

---

### Post by MQMike on 2007-08-28
What Kinematic said.

Reasoning behind the UUIDs:
[https://wiki.ubuntu.com/LibAtaForAtaDisks](https://wiki.ubuntu.com/LibAtaForAtaDisks)

---

### Post by Mark_in_Hollywood on 2007-08-31
Thank all. That's very good, but please remember or re-read this thread. The purpose of this post is to find a solution to my cd-rw having to have media in at at boot time, or it doesn't mount. And the DVD player doesn't mount no matter what.

It's all very well and good to migrate the storage devices to all being denominated as SCSI, but how do I get my optical drives to work?

---

### Post by TeaSwigger on 2007-08-31
Hello,

I also have a Dimension 4100 like yours. It has two DVD-RW drives and both work perfectly, even if used at the same time.

Unfortunately I haven't been into this for long so I don't know much yet either. I did have plenty of problems with the opticals on my other Dell, a 2350, and I was installing right at the time the hd/sd changeover happened. They're working now. I'm trying to think of all I did, but it's such a blur now. I must've tried a hundred things. Sounds like you've been having a long round of problems too. But hey if the drives are working ok you'll get it. Let me look at the fstab, stare at a few things and maybe I can jar up the memory cells. Be back.

---

### Post by TeaSwigger on 2007-08-31
Remember people aren't getting paid here, so don't get bugged if nobody fixes stuff for you. ;) Having lectured, back to the prob...

The fstab in my 4100 is the same as you listed and works fine. For some reason, the fstab in my 2350 lists them like this

```
/dev/sr0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sr1 /media/cdrom1 udf,iso9660 user,noauto 0 0
```

not scd. Using /dev/scd0 didn't work unless I had something in the drive when I booted. Nope I have no idea why or if that matters whatsoever. I also discovered that I can refer to the cdrw as /dev/cdr or /dev/cdrw and the dvdrw as /dev/dvd or /dev/dvdrw in any program and that will also work for the respective drive. All this does make me wonder if maybe it's not associated to /dev/scd0. Maybe looking in the /dev directory will show you which ones are directed somewhere by which show as links? Only a stray uninformed thought understand.

Other changes I made around this time that I do remember:

-Changed 40 pin IDE ribbon for 80 pin.
-Changed drives from both being CS to Master / Slave.
-Reset CMOS by the jumper pin on the motherboard.
-Replaced symlinks in /media: this effectively mapped /media/cdrom0 to /dev/sr0 and /media/cdrom1 to /dev/sr1. Only one, /media/cdrom was there before, and that was mapped to /dev/scd0 which as related above wouldn't be true unless something was in the drive at boot.
-Replaced 2nd drive - a generic DVD-RW that wasn't being detected - with an old CD-RW which was detected and did work.

Anyway it's all working fine now. Hope you can get yours working soon too. Good luck.

---

