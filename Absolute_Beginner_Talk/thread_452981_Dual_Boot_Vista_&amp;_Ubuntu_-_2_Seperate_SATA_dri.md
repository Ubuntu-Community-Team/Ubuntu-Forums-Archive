---
title: "Dual Boot Vista &amp; Ubuntu - 2 Seperate SATA drives."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by gezus on 2007-05-23
Dist,

I currently have 1 SATA drive running Vista.  I plan on adding a second SATA drive and would like to install Feisty on it.

I am curious as to whether or not anyone has done this, and if so what I should look out for, or what I have to do in order to be able to boot into both OS's once completed.

Regards,
Sean.

---

### Post by Hobo Joe on 2007-05-23
Yes, it has been done.
Yes, it is possible, and from what I hear, easy too.
The install will setup the bootloader for you, all you have to do is wait for it to install. :)

---

### Post by jimrz on 2007-05-23
> **gezus said:**
> Dist,

I currently have 1 SATA drive running Vista.  I plan on adding a second SATA drive and would like to install Feisty on it.

I am curious as to whether or not anyone has done this, and if so what I should look out for, or what I have to do in order to be able to boot into both OS's once completed.

Regards,
Sean.

i have a dual boot with xp on one sata2 drive and feisty on another. i tried the normal dual boot proceedure that i had been using with ide drives and kept getting grub errors on the initial restart. seems that my bios/grub/sata did not want to play nicely together. what i did was:
1- completely disconnect the xp drive, including the power connector to it
2- plug my ubuntu drive into the first sata slot (bios would not do anything w/o a drive connected to this port)
3- re-ran the ubuntu install and did the initial updates
4-plugged the xp drive back in, connecting to the next available sata port.

this worked perfectly setting up both edgy and, later, feisty.  i now, on the fairly rare occasions that i boot that system into xp, have to hit f12 to enter setup to select the xp drive or just let it run to boot ubuntu. i later found some how-to's to get around this or at least  add xp to my grub menu but never even bothered to mess with them, since the method i described works great / does not touch the win mbr and does not take any longer to boot xp (fewer kestrokes even) than accessing it via grub.

EDIT: since i had already messed up my mbr, i first had to boot from xp cd / do fixmbr and then start the proceedure above. if you have not yet started, this will not be needed

---

### Post by gezus on 2007-05-23
> **jimrz said:**
> i have a dual boot with xp on one sata2 drive and feisty on another. i tried the normal dual boot proceedure that i had been using with ide drives and kept getting grub errors on the initial restart. seems that my bios/grub/sata did not want to play nicely together. what i did was:
1- completely disconnect the xp drive, including the power connector to it
2- plug my ubuntu drive into the first sata slot (bios would not do anything w/o a drive connected to this port)
3- re-ran the ubuntu install and did the initial updates
4-plugged the xp drive back in, connecting to the next available sata port.

this worked perfectly setting up both edgy and, later, feisty.  i now, on the fairly rare occasions that i boot that system into xp, have to hit f12 to enter setup to select the xp drive or just let it run to boot ubuntu. i later found some how-to's to get around this or at least  add xp to my grub menu but never even bothered to mess with them, since the method i described works great / does not touch the win mbr and does not take any longer to boot xp (fewer kestrokes even) than accessing it via grub.

I may be wrong, but from what I am reading Vista doesn't deal with this in the same way?
If someone can confirm your method to work with vista, I will do that, but will wait to hear more.

---

### Post by Hobo Joe on 2007-05-23
> **gezus said:**
> I may be wrong, but from what I am reading Vista doesn't deal with this in the same way?
If someone can confirm your method to work with vista, I will do that, but will wait to hear more.

I've never done it, but I've heard there are big workarounds to getting Vista working alongside Linux, I forgot to mention that in the first post, sorry! :redface:

I'm gonna look around, I'll keep you posted if I find anything.

---

### Post by gezus on 2007-05-23
> **Hobo Joe said:**
> I've never done it, but I've heard there are big workarounds to getting Vista working alongside Linux, I forgot to mention that in the first post, sorry! :redface:

I'm gonna look around, I'll keep you posted if I find anything.

Please do, I would greatly appreciate it.

---

### Post by gezus on 2007-05-23
If you can, take a look at this
[http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux)

Let me know what you think?

Regards,
Sean.

---

### Post by Hobo Joe on 2007-05-23
> **gezus said:**
> If you can, take a look at this
[http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux)

Let me know what you think?

Regards,
Sean.

As far as I can tell that guide looks perfectly fine for what your trying to do, but like he says, make sure you do EXACTLY as the guide says or you could really screw something up.

---

### Post by gezus on 2007-05-23
This worked fine.

Very simple/very straight forward.

Regards,

Sean.

---

