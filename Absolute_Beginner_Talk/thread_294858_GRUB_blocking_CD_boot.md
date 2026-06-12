---
title: "GRUB blocking CD boot?"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by ko63ap on 2006-11-07
I have set up my Dell Inspiron 2500 as a dual-boot machine:
BIOS: Pheonix Technologies LTD A11, 03.12.2001
CD Drive: SAMSUNG CDRW/DVD SN-308B
     GRUB 0.95
          Ubuntu 5.10
          Window$ XP Pro, SP2

It seems there was a problem with the disc I used to load Ubuntu 5.10 and certain files were missing.  A friend suggested reloading from a new disc.

Since then I've picked up a copy of Ubuntu 6.06.  I've tried this disc in another laptop - the machine booted from the disc and everything seemed to work as it should.

I then put said disc into my Dell and rebooted (first having checked to make sure in BIOS that the first option was to boot from CD/DVD drive).  Machine powered up, disc started spinning, then GRUB comes up. ](*,) 

Within Windoze I can see the files on the Ubuntu disc, the same from within Ubuntu 5.10.

I'm not concerned with running Ubuntu live off the disc - all I wish to do is install it over the existing version without having to wipe the entire hard disc and starting from scratch.

What is the best plan of attack? :-k

---

### Post by Bachstelze on 2006-11-07
Does the CD boot all right on another computer ?

---

### Post by ko63ap on 2006-11-07
> **HymnToLife said:**
> Does the CD boot all right on another computer ?

Yes, it functioned as it should on my Acer TravelMate 611TXV (running Windoze only - no GRUB on it).

---

### Post by bsussman on 2006-11-07
It is not very likely that grub is 'blocking' a cd boot since your BIOS is running things and the HD grub cannot get control until the cd boot is abandoned and the hd (where grub resides) boot started.  Possible but I think it is a stretch.

I have had perfectly good bootable CDs fail in some of my CD drives for no apparent reason, changed the drive and had success.  Like all hardware these days, there is controlling firmware involved and the drive/CD combination just may not be a happy match.

---

### Post by ko63ap on 2006-11-07
I've just tried running Smart Boot Manager ([http://btmgr.sourceforge.net/about.html](http://btmgr.sourceforge.net/about.html)) from a floppy - and it didn't even see the CD drive. :-k 

Is there a way to do something with the 6.06 disc from within Ubuntu 5.10?  As I stated earlier, I can see all of the files on the disc once I have some OS up and running...

---

