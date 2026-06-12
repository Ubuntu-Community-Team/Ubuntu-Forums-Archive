---
title: "Instillation Problems"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by himynameis on 2007-05-19
I'm trying to install Ubuntu 7.04 on my AMD 64 machine, I downloaded the amd-64 image and burned it to a CD at 48x

whenever I try to install, boot in safe graphics mode, check the disk for errors, or boot from first hard drive the system from the CD it will show the ubuntu logo and loading  bar and the bar will move back and forth and then the screen will go black and this message appears:

BusyBox v1.1.3 (debian 1:1.1.3-ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

could it be the CD?

Also I have Dapper Drake already installed on a Hard drive, but my system will not boot from the hard drive, it just tells me how much memory is on it when I boot up the PC. It doesn't say anything about GRUB until I pop in the 6.06 CD and try to boot from it, and even then it will sit and say its loading but it wont load. Its brand-new I just put the parts together, and I configured the BIOS to boot from IDE0 which is what my hard drive is connected to.

---

### Post by bobplano on 2007-05-19
what? 48X? your disk probably has plenty of errors on it, because of how fast it is writing. try 4X or less and also check the .iso's md5sum.

---

### Post by oilchangeguy on 2007-05-19
> **himynameis said:**
> I'm trying to install Ubuntu 7.04 on my AMD 64 machine, I downloaded the amd-64 image and burned it to a CD at 48x

whenever I try to install, boot in safe graphics mode, check the disk for errors, or boot from first hard drive the system from the CD it will show the ubuntu logo and loading  bar and the bar will move back and forth and then the screen will go black and this message appears:

BusyBox v1.1.3 (debian 1:1.1.3-ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

could it be the CD?

Also I have Dapper Drake already installed on a Hard drive, but my system will not boot from the hard drive, it just tells me how much memory is on it when I boot up the PC. It doesn't say anything about GRUB until I pop in the 6.06 CD and try to boot from it, and even then it will sit and say its loading but it wont load. Its brand-new I just put the parts together, and I configured the BIOS to boot from IDE1 which is what my hard drive is connected to.


if you've connected your hard drive to the motherboard correctly. it should be IDE0, not IDE1. try changing the settings in the bios and see what happens.

---

### Post by himynameis on 2007-05-19
> **oilchangeguy said:**
> if you've connected your hard drive to the motherboard correctly. it should be IDE0, not IDE1. try changing the settings in the bios and see what happens.

I went to go check, and it is configured as IDE0, sorry for the typo.

---

### Post by oilchangeguy on 2007-05-19
ok, next question. how is 6.06 already on the hard drive, if the computer will not boot from the hard drive? is this drive from another computer, that was running 6.06?

---

### Post by himynameis on 2007-05-19
> **bobplano said:**
> what? 48X? your disk probably has plenty of errors on it, because of how fast it is writing. try 4X or less and also check the .iso's md5sum.

I just burned the same image file at 4x and popped it into my computer, and it gave me the same error and the MD5 sums are the same. I'm going to try to download a different image file

---

### Post by himynameis on 2007-05-19
> **oilchangeguy said:**
> ok, next question. how is 6.06 already on the hard drive, if the computer will not boot from the hard drive? is this drive from another computer, that was running 6.06?

No, I put in a 6.06 CD while I was waiting for the other CD to finish downloading on a separate computer because I wanted to see my new computer in action. Unfortunately I cannot see much of anything but whats on the 6.06 live CD that I used to install Linux on my hard drive.

---

### Post by oilchangeguy on 2007-05-19
you might want to read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

in your first post in this thread, you said you had 6.06 on the drive. now you're saying 6.10. are you even sure what your're doing? i'd suggest the 32bit version of 7.04, instead of the 64bit version.

---

### Post by himynameis on 2007-05-19
> **oilchangeguy said:**
> you might want to read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

in your first post in this thread, you said you had 6.06 on the drive. now you're saying 6.10. are you even sure what your're doing? i'd suggest the 32bit version of 7.04, instead of the 64bit version.

I usually just use mail-ordered CD's to install the Ubuntu flavor. I'm not too on top of it today, the OS in the hard drive is 6.06 I thought I typed the wrong OS for some reason and changed it to 6.10. I'll try installing the 32-bit version.

---

### Post by jerrylamos on 2007-05-19
"can't access tty" is a catch all message for a bunch of time dependent hardware detection failures usually somewhere in the SCSI simulation of IDE, SATA, CD drives, etc.  There are some things to try in my post "Workarounds" in the  "Installation & Upgrades" forum.

Cheers, Jerry

---

### Post by himynameis on 2007-05-19
> **jerrylamos said:**
> "can't access tty" is a catch all message for a bunch of time dependent hardware detection failures usually somewhere in the SCSI simulation of IDE, SATA, CD drives, etc.  There are some things to try in my post "Workarounds" in the  "Installation & Upgrades" forum.

Cheers, Jerry

Thanks

---

