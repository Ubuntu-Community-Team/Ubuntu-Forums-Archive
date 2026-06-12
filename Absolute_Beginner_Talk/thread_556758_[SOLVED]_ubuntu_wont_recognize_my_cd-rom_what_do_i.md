---
title: "[SOLVED] ubuntu wont recognize my cd-rom what do i do"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by luckymoonboy1 on 2007-09-21
ok ubuntu wont recognize my cd drive and i know it works because its the one i used to install ubuntu. does any one know if there is some kind of driver i can get to make it work?:confused:

---

### Post by alienexplorers on 2007-09-21
Did you try mounting the CD.

---

### Post by Pumalite on 2007-09-21
Check /dev and see if you have a cdrom device.
In some BIOS>IDE Configuration>Set to 'Enhanced Support for PATA+SATA'
If you don't have that option: set CD-DVD to 2nd Master and 'Auto' in BIOS

---

### Post by Kilz on 2007-09-21
> **luckymoonboy1 said:**
> ok ubuntu wont recognize my cd drive and i know it works because its the one i used to install ubuntu. does any one know if there is some kind of driver i can get to make it work?:confused:

Would you happen to be installing 32bit ubuntu onto 64bit hardware? Because thats what happens to my comp when I try that.

---

### Post by Pumalite on 2007-09-21
Do you have a laptop?. If so, what kind of laptop?.

---

### Post by luckymoonboy1 on 2007-09-21
ok i don't know what mounting the drive is. um and thanks every one else for the're tips i will try them. and i no longer have a laptop there was an incedint a few months ago that left it resting in pieces. and also i made sure that it is a 32bit and not a 64bit.

---

### Post by luckymoonboy1 on 2007-09-22
> **Pumalite said:**
> Check /dev and see if you have a cdrom device.
In some BIOS>IDE Configuration>Set to 'Enhanced Support for PATA+SATA'
If you don't have that option: set CD-DVD to 2nd Master and 'Auto' in BIOS

ok  i tryed these things but it still wont work. oh and i figured out how to mount the drive but when i try i says error something then when i click details it says  mount: special device /dev/scdO  does not exist any other sugestions? they would be very helpful. thanks.

---

### Post by alienexplorers on 2007-09-22
Can you please print out your fstab file.

> cat /etc/fstab

also put a cd in the drive and print out the results of 

> sudo fdisk -l

---

### Post by Kilz on 2007-09-22
> **luckymoonboy1 said:**
> ok i don't know what mounting the drive is. um and thanks every one else for the're tips i will try them. and i no longer have a laptop there was an incedint a few months ago that left it resting in pieces. and also i made sure that it is a 32bit and not a 64bit.

What kind of computer is it?

---

### Post by luckymoonboy1 on 2007-09-22
ok the computer is a micron electronics client pro and the harddisk is a 2001 40gig maxtor just incase you need that to. and to alienexplorers i don't know what any of those are and i cnat print anthing because yopu guessed it i need the software off the cd to run my printer. kind of ironic i know

---

