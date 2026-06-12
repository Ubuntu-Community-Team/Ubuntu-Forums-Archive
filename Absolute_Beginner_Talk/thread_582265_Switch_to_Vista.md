---
title: "Switch to Vista"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Ryan1180 on 2007-10-19
I tried ubuntu, and really just don't like it.
I tried popping the Dell Vista CD back in, and it shows up on the screen for ubuntu.  I clicked on the disk icon, but when I try to do anything, ubuntu says that it cant execute the operation because there is no application suitable for installation

How do I fix this?

Thanks!

NEW:I got the disk to load, but it says it is not in the correct windows format, any way to fix this? Thanks again!

---

### Post by oilchangeguy on 2007-10-19
> **Ryan1180 said:**
> I tried ubuntu, and really just don't like it.
I tried popping the Dell Vista CD back in, and it shows up on the screen for ubuntu.  I clicked on the disk icon, but when I try to do anything, ubuntu says that it cant execute the operation because there is no application suitable for installation

How do I fix this?

Thanks!

just as you did with ubuntu, you'll have to boot from the windows cd.

---

### Post by Ryan1180 on 2007-10-19
> **oilchangeguy said:**
> just as you did with ubuntu, you'll have to boot from the windows cd.


But When I try to boot it as I did, it said that it cannot open the files because there is no suitable program to do it.

---

### Post by SunnyRabbiera on 2007-10-19
try another distro perhaps.

---

### Post by oilchangeguy on 2007-10-19
> **Ryan1180 said:**
> But When I try to boot it as I did, it said that it cannot open the files because there is no suitable program to do it.

you can't run it AFTER you're already in ubuntu. it doesn't work that way.

---

### Post by Ryan1180 on 2007-10-19
> **oilchangeguy said:**
> you can't run it AFTER you're already in ubuntu. it doesn't work that way.

So basically I am stuck with this now then?

---

### Post by chuckyp on 2007-10-19
You have to boot the computer to the windows Vista cd.  Just like you did with Ubuntu.  You have to either change your bios to boot to the cdrom.  Or if its already set up that way you may need to press a key.

Put the vista cd in the drive and restart the machine.  Look at the screen something should come up about booting to cdrom before the ubuntu screen comes up.

Also you may want to ask on a vista forum since this is a support forum for ubuntu.

---

### Post by LowSky on 2007-10-19
lmao..sorry

you need to boot from your cd rom drive

it should an option at startup or go into your bios and set boot form cdrom

---

### Post by ratchevs on 2007-10-19
restart your computer with the windows cd still in the drive.

if it doesnt boot through it, you have to go into the bios (keep hitting del while computer is restarting, then go into boot order and change so that the cd rom is ahead of the hard drive)

---

### Post by yabbies on 2007-10-19
hey bro, 
put your cd in the drive and restart your computer
so that your cd drive will boot from disk
have fun with vista

---

### Post by Kleppemeister on 2007-10-19
If nothing of this works, you can try to press F8 when your stating the PC, that will bring up a Boot Device choice sorta page. You then have to selcte the CD room. After that, all you have to do is follow the intructions that or on your screen from there.
I can not say for sure its F8, as im not sure about Dell PCs.

---

### Post by Ryan1180 on 2007-10-19
New question posted!

---

### Post by HermanAB on 2007-10-19
Uhmmmm, it is not so easy.  Windoze is too dumb to know what to do with a hard disk that has been formatted with a Linux file system.

Sooooo, first you have to boot Linux one last time and erase the first little bit of the HDD.  Assuming that your HDD is SATA:
$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

If the HDD is IDE, then make that '/dev/hda'

Now you can reboot with a Vista CDROM and re-install.  However, this will probably not be smooth sailing either, since you may find that you need various device drivers that are not present on the CDROM.

Anyhoo, good luck!

Cheers,

Herman

---

### Post by comjo on 2007-10-19
I hired a guy to shoot me if I ever wanted to leave linux for the darkside, so I will never have this problem :lolflag:

Brandon

---

### Post by papuccino1 on 2007-10-19
Ryan I'm not sure if anyone has given you the necesary info but here goes: 

1. Restart your PC with the Vista CD inside the drive.

2. Press DEL or F2 or F3 (depending on what it says there) to enter the BIOS.

3. Select Boot Device Priority. It's easy to spot.

4. Select CDROM as boot device 1, and remove everything else.

5. Press F10. Select Yes.

6. When it prompts to press any key to boot from CD, press spacebar.

And your done. 

You should print this out, maybe you won't remember.

---

### Post by 11touche on 2007-10-26
Lol comjo

---

