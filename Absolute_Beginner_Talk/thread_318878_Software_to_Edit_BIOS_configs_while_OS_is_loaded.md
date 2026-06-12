---
title: "Software to Edit BIOS configs while OS is loaded"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by habtish on 2006-12-14
I have a broken [PS/2]("http://en.wikipedia.org/wiki/PS/2_connector") port (Thought it was the connector at first.. but changing the connector didn't work) and found out that my BIOS is not configured for Legacy USB Support and I can not enable this now because my Keyboard is not detected by the BIOS. This sadly means that I can not dual boot and have to watch Grub go to the default OS and boot it.
Any software you guys would recommend that would enable me to mess with the BIOS configuration while my OS is running?

Appreciate all suggestions/comments

---

### Post by Ocxic on 2006-12-14
to my knowledge this is not possible.
sorry to say but i don't have a way to help you here, this may be a rare occasion where you just can't do anything.

the only advice i could give you would be to try reseting your bios, this requires you to locate a jumper on your motherboard. that will reset the bios to factory settings and hopefully it will enable you usb keyboard support, but it's a long shot.

---

### Post by gumbald on 2006-12-14
Ouch, all I can say is try a BIOS reset. How old is the motherboard, can you RMA it?

---

### Post by habtish on 2006-12-15
This is very depressing :(

---

### Post by Sef on 2006-12-15
Have you tried to update your BIOS?

---

### Post by habtish on 2006-12-15
> **Sef said:**
> Have you tried to update your BIOS?
I have a Dell ... Would the "update" come Dell?

Sorry if this Q is too elementary..

---

### Post by Ocxic on 2006-12-16
yes you would either get the update from dell, or from the manufacture of the motherboard itself would be even better.

it is not requird for the update to be "dell" as you say they only say dell needs dell parts cause they want to make more money, with computers everything works together mostly.

---

### Post by habtish on 2006-12-16
I got the BIOS Update from [Dell]("http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R84098&SystemID=DIM_PNT_CEL_2400C&os=BIOSA&osl=en&deviceid=308&devlib=0&typecnt=1&vercnt=8&formatcnt=1&libid=1&fileid=110558#3DOS"), Problem is .. it is an .exe that needs to be added to an MS-DOS bootable disk. I have been reading up on HowTos on making these bootable disks and most of them of course assume you are running Windows at the time you are trying to make the bootable disk. How can I load this update exe and make a bootable file from Linux?

---

