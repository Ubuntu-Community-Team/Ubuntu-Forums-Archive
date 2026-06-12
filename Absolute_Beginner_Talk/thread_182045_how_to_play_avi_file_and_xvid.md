---
title: "how to play avi file? and xvid?"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-25
help please..anyone? do i use the supository thing?

---

### Post by matthew on 2006-05-25
This should help you.

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by frodon on 2006-05-25
You should read that : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

EDIT : matthew beats me to it ;)

---

### Post by edwardzafra on 2006-05-25
thanx guys..but any specifics? sorry to be pain but its my 2nd day in linux

---

### Post by mostwanted on 2006-05-25
Just install everything mentioned on the page. AVI is not a file format, but a container format which can have many kind of file types so there's no specific codec for it.

---

### Post by cskeide on 2006-05-25
[QUOTE=edwardzafra]help please..anyone? do i use the supository thing?[/QUOTE]

Alright, mate ;) You're from sydney right?

First of all, I'm assuming you are running version 5.10 aka breezy. If not, these instructions may not work. Also, did you manage to add extra repositories? I use my ISP's (iinet) ftp which is very fast and should work fine for you as well. If you were unable to change your sources list file you can use mine:

```
sudo gedit /etc/apt/sources.list
```

Replace the contents of the file with this:
```
deb http://ftp.iinet.net.au/pub/ubuntu/ breezy main restricted
deb-src http://ftp.iinet.net.au/pub/ubuntu/ breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.iinet.net.au/pub/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ftp.iinet.net.au/pub/ubuntu/ breezy universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.iinet.net.au/pub/ubuntu/ breezy-backports main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ breezy-backports main restricted universe multiverse

deb http://ftp.iinet.net.au/pub/ubuntu breezy-security main restricted
deb-src http://ftp.iinet.net.au/pub/ubuntu breezy-security main restricted
deb http://ftp.iinet.net.au/pub/ubuntu breezy-security universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu breezy-security universe multiverse
```

Now, save and close the file.

Then, in a terminal (Applications -> Accessories -> Terminal), run:```
sudo aptitude update && sudo aptitude dist-upgrade
sudo aptitude install totem-xine xine-ui gstreamer0.8-mad gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg
sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

After this you should be able to view most video formats, DVD's, and play mp3 music.

Hope this helps.

---

### Post by patrick295767 on 2006-05-25
my effortless multimedia.sh installation script could help you also ...

Greetings

---

### Post by edwardzafra on 2006-05-25
cskeide <=== you da man!

thanx yes its working. but why is my sound soft? i am running Power Book G4 an all volum is up. any idea?

---

### Post by manicka on 2006-05-25
[QUOTE=edwardzafra]
thanx yes its working. but why is my sound soft? i am running Power Book G4 an all volum is up. any idea?[/QUOTE]

there are several solutions that may help in this thread

[http://ubuntuforums.org/showthread.php?t=82539](http://ubuntuforums.org/showthread.php?t=82539)

---

### Post by cajunaggie on 2006-05-30
[QUOTE=edwardzafra]help please..anyone? do i use the supository thing?[/QUOTE]

I avoid supositories when I can. I much prefer oral pills or shots.;) 

*runs for cover*

---

