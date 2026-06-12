---
title: "IMac: Problem installing Ubuntu so... Lubuntu?"
date: 2015-01-17
forum: Apple Hardware Users
---

### Post by isabelle3 on 2015-01-17
Hello everyone!!
I have an IMac with a 32 bits processor and I can't install Ubuntu on it (I don't really know why, when I press ALT, the dvd is ejected) so I was wondering if it's possible to intall Lubuntu on my mac and if so, how to? If not, who wants a mac?
Thanks in advance!

---

### Post by kerry_s on 2015-01-18
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

---

### Post by yancek on 2015-01-18
The link posted above is 7 years old so I'm not sure how it will work.  The link below is for installing Ubuntu 14.04 the most current long term release.  Note the version of the imac.  I've never used a Mac so don't know what is current.

[https://blog.sman.dk/?p=261](https://blog.sman.dk/?p=261)

Although many people have managed to do this, if you are an inexperienced user I doubt it will be easy.

---

### Post by isabelle3 on 2015-01-18
Thx Yancek. Done everything and still dont work.

---

### Post by Rex Bouwense on 2015-01-18
You did download the correct image didn't you?
[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

---

### Post by yancek on 2015-01-18
Apple is and always has been very proprietary and has done everything it could to prevent people from doing what you are trying to do.  Simply because there is no money in it for Apple.  People have done it so it is possible but it certainly won't be easy.

---

### Post by isabelle3 on 2015-01-22
Hi everyone,
I have an old Imac 32 bits processor. And I just can't install Ubuntu on it... Everytime I put the burned DVD, it's ejected automatically. Does anyone has the same problem?

---

### Post by isabelle3 on 2015-01-22
What is a Mac image and where can it be found?

---

### Post by lisati on 2015-01-22
Threads merged. Please do not start multiple threads for the same problem, it can get confusing and it dilutes the community's ability to help.

---

### Post by mörgæs on 2015-01-22
There are many different Imacs. Please post the hardware details.

---

### Post by isabelle3 on 2015-01-22
Hi. Thanks for your answers. Sorry for the double thread... 
It's a 10.6.8 with a 2GHz Intel Core Duo processor

---

### Post by mörgæs on 2015-01-23
I was asking for hardware details. 10.6.8 is an operative system.

Anyway, moving to the Apple forum to see if someone there is able to help.

---

### Post by este.el.paz on 2015-01-23
@Isabelle:

All other DVDs stay in when you hit "alt" key?  And only Ubuntu ejects?  And, isn't iMac 64 bit?  That shouldn't make a difference to install 32 bit can install in 64 bit system.  I have had Xubuntu 14 installed on my MBPro, now running LM17?? based on Ubuntu 14 . . . traditionally it has been easier to get Xubuntu running on the MBPro than Ubuntu for some reason.  

Did you check the md5sum number for the iso?  Did you burn the DVD on the iMac or something else? As some mentioned there is now a "amd+mac" option, which may or may not make a difference depending on who is reporting.  For me, I used rEFInd as the boot manager to load the GRUB window, whcih will then boot linux--so possibly you will need to install that, then do a "manual" partition, with 3 partitions, small 10 MB for "bios_grub" . . . a "home" formated as ext4 and flagged as "/" . . . and then a swap of 1 - 2x RAM.  But of course first you have to be able to boot the DVD . . . check the md5sum, then try to re-burn the DVD at "slowest speed" . . . or try another flavor, like Lubuntu or Xubuntu . . . or try to make a bootable USB drive version and see if you can boot that.

There is a learning curve to get linux to run on an apple . . . also check the "mactel" sticky at the top of the page for "fan control" threads . . . .

e.e.p.

---

