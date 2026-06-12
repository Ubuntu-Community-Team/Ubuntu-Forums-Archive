---
title: "Ubuntu 6.06 on Pegasos PPC computers, no more support ?"
date: 2006-05-29
forum: Apple PPC Users
---

### Post by SoundSquare on 2006-05-29
hello there

this is mainly a question to the Ubuntu PPC dev team. Is support for Pegasos computers still planned ? I used Ubuntu Breezy on my Pegasos and it worked (and still does) very well. Yesterday i wanted to install from scratch 6.06 RC and there's no more Pegasos boot image in the CD. When upgrading from Breezy to 6.06 using update manager it works but the vmlinuz image isn't generated so i can only boot on the breezy kernel. 
I noticed you made a nice OpenFirmware menu with options to boot from the CD  at the OF prompt but it cannot find the vmlinuz-chrp.initrd image for the Pegasos. 

is Pegasos support still planned ? will the boot image be included in 6.06 final ? 

thanks by advance.

---

### Post by lugduweb on 2006-05-31
Hi SSQ,

did you also looked on the latest Drapper drake Release Candidate CD ?

---

### Post by joshuapurcell on 2006-05-31
I am also very interested in the answer to this question. I have been planning on getting a computer from Genesi for quite some time now, and I will definitely be loading Ubuntu on it. I haven't had a chance to try the Dapper install on a Pegasos PPC-based system though. This may be a question for the development mailing list, but we'll see if anyone here knows the answer.

---

### Post by nkbj on 2006-06-01
I got this reply when asking for support for OldWorld Powermacs[1]:

> But yes, at present the powerpc desktop CD only supports NewWorld PowerMacs and (with luck, and a following wind) CHRP systems that can use yaboot. For other scenarios, and especially if you're supplying your own boot loader from somewhere, the alternate install CD is probably a better place to start.

Have you tried the alternate install CD?

[1] [https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/46521](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/46521)

Regards,
Niels Kristian

---

