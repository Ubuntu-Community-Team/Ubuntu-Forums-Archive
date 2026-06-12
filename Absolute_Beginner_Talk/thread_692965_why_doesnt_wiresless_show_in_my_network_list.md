---
title: "why doesnt wiresless show in my network list"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by elduderin00 on 2008-02-10
Hi,

I'm having a problem ...i'm very new to ubuntu so may be mssing something abritary. I've tried to be a thorough as i can to find the problem myself but have hit a wall

I've been triyng to install my wireless netgear wg111t usb dongle for about 10 hours. apparently it is possible:

[http://ubuntuforums.org/archive/index.php/t-574474.html](http://ubuntuforums.org/archive/index.php/t-574474.html)

and i've followed everything in that thread...i have the drivers installed for sure ( intalled with windows wireless drivers and double checked in the terminal)

So when o go to network ( system>admin>network ) there isnt any wireless network option there...just wired and modem options...what am i missing??

I followed another troubleshooter [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) 


it seems if i do the lshw command my dongle shows up but doesnt seem to have a driver attachedt( under configuration in the output of lshw for my driver it just lists info about speed and power consumption) so is this my problem.....

the troubleshooter doesnt say what to do if there is not a driver attached...i get to step 3.2 then it bottoms out on me! 

Please help one very frustrated ubuntu newb !

---

### Post by tennvolsmb on 2008-02-10
just so it's clear you are using ubuntu 7.04 fiesty fawn or later. Correct?

---

### Post by masingerz on 2008-02-10
I use wireless with ndiswrapper, atool that converts windows drivers into linux usable wireless drivers.

[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)

theres a step in there thats outdated, try gonig into synaptic and searching for ndiswrapper

---

### Post by ichbinesderelch on 2008-02-10
do you have version1 or version 2 of the netgear usb dongle? on a quick research on the internet i found out that the easiest way to get it working should be with ndiswrapper.. 
try this [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29) out ;)

---

### Post by elduderin00 on 2008-02-10
Hi,
thanks for the prompt replies...
Sorry left some important info out there.....yes i'm on fiesty fwn 7.04....i got it with the big orange linux ubuntu unleashed!!

Yes i've done the ndiswrapper thing.....installed it through synaptic and then used terminal to install the drivers......then i want sure if it had worked so i went tosystem>admin>windows wireles drivers and tried installin g them, again but it said they were already installed.

So to re-cap the drivers are there and the usb dongle does show when i do lshw but no driver seems to be attached in the lshw listing

---

