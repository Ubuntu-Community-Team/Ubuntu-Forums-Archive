---
title: "Trying to run 11.04 live cd on Macbook pro 5,2"
date: 2011-05-01
forum: Apple Hardware Users
---

### Post by byrnejb on 2011-05-01
I have downloaded the 64 bit iso and burned the CD-ROM per the instructions.  The CD is verified.  

When I boot the mac, holding down the C key, I get a menu of options relating to Ubuntu. If I choose the trial run from CD then the CD drive starts up but the screen goes blank and I end up with just a blinking underline cursor in the upper left hand corner of the screen.

Does anyone known if one can, and if so how, to boot the live CD on a Macbook Pro 5,2?

---

### Post by Silmathoron on 2011-05-02
When in the Cd menu (displaying "try ubuntu without installing", etc) press F6 and choose nomodeset. If it isn't engough, try the other options

PS : you can also try to launch in safe graphic mode (F4)

---

### Post by furukazu on 2011-05-02
The Natty LiveCD will not boot out of the box on MBP5,1 / MBP5,2 

since nouveau fails on the 9600MGT.

You can boot up the LiveCD by using kernel command line option 



nouveau.noaccel=1



[FONT=Verdana]Refer to the "Boot/GRUB/Plymouth" section in below link, please.
[/FONT][FONT=Verdana]
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty)

[/FONT]

---

### Post by JohnAtilano on 2011-05-03
> **furukazu said:**
> The Natty LiveCD will not boot out of the box on MBP5,1 / MBP5,2 

since nouveau fails on the 9600MGT.

You can boot up the LiveCD by using kernel command line option 



nouveau.noaccel=1



[FONT=Verdana]Refer to the "Boot/GRUB/Plymouth" section in below link, please.
[/FONT][FONT=Verdana]
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty)

[/FONT]

Actually, it will work.  Slimathron's advice is correct.  Press "F6" select "nomodeset" and "Try Ubuntu..." Did it last night and install went perfectly.  I'm posting from my MBP 5,1 running 11.04 64-bit.

---

### Post by Silmathoron on 2011-05-03
Actually, I wonder if our posts are not two solutions to the same problem, as the issue does come from the nouveau driver ;)

---

### Post by JohnAtilano on 2011-05-03
> **Silmathoron said:**
> Actually, I wonder if our posts are not two solutions to the same problem, as the issue does come from the nouveau driver ;)

Touche.

(For the record, that is NOT douche!  I don't know how to type an "e" with an accent!) :D

---

### Post by Silmathoron on 2011-05-03
Touché ;) (a French keyboard is a great help)

---

