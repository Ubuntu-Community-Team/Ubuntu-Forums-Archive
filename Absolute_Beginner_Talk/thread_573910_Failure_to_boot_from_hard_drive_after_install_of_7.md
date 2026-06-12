---
title: "Failure to boot from hard drive after install of 7.04"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Just Some Person on 2007-10-12
This is a repost with a better description of the problem in the heading (I can't edit the old post).  

I recently got an old pc to try out ubuntu. its specifications are:

400MHZ intel celeron
468M ram
toshiba 13.7GB hard disk

This PC had ubuntu 6.10 installed, and it ran this with no problems, but after installing 7.04, the PC no longer boots from the hard drive, but it does run OK from the CD that I burnt from the download:

The install appeared to work fine, however when I try to boot it from the hard disk the loading bar freezes at about five percent; then after a while the loading screen disappears and i get this message:

*Reading files needed to boot...
[469.073555] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[469.073696] ata1.00: cmd c8/00:00:0a:c6:e9/00:00:00:00/e0 tag 0 cdb 0x0 da
ta (either 13072 or 90112)in

it then repeats that message about a dozen times before the screen goes black and nothing happens (though the HDD light is on)

It boots fine from the disk.

Please help!!!

---

### Post by battyice on 2007-10-12
Considering the age of that pc, I would trying installing 7.04 with the alternate CD.

---

### Post by Just Some Person on 2007-10-12
Thanks for the reply.  

I have avoided going down that route, as being a newbie to ubuntu, I am afraid that I would be getting a lot of options in the alt-CD that I wouldn't understand, with the very likey possibity that i would get lost in the number of options etc- also, working from the premise that the  thing was working with ver 6.10 I assumed that the hardware should be able to handle the upgraded version 7.04

---

### Post by rklauco on 2007-10-12
> **Just Some Person said:**
> Thanks for the reply.  

I have avoided going down that route, as being a newbie to ubuntu, I am afraid that I would be getting a lot of options in the alt-CD that I wouldn't understand, with the very likey possibity that i would get lost in the number of options etc- also, working from the premise that the  thing was working with ver 6.10 I assumed that the hardware should be able to handle the upgraded version 7.04
Don't be scared - that's not that complicated.
It has few more questions and the main disadvantage is that it does not looks that good and you can't browse the net while installing ;-)

---

### Post by rklauco on 2007-10-12
Anyhow, isn't an update a way to go?
It takes a time, but it worked for me on very old Toshiba laptop with no CD, so there was no other way.

---

### Post by Just Some Person on 2007-10-12
Thanks for that - I'll try it, and keep you posted,

Cheers

---

### Post by Just Some Person on 2007-10-12
It works now! there must have been some problem with the hard drive: I replaced it with another one, installed ubuntu and it works perfectly! Yay!

---

