---
title: "MyNewPC"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by ibbrxx on 2007-01-17
i was able to install ubuntu 6.10 from the live CD i downloaded with no problem to my old machine. just followed the instructions and it work the first time.

but the new machine which i bought is giving me problems.

this time i bought the new system with a 80G SATA Hard Drive & a 256 GeForce Graphics card. 

any help you can provide me please. i am very new but wanna stick with the new operating system i found in ubuntu.

---

### Post by Jussi Kukkonen on 2007-01-17
You need to tell us what the problem is... in as much detail as possible.

---

### Post by spockrock on 2007-01-17
posting your pc specs might help as well.

---

### Post by ibbrxx on 2007-01-17
Thank you Guys for opting to help me first of all.

I will do my best to explaine what happens:
I try and boot from the Live CD Ubuntu 6.10
the boot screen come and after a while the whole screen goes blank for a and some error codes and error messages come in white in a black screen then the system freezes and i will have to press the rstart button to restart the system.

Specs:

P4 3.06 GHZ
1GB RAM
80 G Maxtor STM 3802110A SATA Hard Disk
Geforce FX5500 Graphics Card

Any more info you might need!!!

---

### Post by Arturius on 2007-01-17
Were you able to read any of the error messages?

---

### Post by ibbrxx on 2007-01-17
lots of them come in a flash and i could make out "PCI" and some numbers.

---

### Post by Arturius on 2007-01-17
do you have any PCI cards installed in your machine? (sound, network etc?)

---

### Post by psycosmyth on 2007-01-17
That dang Nvidia again I bet, I have a low end card with no probs but it sounds like video to me, There are some good folks here I'm sure can help you solve this easy.

---

### Post by ibbrxx on 2007-01-17
i will do my best to note the errors and post here - until them pls excuse me.
thank you all for he support.

---

### Post by Arturius on 2007-01-17
Good luck, try using the pause button on the keyboard, it *should* pause it so you can read it, I hope you get your problem fixed :) - I doubt I would have been able to help but I hope I helped get more info for "the people that know" :D

---

### Post by psycosmyth on 2007-01-17
does the pc have an integrated graphics chipset as well as the pci? You'd have a second place to plug in the monitor.

---

### Post by ibbrxx on 2007-01-18
i found the problem.
i switched back to the onboard graphics and it worked.
baut try again with the GeForce FX5500 it won't.

pleaes guide me to install my GeForce FX5500.

---

### Post by irish_flu on 2007-01-18
If you don't want to use the integrated video, you can disable it (then Ubuntu shouldn't even have the chance to use it).

My advice is to read the documentation for your motherboard; there may be a setting in the BIOS you can change, or you may have to move a jumper on the motherboard itself (it kinda depends on the board).  Provided the FX5500 is working properly, you should then be able to plug your monitor into that.

Hope this helps!

---

### Post by r4ik on 2007-01-18
Try, in addition to irish_flu

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)  (11.3)

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)  (1.11.2.1)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Good luck !

---

### Post by ibbrxx on 2007-01-18
thnak you for the adivce.
will follw and be back asap.

---

### Post by psycosmyth on 2007-01-18
there are some support files for nvidia cards for ubuntu if you get the os to work, you can try the card then.

---

### Post by ibbrxx on 2007-01-18
still struggling with the card.
os is working 100% and i am proud of it.
it's jsut the FX5500 now.

---

### Post by ibbrxx on 2007-01-19
finally i got it working today with the help of all our you.
let me quickly share what i had to do:

downloaded the nvidia-glx_1.0.8774+2.6.17.5-11_i386.deb package.
and with the nelp of the above howtos blacklisted the buitin graphics card and configured xorg.conf.

i am a very happy ubuntu user now.
got my opeating system running with all my hardwared working perfectly.

---

