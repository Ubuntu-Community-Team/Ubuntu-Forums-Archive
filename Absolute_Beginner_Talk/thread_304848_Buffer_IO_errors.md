---
title: "Buffer I/O errors"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by euthyfro on 2006-11-22
I'm trying to install ubuntu 6.10 on the brand new computer i got yesterday.  It doesn't have any pre-installed operating system and when i select start/install ubuntu it begins but a few minutes in i get a screen telling me "buffer I/O error on device hda, logical block 25630" followed quickly by more of the same error but with different #s at the end.  Is there something i need to change in BIOS?  Have i done something i shouldn't have?  I'm not extremely knowledgeable in regards to computing but i don't wanna use windows anymore.

---

### Post by justin whitaker on 2006-11-22
> **euthyfro said:**
> I'm trying to install ubuntu 6.10 on the brand new computer i got yesterday.  It doesn't have any pre-installed operating system and when i select start/install ubuntu it begins but a few minutes in i get a screen telling me "buffer I/O error on device hda, logical block 25630" followed quickly by more of the same error but with different #s at the end.  Is there something i need to change in BIOS?  Have i done something i shouldn't have?  I'm not extremely knowledgeable in regards to computing but i don't wanna use windows anymore.

Could be either a bad CD, or a bad HD. The last time I used the Edgy disc, I got 3 lines of the Buffer I/O error, and then the installer started. Very odd.

---

### Post by CatKiller on 2006-11-22
**hda** would be the Master device on the Primary IDE channel. Normally, that would be a hard drive.

If it is your hard drive, it could be failing. Run the manufacturer's diagnostic software on it, since you don't want to trust your data to it if it won't be safe.

If it's a cdrom it might only need a clean :)

---

### Post by eXisor on 2006-11-22
I take it the start/install Ubuntu is on the first screen you see when you boot from the cd?

If that's the case, then the problem is your cd (the physical hd is only accessed later once you install from within the livecd Ubuntu environment). Either it didn't burn properly, or it got dirty. Check the cd for defects, clean it, and try burn it again at the lowest possible burn speed.

---

### Post by euthyfro on 2006-11-22
well, i checked the cd on this machine, & it looks like it's all right, like i said i don't have an operating system on the new computer so i'm not sure how i can run a diagnostic on the hard drive to see if it's the problem, i don't have any documentation for it.

---

### Post by euthyfro on 2006-11-22
but i'm burning a new ubuntu disc just 2 b on the safe side, wish me luck!

---

### Post by CatKiller on 2006-11-22
> **euthyfro said:**
> well, i checked the cd on this machine, & it looks like it's all right, like i said i don't have an operating system on the new computer so i'm not sure how i can run a diagnostic on the hard drive to see if it's the problem, i don't have any documentation for it.

You generally download it from the manufacturer's website, and run it from a boot floppy.

> **euthyfro said:**
> but i'm burning a new ubuntu disc just 2 b on the safe side, wish me luck!

Good luck!

EDIT: Oh, and another thing you could check is the cable/jumper settings. If you've not successfully booted the machine before, it's possible that they are set incorrectly.

---

### Post by euthyfro on 2006-11-22
so the new disc got me thru the ubuntu install, but left me with a black screen criss/crossed with orange diagonal lines & no way 2 interact with the system.  guess i'm running into every problem in succession.  i assume it's because i haven't installed the video drivers yet, but how can i do that without an operating system?](*,)

---

### Post by euthyfro on 2006-11-22
so as to illicit the best advice: the machine i'm trying to run ubuntu 6.10 on is an: evga nforce4 sli mainboard, amd 4200 processor, 1 gig ram, geforce 7300le video card, it was put together by cyberpower inc & it's in a kik-*** black x-cruiser cases.  so that's more info than any1 could ever need, let the help come.

---

### Post by CatKiller on 2006-11-22
I think there were some recent posts of display problems with the Edgy live cd for people with newer nVidia cards. You could have a prowl through those to see if there were any solutions forthcoming.

---

