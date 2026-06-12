---
title: "Computer will not boot from CD-ROM"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by barton.jones on 2006-11-23
I'm trying to install 6.10 on my other computer (I know the CD works), but the screen goes black for a while than boots Windows (which I can't get the password for ](*,) ) ... it is setup to boot them the CD-ROM

---

### Post by jonesyp on 2006-11-23
Hi, the only way to do it is to take the case off the PC, remove the battery overnight that put it back in the morning.  This gives time for capacitors to discharge.  This will then reset the bios.  Hope that helps.

---

### Post by jd65pl on 2006-11-23
Are you sure that the boot order is correct? Are you saying you are unable to access the bios settings?

---

### Post by jd65pl on 2006-11-23
I think you should look at using some kind of boot floopy before flashing the BIOS check out the link below I am sure there are other products around.

[http://sourceforge.net/projects/btmgr/](http://sourceforge.net/projects/btmgr/)

---

### Post by barton.jones on 2006-11-23
yes, the boot order is correct, booting from CD-ROM first ... I can access the bios settings

---

### Post by jd65pl on 2006-11-23
> **barton.jones said:**
> yes, the boot order is correct, booting from CD-ROM first ... I can access the bios settings

I had this happen on a PC before and no matter what distro I tried it did the same as you have experienced (it was a packard bell I think!) definitely try the boot floppy to boot ubuntu using the CD. You could also try downloading [DSL]("http://www.damnsmalllinux.org/") and using their[ purpose built boot floppy.]("http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies")

---

### Post by barton.jones on 2006-11-23
problem #2 than, don't have a floppy drive or any floppy discs for that matter

---

### Post by r4ik on 2006-11-23
> **barton.jones said:**
> I'm trying to install 6.10 on my other computer (I know the CD works), but the screen goes black for a while than boots Windows (which I can't get the password for ](*,) ) ... it is setup to boot them the CD-ROM

You could try change drives.

Good luck !

---

### Post by PurplePenguin on 2006-11-23
I just had a similar problem on a laptop with a different distro's live cd.  I had used the same disc a dozen times and it worked perfectly, then the next time I tried using it, it wouldn't boot from the disc.  It just booted straight into windows (which is full of problems, that's why I'm using a live disc).  I had to reburn the CD, and it worked perfectly again.  I'm assuming that there was a tiny scratch on a very important part of the disc or something. :)

---

### Post by Edgy Eft Fan on 2006-11-23
hi, im new to this game also. i had a problem like yours, i changed over the master and slave jumpers on the cd drive and hard drive. that did the trick

---

### Post by barton.jones on 2006-11-23
how do you change over the master and slave jumpers ??

---

### Post by bigken on 2006-11-23
there on the back of the drive they are normally marked cs/sl/ms

---

### Post by barton.jones on 2006-11-23
not very easy to get to on a labtop though

---

### Post by bigken on 2006-11-23
I dont think there are any jumper on laptop cdroms

---

### Post by I_have_seen_the_light on 2006-11-23
Dont know if this would help but fisrt try to see if the system  is set to boot using the CD-rom. if it is, try to see if your CD rom is working might be faulty.  Last resort Discharge the board.  take off the case look at you board near the battery and look for 3 pronged jupers (usually labeled Jp1 or Jp11) move the jumoer to the other prong and still touching the middle one then after about 3 seconds put it back in its original position. then off you go.

---

### Post by barton.jones on 2006-11-23
I still need help on this

---

### Post by withaar on 2006-12-07
I am having the same problem now, on a laptop. I also think it may be the cd that is scratched, so first thing I will try is burn a new disc. After that, I have a DSL cdrom somewhere, I'll try that. Finally, I will try booting from a USB device if all else fails.

Of note perhaps: in the bios the first boot option (cd/dvd device) disappears with my current boot cd, indicating that the bios did not like the cd.

I'll let you know how it goes.

---

### Post by louieb on 2006-12-07
Here is a page that gives a few simple things to try.
[PuppyLinuxWiki : BootingFromCD]("http://puppylinux.org/wikka/BootingFromCD")

---

### Post by CaveRat on 2006-12-07
Here is another suggestion direct from the Ubuntu 6.06 Disk. You will find the file in the Install Directory/Folder on the CD. If you can access the cd from a friends machine that has a floppy drive, this could get you going.

About the Smart Boot Manager image
----------------------------------

  The file `sbm.bin' that is available in this directory may be useful
  to you if you are not able to directly boot the first CD because your
  BIOS may be too old and may not support ISOLINUX.

  Then, instead of booting on the CD directly, you create a Smart Boot
  Manager floppy image by using the sbm.bin disk image. You can create this
  floppy with rawrite (under DOS) or with dd (under Linux). Now you can
  boot on this floppy disk and it will detect your CDROM and let you boot
  on it bypassing any BIOS limitation.

What is SBM ?

  Smart Boot Manager or briefly SmartBtmgr (SBM), is an OS independent
  Boot Manager - a program that is loaded by the bios before any
  operating system and allows you to choose which operating system to
  boot.

  SBM is included in Debian in two ways, the package bmconf allows us to
  install and configure an old version of SBM and sbm wich is the latest
  version of SBM with an installer.

What's the use of SBM on the CD then ?

  SBM includes an IDE driver that allows us to boot the cds even on
  machines with a BIOS that wouldn't support booting from CD, provided our
  CDROM is an IDE one, that is, so you can make a SBM floppy and boot from
  it and then tell it to boot from your CDROM.

  Also, there are some cases where the BIOS would allow booting from the CD
  but isolinux fails to boot from there, in this case you can either boot
  using a CD other than the first, as the others don't use isolinux, or you
  can make a SBM floppy and boot from this floppy and then tell SBM to boot
  your CDROM.

How do you make a SBM floppy ?

  If you have SBM installed on a box you can run sbminst. Otherwise you can
  put the sbm.bin floppy image that we provide with our cds onto a floppy
  just like you would do with a rescue image.

---

### Post by jd65pl on 2006-12-08
> **CaveRat said:**
> Here is another suggestion direct from the Ubuntu 6.06 Disk. You will find the file in the Install Directory/Folder on the CD. If you can access the cd from a friends machine that has a floppy drive, this could get you going.

Already suggested no floppy drive available.

---

### Post by ThornInc on 2006-12-08
I'm having this same problem with my Gateway Solo 9300.  Does anyone else have a Solo with Ubuntu on it?  Maybe they can help me.

I've tried changing the jumpers in BIOS so that the CD-ROM is the primary master, but when I try to boot up I just get a message that says, "Operating System not found"

This is driving me nuts!

Please help me      :(

---

### Post by ThornInc on 2006-12-08
nevermind...now it's working for some mysterious reason...

---

### Post by smile_sunshine on 2006-12-08
barton.jones  = do you have any other bootable cds you can try on your computer (eg windows etc)?  (if these do boot you would know its the cd rather than the cdrom drive /bios / etc thats the problem).

Have you tried the alternate install cd instead? (particularly if your computer has low ram etc)

what is the computer - are you using the cd for the right type of computer?  (most likely the PC (Intel x86) one??)

---

### Post by withaar on 2006-12-10
I had the same problem and I got the cd install to work. I did 2 things:

1 - Burned a new cd
2 - Set the region code in the cd/dvd drive

I had not yet set the region code in the drive, which may be why it balked. I am typing on it now, beautiful. :)

---

