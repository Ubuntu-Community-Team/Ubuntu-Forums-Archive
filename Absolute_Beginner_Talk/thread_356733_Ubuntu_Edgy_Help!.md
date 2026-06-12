---
title: "Ubuntu Edgy Help!"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by ertrules22 on 2007-02-08
I really need some help, and I don't know what to do.  I have a really old laptop like celeron, with almost no memory and want to put Linux Ubuntu on it, but at the bootup it starts the install than starts giving me logical errors, and I have no idea why!!  I am trying to install Ubuntu Edgy, the newest Ubuntu from a disk, but it won't work!!!!!!

---

### Post by meng on 2007-02-08
How much memory do you have?

---

### Post by ertrules22 on 2007-02-08
Hang on, okay, I have 9 GB on my C drive (the local disk) and it runs Windows XP at a slightly slow speed.  The laptop is dell inspiron designed for Windows 2000.  It is pretty old, but not too bad.

---

### Post by ertrules22 on 2007-02-08
And the disk should work fine, because my dad just installed it on his laptop a few days ago.

---

### Post by meng on 2007-02-08
No I mean RAM. It's vital to determine whether your computer is capable of running Ubuntu.

---

### Post by ertrules22 on 2007-02-08
My Bad, okay, it is 597 MHz and has 128 MB of RAM, thus it probably sucks!

---

### Post by jd65pl on 2007-02-08
You could try [xubuntu]("http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/") on that machine it is less resource hungry. You may have more luck with it. Try dapper first though as it is more new user friendly

---

### Post by meng on 2007-02-08
You're best advised to download and burn the Alternate CD, and I would recommend you try Xubuntu rather than Ubuntu. Your machine should still manage Xubuntu okay.
e.g. you could get it from here
[http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.06.1/release.1/](http://ubuntu-cdimage.datahop.it/xubuntu/releases/6.06.1/release.1/)
(the file called alternate-i386.iso

---

### Post by shareMenaPeace on 2007-02-08
I think you need xubuntu because the alternate might need 256 ram to install (and 128 to run) but dont remember for sure now.

I suggest install xubuntu and try to install the ubuntu server version and than after this done, the desktop (kde or genome) but for performance you better of with xubuntu.

Cheers

---

### Post by TBOL3 on 2007-02-08
The alternate disc will not install the ubuntu desktop.  Once you have ubuntu installed, log in and type, sudo aptitude install xubunt-desktop

---

### Post by shareMenaPeace on 2007-02-08
> **TBOL3 said:**
> The alternate disc will not install the ubuntu desktop.  Once you have ubuntu installed, log in and type, sudo aptitude install xubunt-desktop
Ah good to know, 
and to install xubuntu desktop i think you need to type

sudo aptitude install xfc4-desktop ? Or is this the same as 
sudo aptitude install xubuntu-desktop?

---

### Post by meng on 2007-02-08
> **TBOL3 said:**
> The alternate disc will not install the ubuntu desktop.  Once you have ubuntu installed, log in and type, sudo aptitude install xubunt-desktop
No that's incorrect, the Alternate CD for Ubuntu (or for Xubuntu or for Kubuntu) will install the graphical desktop. The Server CD will not install a graphical desktop. Quite different.

---

