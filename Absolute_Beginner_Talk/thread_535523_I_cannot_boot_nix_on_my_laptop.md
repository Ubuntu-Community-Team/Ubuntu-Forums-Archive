---
title: "I cannot boot *nix on my laptop"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by Morca007 on 2007-08-26
So, I am at college right now, and would much rather be using linux, but had installed XP to be sure I had something to work with right away. Fast forward to my first day on campus, and I find they are using "Cisco Clean access" on all windows PCs, this not only makes me dump nod32 for Mcafee, but adds another 23mb of ram usage!

Anyway, I cannot get any variant of linux to boot on my laptop. I have tried the ubuntu 7.04 livecd, PCLinuxOS, and an install of ubuntu via Wubi. Each one has not been able to boot. The only error message I can find is (may be slightly paraphrased) "ERROR: cannot mount livecd."

My computer is a Sager NP2090 (Compal IFL90), specs:
[http://www.powernotebooks.com/specs/Sager/2090specs.php](http://www.powernotebooks.com/specs/Sager/2090specs.php)
Centrino (Santa Rosa) platform, Geforce 8600m GT, 2.0ghz C2D, configured with an SATA HD, and 2gb ram.

Any advice? More info needed?

Thanks.

---

### Post by finer recliner on 2007-08-26
check the md5 checksum.

try reburning the disk at slower speeds.

---

### Post by Morca007 on 2007-08-26
I am attempting to check it, using the checksum "e296e3468358789904097fc8df29609a" from [http://ubuntu.media.mit.edu/ubuntu-releases/7.04/MD5SUMS](http://ubuntu.media.mit.edu/ubuntu-releases/7.04/MD5SUMS)
That should be the code for the same CD I have, then I am using MD5 Check utility V2 to check it versus md5sum.txt on the CD. That shows it not matching.

However, I do know the PClinux cd is good, and that the wubi install should have been clean.

EDIT: I just tried to test the cd for errors, and it booted me out to a busybox shell with this error (Which I have seen briefly on other ubuntu startup attempts):
/bin/sh: can't acces tty; job control turned off

---

### Post by Morca007 on 2007-08-29
Just checking, is there anyone out there who has an idea?
:-k

---

### Post by mlentink on 2007-08-29
You say you have tried Wubi? That doesn't involve a livecd at all, just a simple windows installation. 
Didn't that work either?

Coming to think of it, and this is probably obvious, but did you set up the cd-drive as a boot device in your BIOS? Having it boot prior to the harddrive?

---

### Post by Morca007 on 2007-08-30
I know Wubi is a simple install on a virtual disk.
And yes, I am booting to the correct drive, remember, I can get to the screen to choose what I want the livecd to boot into.

---

### Post by Morca007 on 2007-09-07
Alright, Knoppix boots just fine, after autodetecting that it needs to use vesa.

---

### Post by c1rcu17 on 2008-01-02
I have the same notebook, the NP2090 / IFL90, and I am running Gusty just fine. Follow this guys tutorial exactly, and you will have Ubuntu gusty running in no time. 

[NP2090 Tutorial]("http://lddubeau.com/avaktavyam/linux-on-a-compal-ifl90/")

By the way, if you are in college as am I, you will probably be using IE only web apps. Use [IE4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by jken146 on 2008-01-02
> **Morca007 said:**
> I am attempting to check it, using the checksum "e296e3468358789904097fc8df29609a" from [http://ubuntu.media.mit.edu/ubuntu-releases/7.04/MD5SUMS](http://ubuntu.media.mit.edu/ubuntu-releases/7.04/MD5SUMS)
That should be the code for the same CD I have, then I am using MD5 Check utility V2 to check it versus md5sum.txt on the CD. That shows it not matching.

However, I do know the PClinux cd is good, and that the wubi install should have been clean.

EDIT: I just tried to test the cd for errors, and it booted me out to a busybox shell with this error (Which I have seen briefly on other ubuntu startup attempts):
/bin/sh: can't acces tty; job control turned off

If the checksum is not matching that of your iso, then your download was corrupted.  Download it again.  Use a different mirror or a torrent.

---

