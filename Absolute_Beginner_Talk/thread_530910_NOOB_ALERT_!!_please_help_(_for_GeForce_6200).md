---
title: "NOOB ALERT !! please help ( for GeForce 6200)"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by obscurespectre on 2007-08-21
hi friends. 

i am an absolute noob at linux and know absolutely nothing about installation etc. i have sucessfully installed ubuntu 'fiesty fawn' on an old laptop and everything works out of the box.

the only problem i have is that i am unable to install ubuntu or any other linux distro for that matter on my PC which has a GeForce 6200 card. the live cd boots and i get to options like use livecd, install to Hd, start in safe graphics mode etc. on selecting 'use live cd' the process starts but soon the monitor goes blank n a dialogue pops-up saying that 'the monitor resolution is not supported. please select appropiate settings'

on the other hand i can boot into the livecd in safe graphics mode but the graphics are all substandard.

can someone please help me in step by step instructions on how to install 'fiesty fawn' on my hd and make it detect my geforce 6200 ???

(p.s. i also have an alternate install cd ..... but 'no go' there too)

---

### Post by d80zoom on 2007-08-21
I have a PNY GeForce 6200 AGP and did not have any problems with it. I am running Beryl and play a lot of games like Open Arena, and Tremulous.

It looks to me like you might have a monitor problem, not a Video card problem. Have you tried another monitor?

Also check your motherboard BIOS settings, maybe something is not set right.

---

### Post by aquavitae on 2007-08-21
Start in safe graphics mode, then install as normal.  Hopefully it will sort it out during the installation, but if not you can fix it afterwards.  You can't fix it before as there's nothing installed to fix!  For it to detect the geforce graphics card you'll need to install the nvidia driver (after installing the system.)  See this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

