---
title: "Upgrading Xubuntu 6.06"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-11-06
I've tried to do a new install with Xubuntu 7.10 using a live CD and although I'm able to get to the desktop, when I select install, it fails by switching off my laptop (Samsung V25).

Having failed, I've reinstalled Xubuntu 6.06 without trouble and  I'm wondering if it is possible to upgrade to the latest version of Xubuntu and if so, how would I do this.

---

### Post by overdrank on 2007-11-06
> **a.v.l said:**
> I've tried to do a new install with Xubuntu 7.10 using a live CD and although I'm able to get to the desktop, when I select install, it fails by switching off my laptop (Samsung V25).

Having failed, I've reinstalled Xubuntu 6.06 without trouble and  I'm wondering if it is possible to upgrade to the latest version of Xubuntu and if so, how would I do this.

HI you could update through update manager under system, administration. But you will have to go to edgy, then feisty and so on. So you could try and do a clean install of feisty and then try from there. There is also the alternate cd of Gutsy to try and install. Could you give us some specs on your system and maybe we can solve why the live cd fails and also did you check the cd for errors?

---

### Post by a.v.l on 2007-11-06
> **overdrank said:**
> HI you could update through update manager under system, administration. But you will have to go to edgy, then feisty and so on. So you could try and do a clean install of feisty and then try from there. There is also the alternate cd of Gutsy to try and install. Could you give us some specs on your system and maybe we can solve why the live cd fails and also did you check the cd for errors?


Thanks, I tried doing an upgrade using update manager as you suggest but when I try the laptop screen simply goes blank and the computer turns off. I've also tried installing using the alternatove Xubuntu 10.1CD and the same happens. I have the same problem more or less with all other versions of Ubuntu I try to install, even though I can use the live CD and get as far as the desktop..

The laptop spec are:

Samsung V25
Pentium 4
512meg of RAM
30Gig Hard drive.

I have a suspicion that its possibly down to the graphics card which seems to be struggling a little. text flickers a little during install. I'm not sure if this card can be changed or even how to find the spec of the  card.  Any advice would be welcomed as I've been trying to get Linux to work on this machine for almost a year now. Xubuntu 6.06 works but not the wireless card, hense my reason for upgrading to Xubuntu 7.10.

---

### Post by overdrank on 2007-11-06
> **a.v.l said:**
> Thanks, I tried doing an upgrade using update manager as you suggest but when I try the laptop screen simply goes blank and the computer turns off. I've also tried installing using the alternatove Xubuntu 10.1CD and the same happens. I have the same problem more or less with all other versions of Ubuntu I try to install, even though I can use the live CD and get as far as the desktop..

The laptop spec are:

Samsung V25
Pentium 4
512meg of RAM
30Gig Hard drive.

I have a suspicion that its possibly down to the graphics card which seems to be struggling a little. text flickers a little during install. I'm not sure if this card can be changed or even how to find the spec of the  card.  Any advice would be welcomed as I've been trying to get Linux to work on this machine for almost a year now. Xubuntu 6.06 works but not the wireless card, hense my reason for upgrading to Xubuntu 7.10.

HI and it appears that system has a intel chipset for graphics and that should not be an issue. You may check the power management in your bios to see if it shutting down the system. I would also suggest checking the cd for errors and also do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by a.v.l on 2007-11-06
> **overdrank said:**
> HI and it appears that system has a intel chipset for graphics and that should not be an issue. You may check the power management in your bios to see if it shutting down the system. I would also suggest checking the cd for errors and also do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Much appreciate your help, I'll do some checking when I get home from work this evening.

---

### Post by a.v.l on 2007-11-10
> **overdrank said:**
> HI and it appears that system has a intel chipset for graphics and that should not be an issue. You may check the power management in your bios to see if it shutting down the system. I would also suggest checking the cd for errors and also do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Having  decided to install Xubuntu 7.10 because It gives me my best results so far.  I  must be somewhere near installing it  using the  alternative CD.

First I checked the installation CD for faults no none were reported.

I reformatted the laptop hard drive and then reinstalled XP which is working ok.
Next I installed Xubuntu  from the 7.10 alternative CD and on completion restarted the laptop.

On starting I was taken to GRUB and given the option of Xubuntu or Microsoft XP

Selecting Xubuntu I get the spalsh screen and after a minute or so I get various colours from the screen and infact I once was able to go as far as the user and password screen but stayed there for no longer than a half second before the screen went blank. Waiting 5 minutes does nothing. I end up with a blank screen. and repeating the process does the same thing each time.

My BIOS (Phoenix) doesn't have anywhere to checkthe power management or to alter the graphics card as far as I can tell.

Will I ever get this to work?

By the way I can install Xubuntu 6.06 but nothing higher, not even Ubuntu 6.06 will install.

I've added some images of the boot up process in the hope it helps.

---

