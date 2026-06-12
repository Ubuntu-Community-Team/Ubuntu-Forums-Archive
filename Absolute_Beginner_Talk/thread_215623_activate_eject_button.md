---
title: "activate eject button"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Blur-king on 2006-07-14
Hi can anyone direct me to the package that will enable the cdrom eject button. I forgot where I install it from.   Thanks  :-k

---

### Post by ProjectGod on 2006-07-14
from the terminal. type:

eject -r

eject -tr 

the second one is for popping the tray back in. not actually a button but works better then the actual physical button on the cd rom drive. sometimes when you find that you cannot open the tray even when pressing the button on the drive 10000 times... just use the terminal... magick!

---

### Post by T700 on 2006-07-14
Automatix used to (see my sig), but there was some talk of removing that bit of the script, so I'm not positive if it still does.  You might check their feature list.

Paul

---

### Post by bluntu on 2006-08-09
I find it very STRANGE that I do not have control over my DVD-ROM's "Eject" button. Everytime I want to get my cd out I have to right click then "Eject".

This is BAD design. The user should have total control...

---

### Post by Psquared on 2006-08-11
new version of automatix does not enable the cd eject button - at least not for Kubuntu. not sure why but the only way i have found is using the eject commands in a terminal window. would love to find a way around that. its a pain in the you know what. :confused:

---

### Post by Blur-king on 2006-08-15
Hello, Try this found it in one of the forum and it work for dapper

This HOWTO is just for trick to make the cd eject by pressing the eject button on the cd drive which has been included into dapper, but this is how to do it on breezy

Open Terminal and type

Code:
sudo sysctl dev.cdrom.lock=0

now your cd can be ejected by simply clicking on the eject button but if you restart it will no longer be available, to make it permanent, 
then type

Code:
sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

Now it will be permanent.  ;)

---

