---
title: "[SOLVED] if u can help me i will appreciate it."
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Vic! on 2007-09-03
i just bought a toshiba satellite a135 s4656 and im very interested in getting rid of the crappy vista it comes with. i downloaded ubuntu 7.04 feisty fawn and i am trying it out by booting from the burned cd but i noticed i dont have any audio coming out of my speakers im not the most linux smart person either so i dont know what to do... i want to get rid of my vista but not before managing to get sound on my computer when i boot into ubuntu

THANX i appreciate any help i can get

vic

---

### Post by nowshining on 2007-09-03
since it's a newer computer I suggest waiting for Gutsy to officially come out as it should have better hardware support or you can download the dev. Gutsy and try it out but it might give some problems again i highly suggest sticking with what you have until october..

---

### Post by Vic! on 2007-09-03
thanx alot. i hope the october release will support my computers hardware so i can just install it and go about. but like you said what if that gives me issues also? there seems to be nothing else wrong with this 7.04 ubuntu except the sound i mean even my wireless internet reciever works right from the boot. it mentioned ssomething about a driver being restricted in use. will getting that help any?

---

### Post by wolfen69 on 2007-09-03
download gutsy [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) just to see how the live cd runs. it cant hurt. im running gutsy right now without any problems.

---

### Post by lnxmomo on 2007-09-04
Hey Vic, i have an A135 laptop (s2386). You have to install ubuntu first, then update fully and reboot then follow my guide [here]("http://ubuntuforums.org/showthread.php?t=539595&highlight=A135"). Sound should work perfectly. If you have brodband, this should not take longer than an hour (including installing, updating and sorting out sound). Post back and tell me how it goes. I got rid of Vista and now running 100% ubuntu :D

The restricted driver in use is your wireless atheros card. The other restricted file that is not in use is your graphics card driver, that should be installed after you install Ubuntu and updated it.

---

### Post by Vic! on 2007-09-05
im having trouble at the command prompt apparently the files weren't found.

---

### Post by lnxmomo on 2007-09-05
Have you created a /home/yourusername/downloads directory where yourusername is your user name :p

After you create that, download the packages there then follow my guide as normal

---

### Post by Vic! on 2007-09-05
THANX for getting my sound to work i did what u told me and it works except i had to put options snd-hda-intel model=3stack in the alsa base gedit thing at the bottom instead of the levono one you told me to use ................Ok now my sound works but i have this hissing coming out of my speakers it sounds like a loud fan or something i right clicked the speaker icon and went into volume control and messed with the settings when i go to file>change device select the realtek alc861-vd oss mixer and mute the first volume bars the sound completely stops but regardless of what i do to the hda intel alsa mixer it wont work  i hope this info is of use i have sound now but its low volume and lots of loud hiss .... I CAN FEEL this problem getting resolved slowly :)!!!

thx for ur help

---

### Post by Vic! on 2007-09-05
Thanx to u guys my sound is now static free...hiss free and working properly.... my wireless internet is good to go... all my devices are working great cd/dvd is playing ... sd card reader works also i hink im ready to get rid of my vista partition for this laptop any idea how i can do that??


it would make my month if i could do this hassle free thanx alot !!! :) :) :D

---

### Post by Vic! on 2007-09-05
thanx again lnxmomo :)

---

### Post by lnxmomo on 2007-09-05
Hey, nice to see things worked out.

As for sound working out of the box, I think this my be solved in ubuntu gutsy as a developer indicated this in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109838").

I hope you enjoy linux and ubuntu and if you are like me, you might get rid of vista :D. :guitar:

lnxmomo

---

