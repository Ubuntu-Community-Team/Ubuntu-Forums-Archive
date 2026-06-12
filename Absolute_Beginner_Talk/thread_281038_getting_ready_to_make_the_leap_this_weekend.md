---
title: "getting ready to make the leap this weekend"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by at0mic on 2006-10-20
hi guys. im going to install ubuntu this weekend. my very first linux after hearing all the great things about this software and how easy it makes the transition im ready to make the plunge.

My question is that how i want to install linux is first install it on a solo 80GB hd with no other hd's plugged in so i dont mess up my windowz stuff [mistakes happen first time thru]. I read that you can modify the ubuntu boot loader to include windows later. Is it technically possible to do this if the boot drive for windows is on a raid 0 nvidia raid set?

I would also like to know if i have the freedom to install any other linux distributions [eg = debian] on a seperate partition if i so choose? is there any incompatability with any distro? Do they have to be installed in any order? Does the last os installed determine the boot loader?

Thanks.

---

### Post by Eddie Wilson on 2006-10-20
Hello and welcome to this crazy world. I really don't know about the raid setup but from what I've read it should work ok. On the other distro, you can install any other distro you like. As long as you have another partition there will be no problems. Also the last distro you install will determing the boot loader. You can edit the boot loader later on to fit your needs. I triple boot my system and I've had no problems at all. Again welcome to the world of linux.

Iguana =D>

---

### Post by elchinovi on 2006-10-20
Welcome to the comunity, at0mic!
I just wanted to add that not only you can multiboot, but you need only one swap for all linux distros!
That's cool!
If you run into any problems, come over and post them, and we'll try to get them fixed!
Good Luck!

---

### Post by ReaderRat on 2006-10-20
Don't know about RAID. Yes, you can install more than one distro and add them to GRUB bootloader, but you are limited by the number of Primary partitions (4) you can have.You only need one /swap partition for all distros. If you load Windoze and Linux on the **same** HDD, you should load Windoze first.Linux distros can be installed in any order.

---

### Post by herrweh on 2006-10-20
I cheated and avioded all the geeky stuff about partitions, etc. I removed my floppy drive and ran the HD IDE and power cables through the opening. I then went on line and bought about 4 15 GB hd's for about $20 each. I loaded a different Linux flavor on each, swapped them out every few days, decided which I liked best (Kubuntu), then later permanently installed that hd in my computer.
Good luck

---

### Post by Pablo Pablovski on 2006-10-20
I had problems getting dual boot of XP and ubuntu working on my nForce 4 RAID 1 drive (2x 250GB SATAs). It installed fine, but always booted into XP with no chance to select anything else. I tried everything I could, but eventually I removed RAID, and restored XP to one disk and installed ubuntu on the other. All went in smoothly. I now use Acronis Disk Director Suite as the boot manager. 

I wasn't able to find much help anywhere on how to fix the problem, but I'm pretty sure it was something to do with the nVidia RAID drivers - I tried a couple of versions, but neither had any effect.

Good luck, though! ubuntu is a treat. 8)

---

### Post by Mimsy on 2006-10-20
> **at0mic said:**
> hi guys. im going to install ubuntu this weekend. my very first linux after hearing all the great things about this software and how easy it makes the transition im ready to make the plunge.


Um... not to break up the thread with negativity here, but I hope you've heard [a balanced account of Ubuntu]("http://www.ubuntuforums.org/showthread.php?t=63315"), and not just the infatuated declaration of perfection that comes from a certain type of user (of *any* OS, not just Linux)? Ubuntu makes it easier, yes, but that's not the same as easy.

Expect a sharp learning curve, hardware compatibility issues, and lots of frustration or confusion. They may not happen, but if they do, don't be surprised. Just come back here and ask questions, and wait for the great help you'll get.

You seem pretty sane though. :) 

/Mimsy

---

### Post by at0mic on 2006-10-20
thnx guys. much love in the room.

i cant wait to get home and start the adventure and post back here when im up and running. the first time i install and listen to music / watch movies on something other than windows is going to be a rush. whole new world to explore.

Mimsy:
yes i know of the challanges ahead and welcome them. its part of the fun if u ask me. with my new friends here and google im sure ill be ok. im gonna also squat the irc channel thats up for sure.

---

### Post by barkej on 2006-10-20
Welcome to the community!

---

### Post by Mimsy on 2006-10-20
I thought you seemed sane enough. ;)

Welcome to Ubuntu. You will be assimilated. :)

/Mimsy

---

### Post by at0mic on 2006-10-20
I MADE IT ! WoOT !

first impressions:
after some altercations with my bios and stupid nv raid i loaded unbuntux64 without much difficulty. extremely impressed with the quick install and picked up all my hardware and installed the drivers. even had internet right off the bat with no internet setup! [ms cant even do that] 

i did experience one hickup and possibly a bug where i loaded up first time and it said i had 48 updates!! so i updated immeadiately and tried clicking some of the buttons to see what they would do... while it was installing all the packages i hit the hide all windows button and then lost all control to click anything. after the updates were done it said click here to restart... i couldnt even click that or anything after the updates were done. mouse moved fine and the box that said click this button to restart eventually faded so i didnt crash... had to power down the hard way... after reboot it brings me to here... on to setting up easyunbuntu!

---

### Post by dbd on 2006-10-20
Woo!

In the future to avoid pressing your PC's power button (potentially damaging data) it might be best to press Ctrl+Alt+Backspace. That will restart X (the basic graphical frontend) so you can shut down safely.

Also, if you are feeling nice you could look at [launchpad]("https://launchpad.net/distros/ubuntu/+bugs") to see if it is a known bug. And if not then file a new bug report and give details on how to reproduce it. Then it can get fixed :)

---

### Post by at0mic on 2006-10-20
i tried the classic 3 finger salute but it wouldnt work :D  [alt+cctrl+del]

any cute terms for alt+ctrl+backspace yet? almost too easy with backspace...

now got the shoutcast goin... linux soundin good!

just need to figure out how to increase brightness and change font now...

---

### Post by confused57 on 2006-10-20
I've never used EasyUbuntu, but I've had excellent results with automatix:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Mission 10 on 2006-10-20
Welcome! (I'm always late with that...) And congrats on a good install... If you like music then you must try out Amarok.. it's a sweet sweet app for music. I think it's in automatix.

---

### Post by Mimsy on 2006-10-20
I've tried both Automatix and EasyUbuntu, and I haev no preference other than the purely aesthetical one - Automatix isn't as pretty.

Amarok is in Synaptic, and is awesome. Just remember to install the extra codecs, for file formats' sakes... if you have issues with mp3 files, try [this solution.]("http://ubuntuforums.org/showthread.php?t=267704")

/Mimsy

---

