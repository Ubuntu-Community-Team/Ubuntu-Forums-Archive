---
title: "G4 Install Problems"
date: 2006-08-21
forum: Apple PPC Users
---

### Post by avro on 2006-08-21
I have downloaded Ubuntu 6.06 for my G4 Power Mac and burned the ISO image to a CD but when I go to startup disk, the CD does not show as a startup option ](*,)   . Any ideas of what is wrong? 

I would like to install and run it on a partition (formatted but no OS on that partition as of yet).

avro in Bruggen

---

### Post by Tofu on 2006-08-21
Did you put the CD in, then restart the Mac while holding down the 'c' key?
(the c button makes it load from the CD).

Otherwise, I had some difficulties with an older G4 Power Mac, which I wrote in an [earlier thread]("http://www.ubuntuforums.org/showthread.php?t=238510").

---

### Post by avro on 2006-08-21
Yes, I held down key C but it booted off the hard drive.  I got the Apple logo and then my normal desktop altho it did refuse to eject the CD because it was in use ](*,) .

avro

---

### Post by Tofu on 2006-08-21
That's strange... that OS X would refuse to eject the CD, because it is "in use".

Restart the machine again. If it doesn't restart, force it to restart...  there's a little button on the front panel of the G4 that will force a restart (it's the little button bottom-left with an arrow).

Immediately hold down the c key and keep it held down until you see some text on the screen.

---

### Post by 3rdalbum on 2006-08-21
The CD will never appear as an option in the Startup Disk control panel.

If you have trouble ejecting CDs, you might have File Sharing turned on and set to share removable media.

Insert the disc while Mac OS is running. Open it up. Are there a whole bunch of files and folders on there, or just the .iso file? If it's the latter, then you need to use the "Disc Image" function of Toast.

If it's the files and folders and it won't boot, then hold down Command-Option-O-F while you start up. Put in the CD, wait a little while, then type "boot cd" at the prompt.

If that doesn't work, try burning at a lower speed onto one of the discs that is made "for music".

---

### Post by avro on 2006-08-21
Thanks for the advice. I actually did not need any other software than what was included in OS X .  Rather than just copy the Disk Image, I needed to open Disk Utility on the Mac and then choose to burn the ISO disk image (I had previously been doing just a copy before burn #-o   and that was the problem).  I  then used a DVD for the burn and then held down the 'c key' on restart.  A couple of loading errors and some Unix prompts and I was up and running in about 2 minutes.  I still have not figured out how to install Ubuntu off the DVD (I am currently running it off the DVD)  but that should be relatively easy once I play around with it for a while.


avro in Bruggen

---

### Post by gmcgrillan on 2006-08-23
Hi there,

I had some difficulties with the standard version of Ubuntu and had to install the alternate version  - It worked a treat! This was after I used the  OS X Disk utily to burn the ISO though. It appears that lots of folks have had difficulty with the standard version and have subsequently used the "alternate" version to install.

I am still pretty new to Ubuntu - so I will do my best to answer any questions you have!

Gareth...

G4 Sawtooth, 10 Gb HD, 192 MB, Belkin F5d7000 Wireless Card !
Awaiting a bigger HD and more RAM!!

---

