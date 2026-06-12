---
title: "Install Ubuntu on laptop without CD drive"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by mcdermott_c on 2006-08-16
Hi

New to linux although i have installed it before and played around with it. I was wondering how I could install ubuntu on a sony srx41p which doesnt have a built in CD drive. I dont have an external cd drive either however I wondered if it was possible to install without a CD drive (i do have a USB external hard disk) and if there were any good step by step guides on how to do this.

Many thanks for the help

Chris

---

### Post by xpod on 2006-08-16
Cant tell you for sure but i believe it`s quite possible to just download the os itself from the internet.

Im not 100% sure but im positive i seen it somewhere.....there WILL be a simple answer im sure.Everything else on Ubunto seems to have one

---

### Post by davidY on 2006-08-16
I am no expert, but this sounds like the chicken egg problem - you are not in ubuntu, so you cannot install ubuntu.. or something like that.... sorry, I am a newbie here too (just waiting for people to help my post :-), thought I keep you some small company)

---

### Post by seshomaru samma on 2006-08-16
I think you double posted
see my suggestion [here ]("http://ubuntuforums.org/showthread.php?t=237431")

---

### Post by lupine_nickt on 2006-08-16
Yes, you can... I managed to install it on an ancient laptop recently, which had no working floppy *or* CD-ROM drive! A bit of a pain to do, though. 

Since Ubuntu is knocked-up Debian, you can do it all manually by using the 'debootstrap' tool to copy over the base system, installing and setting up the kernel and bootloader yourself, then running 'apt-get install ubuntu-desktop' to get all the GUI stuff. It does require a lot of patience and a degree of confidence with command-line tools, but it's perfectly possible.

Alternatively, you can follow this:-
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

xF,

...Nick

---

### Post by bobpur on 2006-08-16
If you have USB ports couldn't you load  it into a flashdrive and then feed it to your laptop that way. Puppy Linux is supposed to be able to be installed that way. 
For that matter, couldn't you take your external harddrive hook it up to another computer install to the drive and then re-attach to the laptop. From then on it should be like a regular install.
Never having fooled with laptops this is all conjecture on my part.
                               Good Luck!

---

