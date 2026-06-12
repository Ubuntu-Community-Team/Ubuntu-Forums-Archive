---
title: "installation error"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by tudj on 2007-06-03
i am trying to install the 7.04 version of ubuntu. i made a LiveCD and when i boot from it, i select the install option and the process continues, i get the screen with a loading bar with an orange block moving left to right, after a while it then starts to load but i get the following error:

[124.6436] Buffer I/O error on device fd0, logical block 0

this continues to appear every few seconds, i understand that device fd0 is my floppy drive, when i first tried to install Ubuntu i did not have one connected and it was disabled in the BIOS, i have tried again several times with the floppy drive connected and enabled in BIOS.

Computer Specs:

Core 2 Duo E6300
Gigabyte P965-DS4 motherboard
Gskill PC-6400 DRR2
ATI X1900GT 256MB
120GB SataII HDD
DVD-RW
floppy drive.

i am a complete linux noob so please keep anything you suggest in the most simple terms.

---

### Post by Jussi Kukkonen on 2007-06-03
If you happen to have a CD-drive lying around, you might want to try swapping it with your DVD-drive for the install (just a hunch)... Also, you might want to try the alternative install CD, it may well work.

This may be your bug:
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306)

---

### Post by tudj on 2007-06-03
ok thanks alot, where do i get the alternate CD image?

---

### Post by southernman on 2007-06-03
Did you happen to d/l a copy of the "alternate cd?"

If not, I would suggest trying it too. Of the specs you posted, I'd think the thing that would give you trouble would be your video card. Perhaps you'll be the exception to the rule.

You may want to have a look here.. [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306") first. Sounds similar to what your running into.

Good luck

---

### Post by tudj on 2007-06-03
> **southernman said:**
> Did you happen to d/l a copy of the "alternate cd?"

If not, I would suggest trying it too. Of the specs you posted, I'd think the thing that would give you trouble would be your video card. Perhaps you'll be the exception to the rule.

You may want to have a look here.. [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/97306") first. Sounds similar to what your running into.

Good luck

no i didnt, i dont know where to dl it from.

thanks for the link, it is the same problem

---

### Post by southernman on 2007-06-03
> **tudj said:**
> no i didnt, i dont know where to dl it from.

thanks for the link, it is the same problemYou'll feel better if you can get this issue resolved, but none-the-less you get the alternate cd from the same place you got the live cd which would be here... [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download").At the bottom of the page you'll have an option to tick a box next to where it says: > Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer. Tick the box after selecting your mirror... and away you go! ;)

---

### Post by tudj on 2007-06-03
> **southernman said:**
> You'll feel better if you can get this issue resolved, but none-the-less you get the alternate cd from the same place you got the live cd which would be here... [http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download").At the bottom of the page you'll have an option to tick a box next to where it says:  Tick the box after selecting your mirror... and away you go! ;)

i found that a few minutes after posting, thanks all the same, nearly completed the download but will have to burn/attempt to install tomorow evening, thanks again to all who reponded, i will report back tomorow night :)

---

### Post by southernman on 2007-06-03
> **tudj said:**
> thanks again to all who reponded, i will report back tomorow night :)Your welcome... and please do. Let us know how it goes. Am sure everything will be ok using the text based installer.

Sleep well -

---

### Post by tudj on 2007-06-04
theres good news and bad news....

good news is that the alternative installer does not get the same fd0 error message, i do however get another but dont have time to write it down, the installation process does continue after a few seconds however.

I select my country and keyboard layout but then get an error saying there is no CD-ROM connected, but there is as i used it to boot from the CD. I can try another DVD drive on thursday, until then is there any other possible solution ?

---

