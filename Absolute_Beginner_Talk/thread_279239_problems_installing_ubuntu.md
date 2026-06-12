---
title: "problems installing ubuntu"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by kurt09 on 2006-10-17
i am trying to install ubuntu for the first time.
the cd seems to be working. after booting from the cd the ubuntu-start menue appears. after choosing "install ubuntu" the following error ocurrs:
[B][B]"uncompressing linux ...
invalid compressed format (err=2)
... system halted"[/B][/B]

what is wrong?

---

### Post by geezerone on 2006-10-17
Did you perform a disk check on the live cd which i presume you are using?

---

### Post by taurus on 2006-10-17
Did you check the image with md5 right after you finish downloading it?  Also, make sure you burn it at a slower speed like 4x because fast burning can cause all kind of problems when trying to run/install it...

---

### Post by foneguy9 on 2006-11-06
I have the same exact error.  I requested the CD's 6.06.1 LTS from the Ubuntu website and I got the same error.  I have tried (2) CD's and am booting up with a third.  

On my test station I have a system that I have dedicated for testing Linux Workstation and server distros.  I will continue trying with the other CD's that I recieved in the mail, but I feel ](*,) ...

Unless you'all have some helpful hints.:-D

---

### Post by foneguy9 on 2006-11-06
I tried all (5) CD's that I recieved in the Mail.  All have the same error or with a (err -1).  

I also get the Splash screen and select the first option, Start or Install Ubuntu.

Oh, I also tried to check the CD for errors and have the same error.  The OS on the HDD is Mandriva One.  

System:
Intel Celeron 800 MHz
256 Megs of RAM
8.5 Gig HDD

---

### Post by foneguy9 on 2006-11-15
By the way, I tried the CD's (2) of them on my laptop, HP Pavilion dv1000 and they are working like a charm!  Even the integrated wireless was working as soon as the Ubuntu desktop came up!  
I didn't install Ubuntu, but the CD came up to the desktop just fine so the problem isn't the CD but probably my HDD or PC?

I have Mandriva Free on the whole HDD now. I don't know if that has anything to do with it.  On the HP Laptop, I have Win XP Home running.

---

### Post by dushy on 2006-12-19
I have a an old Pentium III 866 machine with 128 MB Ram. I tried to insatll XUbuntu and initially getting the [COLOR="Red"]Invalid compressed format (err=1)[/COLOR] error.

Read all the forums did the md5sum check and re-burned the CD at a lower speed (as suggested by almost all the replies), initially I stumbed up on a reply which suggested may be machine is too old to run the latest distros. Irony is the machine runs Windows XP without any problems.

After more Googling I came up on a reply suggesting updating the BIOS. After wading through HP website I found the BIOS upgrade to the machine, installed it, tried Xubuntu installation again.

Guess what, now I am getting [COLOR="Red"]Invalid compressed format (err=2)[/COLOR] now :-k. At least I am moving up the ladder :confused: Back to searching I suppose.

Hope this reply helps in any way.

The frustrating part is, I am a Windows user finally decided to venture in to Linux territory and encountered this problem. I was actually planning to convince & help all my  (less technical) friends to switch to Linux. I am a bit wary now.

---

### Post by taurus on 2006-12-19
Have you tried to boot the same CD from another machine to see if it boots at all?  Maybe it's not your machine; instead, it's the CD...

---

### Post by pointym5 on 2006-12-27
I'm getting exactly the same failure (err=2) on a 600X that has worked just fine with Ubuntu for a long time (and in fact still boots from its current HD installation).  The CDs I've burned boot fine on other machines, and the machine in question can boot other install disks for other OSes.

---

### Post by jvc26 on 2006-12-27
Is it a problem with the specs of your computer (@ pointym5) which stop it booting up? If its not the cd then it can only be the computer i guess.
Il

---

### Post by wpshooter on 2006-12-27
Pointym5:

Do you need the Mandriva O/S that you have on the computer ?

If not, why don't you remove it and see if that is causing your problems ?

---

### Post by pointym5 on 2006-12-27
> **wpshooter said:**
> Pointym5:

Do you need the Mandriva O/S that you have on the computer ?

If not, why don't you remove it and see if that is causing your problems ?

What in the world makes you think I've been running Mandriva?!?  I've had Ubuntu on it for a couple years now.  It's got a bootable upgraded Dapper -> Edgy system on the hard disk, and that continues to work fine. I wanted to try a reinstall because my Ralink-based PCMCIA wireless card stopped working after the upgrade.

In any case, it is so wildly improbable that the OS installed on the hard disk would make the CDROM boot fail that removing that installation is not worth considering at all.

---

### Post by pointym5 on 2006-12-27
> **Illuvator said:**
> Is it a problem with the specs of your computer (@ pointym5) which stop it booting up? If its not the cd then it can only be the computer i guess.
Il

No, it is not a problem with the specs. ***The machine boots just fine from the upgraded Dapper->Edgy installation currently on its hard disk.***

---

