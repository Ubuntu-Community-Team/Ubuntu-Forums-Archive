---
title: "Trouble getting Ubuntu to install on Mac G3"
date: 2006-10-16
forum: Apple PPC Users
---

### Post by tbar3 on 2006-10-16
:-k ](*,) I'm new to both Linux and Macs... i was given a Mac G3 slot load, 350 MHz that currently has OS 9 installed. i don't really care for this, so i was going to put Linux on it. i DLed the Live CD, and got to the splash screen where Ubuntu is loading, and then the screen goes black, and the CD just keeps spinning in the CD-Rom... i've tried a couple different CDs just in case i burned a bad one the first time, both with the same result. i'd really like to get this up and running... any ideas as to what may cause this, or (preferably) how to fix it? my only current guess is bad CD-Rom, but, i'm not sure where to start to replace that... is there a way to install from a Flash drive? i could do that, if it's possible, but again, i'm new... any help is appreciated. thanks in advance!

---

### Post by bodycoach2 on 2006-10-16
More than likely, the G3 doesn't have enough memory to run the live CD. I've put Xubuntu on two Bondi style iMac G3, 333 Mhz, 160 MG of memory, and 6 gig hard drives. Here's what I recommend:

Choose Xubuntu over Ubuntu. Download the install CD, not the live version. Make sure you download and burn the 6.06.1. For many people, the 6.06 PPC version would not load up on many G3's.

Xubuntu is an excellent distro, and fast enough to actually use on the iMac G3's.

> **tbar3 said:**
> :-k ](*,) I'm new to both Linux and Macs... i was given a Mac G3 slot load, 350 MHz that currently has OS 9 installed. i don't really care for this, so i was going to put Linux on it. i DLed the Live CD, and got to the splash screen where Ubuntu is loading, and then the screen goes black, and the CD just keeps spinning in the CD-Rom... i've tried a couple different CDs just in case i burned a bad one the first time, both with the same result. i'd really like to get this up and running... any ideas as to what may cause this, or (preferably) how to fix it? my only current guess is bad CD-Rom, but, i'm not sure where to start to replace that... is there a way to install from a Flash drive? i could do that, if it's possible, but again, i'm new... any help is appreciated. thanks in advance!

---

### Post by tbar3 on 2006-10-16
thanks.. i'll try that out tonight... just so ya know.. i've got 256 ram in the machine.. i believe it is a 6 gig hdd (i haven't played around with it much...), so i wouldn't imagine the RAM would've been the issue, but that's why i'm the n00b, i guess :) thanks..

---

### Post by bodycoach2 on 2006-10-16
256 is a good enough amount of RAM, but the G3's are 'persnickity' so-to-speak. With the speed of the processor, Xubuntu, or even nUbuntu (fluxbox version) will be a better, and faster, choice.

> **tbar3 said:**
> thanks.. i'll try that out tonight... just so ya know.. i've got 256 ram in the machine.. i believe it is a 6 gig hdd (i haven't played around with it much...), so i wouldn't imagine the RAM would've been the issue, but that's why i'm the n00b, i guess :) thanks..

---

### Post by taurus on 2006-10-16
Will move this one over to Mac section since there are more Mac users hanging out there...  ;)

---

### Post by 3rdalbum on 2006-10-17
Follow the directions on this thread:

[http://www.ubuntuforums.org/showthread.php?t=75604&highlight=iMac+blank+screen](http://www.ubuntuforums.org/showthread.php?t=75604&highlight=iMac+blank+screen)

---

### Post by tbar3 on 2006-10-18
tried this, too... i can get to the console, i can edit the file to get the refresh/etc as specified... only problem is i was booting from the LiveCD so as far as saving those specs to the CD... uh uh... i also tried the xUbuntu, but i think (again) the CD i burned was bad, so i'll have to try that again later... i tried usin' the i386 LiveCD on my PC, and it worked flawlessly, so i dunno.. i think the mac's drive may just be shot... i'm thinkin' about splurgin' for the $15 replacement... any other ideas before i spend $???

---

### Post by JP_Godfrey on 2006-10-18
That's how I got it to work on my iMac G3.  As to saving to the cd, it doesn't.  It saves to the RAM Disc that the system is running from.  This does mean that you have to change the file every time you boot from the cd.

---

### Post by tbar3 on 2006-10-18
pardon the ignorance... but once i change the file, save it, etc, how do i get back to the desktop from the console?

---

### Post by linear on 2006-10-18
Assuming this is the Ubuntu Dapper (Gnome) LiveCD:

**sudo killall -HUP gdm**

(If it's Kubuntu replace gdm by kdm.)

---

### Post by tbar3 on 2006-10-18
awesome!! thanks so much!!! now i can actually use this mac to potential! :)

---

