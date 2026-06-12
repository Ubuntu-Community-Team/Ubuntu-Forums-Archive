---
title: "CD keeps ejecting"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by telegramsam on 2006-08-13
I've been trying to rip some CD's into my comp for a while, and the CD keeps ejecting about halfway through the first track.  I was using Sound Juicer to begin with, and then downloaded KAudioCreator and shut down the auto-run for Sound Juicer.  The disc ejects with either program...Any ideas?  I've been through every system setting to see if there is an automatic disc eject, and I can't find anything...

---

### Post by GuitarHero on 2006-08-13
Try K3B, its the best.  It sounds like a settings problem if it is program independant.

---

### Post by telegramsam on 2006-08-14
Any idea how or where I might change that setting?  This is driving me crazy.  Data CD's don't eject, just factory audio CD's.  I've been throught all of the system settings, and I can find nothing about automatically ejecting CD's.  I've installed w32codecs, but I don't think that should have anything to do with CD audio...?

](*,)

---

### Post by jimmynoboat on 2006-09-07
I get the exact same problem - did you fix it Telegramsam?
The CD I tried was Abba so, I wasn't all that shocked whe the PC rejected it but it also rejects Queen so it must be a fault

---

### Post by whizbaby on 2006-09-07
I cannot resolve, only add problems:
I installed ubuntu at a friend's yesterday, everything went fine (as usually). But when I rebooted the computer and logged in it started to *eject and then withdraw* the *installation cd* for about **twenty times**. Same with other cd's... (only thing I like in it is the rythm it produces)

---

### Post by KCMiller3 on 2006-10-02
I am having the same problem.  It constantly ejects all audio CDs after about 30 seconds.  Any fix?

---

### Post by youngsaint on 2008-03-21
I have the same problem. I have heard about others who have the problem, and I believe its the cd drive we are using that is slightly off.  anyways, even though this is old, you can get around the problem by using command line tools.  (cdrecord, wodim....) good luck

---

### Post by youngsaint on 2008-03-21
> I think I may have found the source of the mystical weirdness that is magically ejecting drives on (but not limited to) PS3

It would appear that the whole gnome-volume-manager bug thing is a red herring. Getting to the root of the problem shows that hald is getting upset with some (particularly Mitsumi) drives - in an ironic "I'm afraid I can't do that Dave" stylie.

There are some ways around this removing/disabling hald or only allowing root to mount disks by setting cdrom as nouser in fstab - however all these options don't make for an easy-to-use system. It might give me what I need for running remastersys though.

guess what?  I have a Mitsumi drive.

```
young@ubuntu:~$ wodim -checkdrive
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'MITSUMI '
Identification : 'CR-4804TE       '
Revision       : '2.6C'
Device seems to be: Philips CDD-522.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET RAW/R16 RAW/R96R
```

---

