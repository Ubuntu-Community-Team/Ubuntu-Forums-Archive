---
title: "Can't play video files.............."
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Harshana on 2008-01-30
Hi Everybody...............

I installed ubuntu 7.10.
Mplayer can't play any video file which play in windows media player(DAT, MPEG, MP3, WMV etc....).

I know that mplayer must update.But i don't hava an internet connection to my home computer & i"m using a pen drive.
:(
Please help me to update Mplayer & other applications in ubuntu.

I'm totally new to open source softwares.

Please..........

Thank you very much.........

---

### Post by oedha on 2008-01-30
if you dont have internet connction at home....it means you have to install gstreamer package per package....they are 37 packages.....

or create a repo cd by yourself.......

or use Lnux mint......the gstreamer installed by default

~E~

---

### Post by JoshuaRL on 2008-01-30
If you have Linux on a computer that is connected you can install APTonCD.  It will gather all the dependencies you need and put them on a disk to run from your computer.

But what you really need is a package named ubuntu-restricted-extras.  That will install all the needed codecs to run the videos you want.

You could try opening Synaptic and check that package for installation.  When you do, it will tell you if any other packages are needed. (Dependencies)  Write those down and then from a internet-enabled computer go to packages.ubuntu.org and download all those and either burn those to a disk or a pendrive.  Then install those on your computer.  That *should* fix it, but the dependencies may have dependencies.  So just take it one step at a time.

---

### Post by mikeyphi on 2008-01-30
> **Harshana said:**
> Hi Everybody...............

I installed ubuntu 7.10.
Mplayer can't play any video file which play in windows media player(DAT, MPEG, MP3, WMV etc....).

I know that mplayer must update.But i don't hava an internet connection to my home computer & i"m using a pen drive.
:(
Please help me to update Mplayer & other applications in ubuntu.

I'm totally new to open source softwares.

Please..........

Thank you very much.........

If you have access to a computer with Internet access - try the package 'aptoncd'
that will allow you to download updates etc, burn to CD/DVD and install on your system

If you are runnning Ubuntu via a pendrive - you can make that drive 'persistent' look at this guide: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

You will then be able to run your system on (almost) any computer that can boot from pendrives.

---

### Post by oedha on 2008-01-30
question : aptoncd needs files from /var/cache/apt/archives right ??
and harshana just install the unit.....can she use aptoncd too ?

regards;
~E~

---

### Post by Harshana on 2008-01-30
How install gstreamer packages & how can i find them ?
I'm absolutely new to this........

Thanks.....

---

### Post by JoshuaRL on 2008-01-30
Gstreamer is another media player.  You need the correct codecs.

You need the package named:

ubuntu-restricted-extras

---

### Post by Harshana on 2008-01-30
Actually i don't know that she can use it or not.My computer has a cd rom.

---

### Post by Harshana on 2008-01-30
How can i find ubuntu-restricted-extras ?

thanks.....

---

### Post by JoshuaRL on 2008-01-30
I kind of explained it some in my first post, but it really depends on what you want to do.

Either you can try APTonCD, a linux app that lets you put packages on a CD for a computer that doesn't have the internet, or you can try to do exactly that manually.

APTonCD will be much easier, but has to be run from a Linux computer.  However, it will work, I'm 99% sure.  It's a really great app.

If you go to packages.ubuntu.org then you can search on there for the packages you need and burn them to a disk.  That may also work.  If you decide to to that, I would suggest you go into Synaptic on the non-internet computer and search for the packages needed.  When you mark them for installation, it will list others that will need to be installed also.  Make sure you download and burn all of those to the same CD.  You could also put those on a pen drive.  Basically, you would be trying to do what APTonCD does automagically, but manually.

---

### Post by Harshana on 2008-01-30
Thank you very much.I'll try it & reply you.

Thanks again.

---

