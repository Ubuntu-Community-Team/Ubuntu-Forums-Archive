---
title: "Trouble booting live CD with HP DV6000"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Spirit_of_68 on 2007-08-24
I am a total noob, I am trying to get the live cd to run on a HP DV6000 AMD Turion with no success. 

I have followed the instructions and added noapic irqpoll noirqdebug but it still fails and comes up with the message about the X window system

Am I typing it in correctly? 

Code: noapic irqpoll noirqdebug

Any help would be much appreciated.

Thanks

---

### Post by overdrank on 2007-08-24
> **Spirit_of_68 said:**
> I am a total noob, I am trying to get the live cd to run on a HP DV6000 AMD Turion with no success. 

I have followed the instructions and added noapic irqpoll noirqdebug but it still fails and comes up with the message about the X window system

Am I typing it in correctly? 

Code: noapic irqpoll noirqdebug

Any help would be much appreciated.

Thanks

HI and sorry to hear you are having trouble I to am having similar trouble so I thought I would bump the thread
I can not install via live cd or alternate with a Geforce 6100. I get all kinds of errors and spawning to fast stopped. :confused:

---

### Post by ramjet_1953 on 2007-08-24
I few questions first.

1. When you burnt the iso, I assume that you burnt it as an iso9660 image, not as an ordinary data CD?

2. What speed did you burn the image at? Any faster than 4 X will usually cause error problems with any iso.

3. After burning the image, did you check the disk for integrity, with the MD5 checksum?

Regards,
Roger :cool:

---

### Post by kornface13 on 2007-08-25
> **ramjet_1953 said:**
> I few questions first.

1. When you burnt the iso, I assume that you burnt it as an iso9660 image, not as an ordinary data CD?

2. What speed did you burn the image at? Any faster than 4 X will usually cause error problems with any iso.

3. After burning the image, did you check the disk for integrity, with the MD5 checksum?

Regards,
Roger :cool:

yea you should definately check into this.  i also have a dv6000 and my live CD worked perfect

---

### Post by overdrank on 2007-08-25
HI I know this may not help you but I finally install by installing via another system. Then when I moved the drive back to the system I had to edit the the kernel with vga=771 and then the system booted so I could reconfigure the xorg. Thanks to all for the help in the forum. :guitar:

---

