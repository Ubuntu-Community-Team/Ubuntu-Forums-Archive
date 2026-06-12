---
title: "FreeBSD or Ubuntu Specific Hardware issues"
date: 2007-03-28
forum: BSD
---

### Post by heather on 2007-03-28
Hi

i have been using FreeBSD i think it is a wonderful os
i Use OpenBSD as my Web and File Server.

i have also tried Ubuntu in the past and it too was a very nice Distro

My main complaints about FreeBSD is i can not use the following hardware

1) Logitech Orbitron Cam
2)Hp 3930 or 3900 series Printers


My Questions are will Ubuntu be able to overcome my Hardware issues
Should i come back to Ubuntu. as my Desktop.

Thank You :)

---

### Post by mips on 2007-03-28
The printer will work.
Camera might work depending on the chipset it uses.

---

### Post by heather on 2007-03-28
> **mips said:**
> The printer will work.
Camera might work depending on the chipset it uses.



Hi

ok on the printer that part sounds good,and i do belive i had seen it work before.
and i didnt even have to do anything to get it to work,
But the Camera a Logitech Orbitron MP i am not sure of yet if Ubuntu wreallyu suports it or no

If i ever decide to go back to Ubuntu as my Dekstop
i woud have to start over perhaps go over and go over All of
my old notes to install the old xscreensavers ad the nvidia acceleration drivers as well
Also im not sure if i can use fwbuilder with ubuntu or ssh password authenticatrion

Thanks for your help

---

### Post by mips on 2007-03-28
> **heather said:**
> Hi

ok on the printer that part sounds good,and i do belive i had seen it work before.
and i didnt even have to do anything to get it to work,
But the Camera a Logitech Orbitron MP i am not sure of yet if Ubuntu wreallyu suports it or no

Usually no problems with HP printers & linux, they work great. Plug & play.

The camera is very much dependant on the chipset. I would be able to tell you if it works if you give me the output of the following with the camera plugged in:

```
lsusb
```


> **heather said:**
> 
If i ever decide to go back to Ubuntu as my Dekstop
i woud have to start over perhaps go over and go over All of
my old notes to install the old xscreensavers ad the nvidia acceleration drivers as well
Also im not sure if i can use fwbuilder with ubuntu or ssh password authenticatrion

Thanks for your help

Throw the notes away unless you need to remember your favourite apps or screen savers. These days things are much easier. Try Feisty Fawn release, the beta is out.

If you use FreeBSD & OpenBSD then Ubuntu will be a walk in the park for you.

---

### Post by heather on 2007-03-29
Hi

i am sorry i did not get back to you sooner
Ok i just logged onto my other machine on FreeBSD
as you are well aware i dont have Ubuntu installed
so the command lsusb woudl be invalid

code:
lsusb

command not found
$


So what i did was installed Ubuntu anyways to give things a spin and here is my output

Bus 005 Device 002: ID 046d:08c2 Logitech, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:7604 Hewlett-Packard
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 093a:2500 Pixart Imaging, Inc.
Bus 002 Device 002: ID 050d:0551 Belkin Components
Bus 002 Device 001: ID 0000:0000

---

### Post by heather on 2007-03-29
Hi

If someone coul dhelp me get my Web cam working

My Logitech 4000 works but Logitech Orbitron MP wont
i used Softphone to detect and try both cameras


i prefer my Orbitron as it has a built in mechanical tracker

Thank You'

---

### Post by mips on 2007-03-29
This should help you:

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
[http://www.lavrsen.dk/twiki/bin/view/Motion/LinuxUvcTrackingPatch](http://www.lavrsen.dk/twiki/bin/view/Motion/LinuxUvcTrackingPatch)

---

### Post by heather on 2007-03-29
> **mips said:**
> This should help you:

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
[http://www.lavrsen.dk/twiki/bin/view/Motion/LinuxUvcTrackingPatch](http://www.lavrsen.dk/twiki/bin/view/Motion/LinuxUvcTrackingPatch)


Thank You :)

---

### Post by heather on 2007-03-29
> **mips said:**
> This should help you:

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
[http://www.lavrsen.dk/twiki/bin/view/Motion/LinuxUvcTrackingPatch](http://www.lavrsen.dk/twiki/bin/view/Motion/LinuxUvcTrackingPatch)

i had went to the first link you had provided but could not really find the link to
the driver i am supose to install.
i saw something that said download but was unable to click it

Rember this is my first time using Ubuntu in a very long time lol
and i may need some guidance

Thank You

---

### Post by mips on 2007-03-29
I will get back to you. I just saw those sites as being a source of info, the drivers might even be in the repos.

---

### Post by heather on 2007-03-29
> **mips said:**
> I will get back to you. I just saw those sites as being a source of info, the drivers might even be in the repos.

HI

Thank You

i installled my old 6.06 badge or dapper i cant remember which i had 
but now i am downloading 6.10
i am going to burn and install that.
while i wait for your next reply

---

### Post by mips on 2007-03-29
> **heather said:**
> 
but now i am downloading 6.10
i am going to burn and install that.
while i wait for your next reply

7.04 beta maybe ? 6.10 was/is not that great.

---

### Post by heather on 2007-03-29
> **mips said:**
> 7.04 beta maybe ? 6.10 was/is not that great.

i take your word for it
i will look for the beta or should i stay with 6.06 till alpha i out

---

### Post by mips on 2007-03-29
> **heather said:**
> i take your word for it
i will look for the beta or should i stay with 6.06 till alpha i out

If you have 6.06 or 6.06.1 then use it. 7.04 alpha has come and gone, the beta is out now, RC will probably follow soon.

---

### Post by heather on 2007-03-29
> **mips said:**
> If you have 6.06 or 6.06.1 then use it. 7.04 alpha has come and gone, the beta is out now, RC will probably follow soon.



Thanks

---

