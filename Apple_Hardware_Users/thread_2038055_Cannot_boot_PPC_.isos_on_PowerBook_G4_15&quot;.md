---
title: "Cannot boot PPC .isos on PowerBook G4 15&quot;"
date: 2012-08-05
forum: Apple Hardware Users
---

### Post by Elliot.strumlauf on 2012-08-05
I tried to google/forum as much as possible, couldn't find a fix.

I am unable to boot from any PPC iso, from 10.10 to 12.04. I burned the image on two different computers, slow speeds, checked md5, etc etc. In all scenarios, holding 'c' at boot eventually boots into 10.5.8, and 'alt' at boot does indeed show a linuxCD, but selecting it circles back into the startup disk chooser (albeit in awful 8-bit graphics). 

As we cannot boot from USB, does anybody know how I can boot/install Ubuntu on my PowerBook G4 15"?

Thanks!

---

### Post by gwjvan on 2012-08-05
How far does it get into loading the CD? Does it give any text feedback?

Also, have you tried dd'ing a CD image to a usb flash drive and holding command+option+o+f at startup then telling the computer to boot from the usb (with a command similiar to "boot usb0/disk@1:2,\\yaboot"?

---

### Post by Elliot.strumlauf on 2012-08-06
I do not even get to the point where the DVD would fail; it simply doesn't get past the startup disk chooser when I hit alt. 

I did not try the USB method. Does that work with LiLi/'Startup Creator'? Or do I have to try a specific method?

Thanks.

---

### Post by rsavage on 2012-08-06
The openfirmware path to the cd drive is hardcoded into the *ubuntu cd's boot files.  If you are using an external drive then this will cause problems (what you describe).  If your pram is corrupted this will similarly cause problems.

[https://wiki.ubuntu.com/PowerPCFAQ#The_CD_won.27t_boot](https://wiki.ubuntu.com/PowerPCFAQ#The_CD_won.27t_boot)

[https://wiki.ubuntu.com/PowerPCFAQ#Ho_do_I_reset_the_PRAM.2BAC8-PMU.3F](https://wiki.ubuntu.com/PowerPCFAQ#Ho_do_I_reset_the_PRAM.2BAC8-PMU.3F)

---

### Post by Elliot.strumlauf on 2012-08-06
Well, I reset my PRAM and tried booting via Open Firmware. When I got the OF prompt, I tried:
boot cd:,\install\yaboot     <<no luck
boot cd:,\\:tbxi             <<no luck

In both instances I got "can't open {my command}"

Any other ideas..??

---

### Post by rsavage on 2012-08-07
The only other thing I can think of (apart from faulty drive) is that your dvd drive has some other alias apart from 'cd'.  I am not an expert on booting cds though.  I always use a USB flash drive (see FAQ).

---

