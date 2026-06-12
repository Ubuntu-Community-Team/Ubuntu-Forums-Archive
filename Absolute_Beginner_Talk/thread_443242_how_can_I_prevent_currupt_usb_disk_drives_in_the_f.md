---
title: "how can I prevent currupt usb disk drives in the future?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by civilmonkey on 2007-05-14
I have a iAudio U3 mp3 player which acts as a plug and plug usb disk drive.  It was working great and I regularly used it in Win XP and Ubuntu 6.10.

One day I deleted the files in the trash folder from Linux to free up space.  When I tried to properly remove the device by right clicking and hitting eject a dialog popped up indicating that Ubuntu was copying files over before I could unplug the device.  I hadn't actually copied files over but I waited quite a while (5 minutes). 

Silly me, I finally gave up and unplugged the device.  The device became read only. I tried resetting, setting permissions, and finally reformatting in FAT32.  The re-formatting killed the device (became unreconizable in WinXP or Ubuntu).  I was unable to re-load firmware.  Tech support gave me an RMA and the device has been sent in for repair to the manufacturer. 

My question is does this happen often?  If I had waited longer, would Ubuntu have finished writting files so I could safely remove the device (I got the feeling it wouldn't have).  I'll be scared to use my mp3 player with Linux when I get it back (despite the fact iAudio advertises Linux compatible).

---

### Post by doobit on 2007-05-14
I have never had a corrupted USB drive and I use them a lot, so it doesn't happen often, at least in my experience. Also, normally you need to format a USB drive as FAT16, not FAT32.

---

### Post by lazyart on 2007-05-14
Naah... FAT32 is fine for USB drives.

---

### Post by tgalati4 on 2007-05-14
If there were several gigs of files in the .Trash, then it's possible that write/erase operation had not finished.  Some USB controllers are slow and it could take several minutes to finish certain operations.  Pulling the drive before it finishes will render the file system as "dirty".

Doing a simple file system check (sudo fsck /dev/sda1) will normally bring it back to "clean".

---

### Post by icecruncher on 2007-05-14
dunno, windows likes to corrupt my usb drive, but haven't had any problems with ubuntu. 
:rolleyes:

---

### Post by Josh1 on 2007-05-14
Make sure you safely eject your USB Stick at all times, do not have something open that is reading from it.. I have never had a corrupt usb disk with this method.

---

### Post by civilmonkey on 2007-05-14
[quote=doobit]
Also, normally you need to format a USB drive as FAT16
[/quote]

That's was I thought too, but I checked the device first and it was FAT32 originally.

[quote=tglati4]
Doing a simple file system check (sudo fsck /dev/sda1) will normally bring it back to "clean".
[/quote]

That is something I definitely should have tried!  Thanks for the tip.  Learning Ubuntu bit by bit....

---

### Post by icecruncher on 2007-05-14
> **tgalati4 said:**
> 

Doing a simple file system check (sudo fsck /dev/sda1) will normally bring it back to "clean".

you mean all the way?  cool thanks

---

### Post by Wim Sturkenboom on 2007-05-14
I had a 2 GB flash disk that died (and it died in Win2000, not Linux); can still read it but no longer write. A 1 GB bought at the same time is still alive as well as a 256 MB that's about 5 years old.
Just bad luck.

You might know that flash devices have a limited number of write cycles (100,000 .. 1,000,000) per bit. Every time you eject the flashdisk, the FAT gets rewritten (adding, deleting). And that's always the same area that gets rewritten.
It's also possible that the FAT gets rewritten after every write/delete which significantly reduces the lifespan; this had something to do with mounting with some option (sync?)); I don't think that that's the case in Ubuntu, but I'm not sure.

You probably have had bad luck (just like me); any electronics usually dies either in the beginning or at the end of its life (and hardly ever somewhere in between).

---

