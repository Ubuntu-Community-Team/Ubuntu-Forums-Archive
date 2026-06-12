---
title: "installing  libdvdcss2"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by manuleka on 2007-06-28
i followed this link to install  libdvdcss2 

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

after running:

sudo /usr/share/doc/libdvdread3/install-css.sh

it seems that totem movie player still can't play dvds :(

am i missing something here?

is there a way of viewing this libdvdcss2 if its installed already? or do i have to visit the /usr/share/doc/libdvdread3/install-css.sh file or folder?

---

### Post by overdrank on 2007-06-28
> **manuleka said:**
> i followed this link to install  libdvdcss2 

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

after running:

sudo /usr/share/doc/libdvdread3/install-css.sh

it seems that totem movie player still can't play dvds :(

am i missing something here?

is there a way of viewing this libdvdcss2 if its installed already? or do i have to visit the /usr/share/doc/libdvdread3/install-css.sh file or folder?

HI you might try this link it worked for me 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Or you could try automatix.:KS

---

### Post by compiledkernel on 2007-06-28
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by darkrose on 2007-06-28
Try adding the medibuntu repository
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

then you can install libdvdcss with
sudo apt-get install libdvdcss2

---

### Post by RomeReactor on 2007-06-28
Make sure all these packages are installed:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs mplayer w32codecs libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3
```
Did you install **totem-xine**?

---

### Post by manuleka on 2007-06-28
thanks guys it works now... i couldn't get one dvd to play tho for some reason.. i've returned it, but could it be a zone problem for that dvd i think, i can't remember what zone it was... or should these plugins make my dvd player zone-independent?

---

### Post by iver2435 on 2007-06-28
There is a package available called "setregion" available that lets you set your DVD player's region at the command line...I think that's the name of the command you run also.

---

