---
title: "Installation issue on Powerbook G4 TI, Radeon 9000 M9"
date: 2006-11-08
forum: Apple PPC Users
---

### Post by rcas on 2006-11-08
Hi,

Just picked up a TI powerbook and have run into an issue with install as well as X setup.

powerbook TI (G4 - 1ghz, Radeon 9000 M9 (64MB), 15.2 LCD)

This is what I see using Ubuntu 6.10:

"live" - black screen
"live video=ofonly" = messed up colors, then black screen
"live video=radeon"
"live video=radeonfb" - screen is split in 2 (top / bottom) with
a narrow band at he bottom of both slpits that gets progressivly whiter.

Tried the ctrl-alt-backspace full screen grows white.

Ran into similar issue with YDL 4.1, used text install and then
tried various xorg.conf settings (mode, etc.) all with no luck.

Any help would be GREATLY appreciated.

Thanks,
Ray

---

### Post by ssam on 2006-11-08
hi

i am using the same powerbook, and have generally found it to work very well with ubuntu.

have you checked the CD is ok? you need to do a md5sum on the disk image. (if you are not sure what this means just ask). also some people recommend writing the cd at a low speed, i recommend buying good (branded) CD-Rs

you could try the ubuntu 6.06.1 (dapper) cd, and see if that works any better.

if that fails, try using the alternate install CD. its not as pretty to use, but the questions are basically the same.

---

### Post by rcas on 2006-11-08
CD checks out, using "check video=textonly"....

I will give the 6.06.1 a try.

---

### Post by rcas on 2006-11-09
Tried 6.06.1 no dice.
Tried 6.06.1 alternate, used the install video=ofonly
and got the installer up, colors were red....

Went through the whole install and did the reboot and
there was no screen.  Could not switch to another screen,
and when I tried the ctrl, alt, delete screen went white.

Still no dice getting X up....

---

### Post by dpny on 2006-11-09
> **rcas said:**
> Tried 6.06.1 no dice.
Tried 6.06.1 alternate, used the install video=ofonly
and got the installer up, colors were red....

Went through the whole install and did the reboot and
there was no screen.  Could not switch to another screen,
and when I tried the ctrl, alt, delete screen went white.

Still no dice getting X up....

See the thread on Dapper hates Pismo: looks like I'm running into a similar problem trying to install. 

BTW: what does 

> "live" - black screen
"live video=ofonly" = messed up colors, then black screen
"live video=radeon"
"live video=radeonfb" - screen is split in 2 (top / bottom) with
a narrow band at he bottom of both slpits that gets progressivly whiter.

mean. Can one change video preferences on boot/install?

---

### Post by rcas on 2006-11-09
Yes, once you get the yaboot prompt if you hit the <tab> key you should get a list of all the available options.  You can then add stuff to the commands like 'video=ofonly'.  Which is the only way I have been able to get any istalls to work with my powerbook.

---

### Post by dpny on 2006-11-09
> **rcas said:**
> Yes, once you get the yaboot prompt if you hit the <tab> key you should get a list of all the available options.  You can then add stuff to the commands like 'video=ofonly'.  Which is the only way I have been able to get any istalls to work with my powerbook.

Oh. I can't see a thing so far.

---

### Post by ssam on 2006-11-09
are there any firmware upgrades for that powerbook? have you tried resting the PRAM? maybe it would help

---

### Post by Zarephath on 2006-11-09
I tried everything I could although I have a dual G4 mirror drive PowerPC...same video issues you describe using edgy. I got it installed last night by installing the alternate cd which can be found below the regular download link(scroll down). Download and install this...then it will all be well with you. Good Luck!  :)

---

### Post by dpny on 2006-11-09
> **ssam said:**
> are there any firmware upgrades for that powerbook? have you tried resting the PRAM? maybe it would help

It's all up to date. I am heeding several people's suggestions and grabbing the alternate install.

---

