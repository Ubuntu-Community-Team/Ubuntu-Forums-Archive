---
title: "Annoying Media Change Alert"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-01-19
Everytime I run apt-get install (program), I get this annoying alert.
Media Change, please insert Xubuntu Alternative CD 6.06 (bla bla bla)
Is there something wrong with my depencendies?

(sorry for all of the newbieness here, I havn't used linux in a very long time, and even then, I really only dipped my feet in the water.)

---

### Post by %hMa@?b&lt;C on 2007-01-19
> **chris062689 said:**
> Everytime I run apt-get install (program), I get this annoying alert.
Media Change, please insert Xubuntu Alternative CD 6.06 (bla bla bla)
Is there something wrong with my depencendies?

(sorry for all of the newbieness here, I havn't used linux in a very long time, and even then, I really only dipped my feet in the water.)
post the output of
cat /etc/apt/sources.list
from terminal

---

### Post by meng on 2007-01-19
You probably have the CD as one of the software repositories, so that apt-get will look there first for packages. If you want to install everything from the internet, then:
sudo nano -B /etc/apt/sources.list

and look for the line with "cdrom" (should be at or near the top)
put a # in front of it (comment, will be ignored)
then save (ctrl-x)

sudo apt-get update

Bingo! You're done

---

### Post by chris062689 on 2007-01-19
Ah ok thank you very much!
I just used Synaptic Package Manager instead of doing that . :)
I'm looking around on how to install the dilo browser, and I've enabled community respatories, and still can't find it.
(NOTE: Instead of clutting the forums with my stupid questions, I'll just put them all in this thread)

---

### Post by meng on 2007-01-19
You sure you've enabled universe repositories? Should be in there.

---

### Post by chris062689 on 2007-01-19
Yes, and I've also reloaded.

---

### Post by meng on 2007-01-19
Better post your sources list.

---

### Post by chris062689 on 2007-01-19
# 
# deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted


# deb cdrom:[Xubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by meng on 2007-01-19
Any line that begins with 
# deb
or
# deb-src

is NOT recognized as a repository (it is commented out). Consider uncommenting those lines (not the cdrom one of course).

---

### Post by chris062689 on 2007-01-19
Ok thank you, one more question! ](*,) 
Right now, I only have two moniter resolutions, 800x600 and 640x840.
Both appear very, very small.
Is there a way I can get more choices?

---

### Post by meng on 2007-01-19
Try this
sudo dpkg-reconfigure xserver-xorg

and select more resolution options.

---

### Post by chris062689 on 2007-01-19
I tried that the first time, and it went to go autodetect screen resolution sizes, and on my screen appered gibberish (meaning the autotest failed), the desktop manager rebooted, and no settings were saved, last time, I told it NOT to autotest, and was able to select a few screen resolutions, but it came up with this error:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070119234512

---

### Post by meng on 2007-01-19
Okay, what sort of graphics card do you have?

---

### Post by chris062689 on 2007-01-19
*shrugs*

---

### Post by meng on 2007-01-20
Try:
lspci | grep VGA

---

### Post by chris062689 on 2007-01-20
lspci | grep VGA
0000:00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

Ok now what?

---

### Post by meng on 2007-01-20
What video driver did you select when you did the dpkg-reconfigure (I think it's the first question you have to answer)? Is it i810?

---

