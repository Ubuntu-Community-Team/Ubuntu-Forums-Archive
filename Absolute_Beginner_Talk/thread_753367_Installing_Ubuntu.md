---
title: "Installing Ubuntu"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by david cowan on 2008-04-12
Hi,
Just spent the entire day trying to install Ubuntu. My hard drive is quite full so I have tried to install it to a 4GB memory stick (I know this is fairly small but should be adequate. I am installing from a purchased live CD and the installation seems to go OK. It did seem to work for a time and then stopped working. Every time I try to install it seems toinstall fine but gives an error or hangs when I try to boot. The last time the error was "[35.275502] Kernel panic- not syncing:VFS Unable to mount root fs on unknown-block(0,0)."

I was led to believe that these sort of problems were peculiar to windows???!!!!

Any help or suggestions greatly appreciated.

Thanks,

David Cowan

---

### Post by Crafty Kisses on 2008-04-12
You're getting a kernel panic it looks like. What are your system specs?

---

### Post by david cowan on 2008-04-13
I'm trying to install Ubuntu 7.10.

---

### Post by david cowan on 2008-04-13
My compuer is a 2.5GHz pentium of about 2-3 years vintage. It has a 40GByte hard drive (about half full). Not sure exactly what other specs you need.

Thanks

---

### Post by Michael.Godawski on 2008-04-13
Here are two tutorials on how to install Ubuntu on a flash drive:
[LIST]
[*][http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)
[*][http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)
[/LIST]

But first make sure your CD is without defects. You can check the CD during th booting process.
Did you manage to boot into the Live CD session? If you open the terminal and run 
```
sudo lshw
```
to list your hardware devices

---

### Post by david cowan on 2008-04-13
I did try to check that the CD was OK. What happened was that the Screen displays Ubuntu in big letters at the top and then a bar indicating progress accross the screen eventually the bar gets completed without incident and the computer just sits there. Several hours later I came back to a blank screen. Not sure whether this indicates a fault or not.
I had assumed that since the CD apparently installs UBUNTU that this would indicate that it might not be the source of the problem!!!

I will try to boot the computer again from the CD later today and report what hardware it thinks exists.

---

### Post by Michael.Godawski on 2008-04-13
Perhaps it is some compatibility issue with your graphic card. You can try installing with the Alternate CD in text mode. It usually solves many compatibility issues.

Alternate CD:[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)
Alternate CD Installation Guide: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by david cowan on 2008-04-14
Hav attached a file with the system config obtained with the command you suggested.

Thanks,

---

