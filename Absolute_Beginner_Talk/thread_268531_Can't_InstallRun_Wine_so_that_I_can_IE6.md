---
title: "Can't Install/Run Wine so that I can IE6"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by newbie8 on 2006-09-30
I've gone over the "How tos" regarding the dowloading, extracting, installation and running of Wine so that I can surf using IE6 but it simply does not work.

Is there an easy process to install Wine?

What if I have Wine but can't run it in the terminal? How would I know?

Thanks!

---

### Post by llamakc on 2006-09-30
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Has always worked wonderfully for me.

---

### Post by lavikl on 2006-09-30
I tried to go by the instructions as mention in the link that was posted.
When i rub the "apt -get update" i get the following message

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) breezy/main Packages
Errhttp://wine.budgetdedicated.com breezy/main Packages
  404 Not Found

I'm using Dapper version, so I tried to change "breezy" into "dapper" in the "sources.list" file. and then i got this message :

Errhttp://wine.budgetdedicated.com dapper/main Packages
  404 Not Found

needless to say that the rest of the installation of IE didn't work...

help anyone ?!

---

### Post by thephantomlinguist on 2006-09-30
Try this (from WineHQ):

> Installing from the WineHQ APT Repository with Synaptic:

To install Wine from the WineHQ APT repository, you need to configure APT to look in the right place for the Wine packages. On Ubuntu systems, and those using the Synaptic Package Manager, this can be done easily by opening up Synaptic (System->Administration->Synaptic Package Manager) and selecting Settings->Repositories. Then click add, select custom, and enter one of the following:

For Ubuntu Dapper (6.06):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Then, simply click reload and search for the package 'wine' for installation. If you already have a 'wine' package installed, selecting mark all upgrades should update Wine to the newest version.

Looks like you had the right idea, you just typed it wrong.

Hope this helps!

---

### Post by lavikl on 2006-09-30
Thanks for the help but unfortunatly i tried that as well...
when Reload through Synaptic I get a message saying :

[http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/dapper/main/binary-amd64/Packages.gz:) 404 Not Found

any ideas for an alternative repositories ?

---

### Post by thephantomlinguist on 2006-09-30
If I'm not mistaken the wine.budgetdedicated.com repo is really for the bleeding edge. I'm not sure IEs4Linux requires it. In other words, you can probably get away with using the official repositories to install wine.

Hope this helps!

---

### Post by lavikl on 2006-09-30
I Searched Synaptic for Wine and i found :
libwine
libwine-dev
winefish

the first 2's description say :
"Microsoft Windows Compatibility Layer (Dummy Package)"

so i guess it's not it.
the 3rd is something that has to do with bluefish.

I have enabled universe and multi-universe repositories.

would appriciate more help... ;)

---

### Post by thephantomlinguist on 2006-09-30
Here's my sources.list

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

and what I get when I search for wine

> $ apt-cache search wine
kftpgrabber - KDE FTP client
libwine - Microsoft Windows Compatibility Layer (Dummy Package)
libwine-dev - Microsoft Windows Compatibility Layer (Dummy Package)
tellico - collection manager for books, videos, music
wine-dev - Microsoft Windows Compatibility Layer (Development files)
winefish - LaTeX Editor based on Bluefish
wine - Microsoft Windows Compatibility Layer (Binary Emulator and Library)

It might be helpful for comparison.

Hope this helps!

---

### Post by gertlm on 2006-09-30
hello. why you just add in /etc/apt/source.list 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
then:
sudo apt-get update
sudo apt-get automatix

In automatix at the bottom of the list you can install wine. remember when finish to install to configure with winecfg

I hope this help you

---

### Post by podunk on 2006-09-30
[http://www.getautomatix.com/](http://www.getautomatix.com/)

You won't learn a thing but it works. :-) Very easy instructions on installing automatix, and wine is close to the bottom.

Be suire to exit automatix before you run the wine configuration!

Why do you want to run IE anyyway? :biggrin:

---

### Post by newbie8 on 2006-09-30
I am already in the part from page 145 of the "Official Ubuntu Book"

alt f2 then type winecfg

after that, a window pops with some choices of .exe file which don't seem to work again.

I simply like to check IE6 on some sites.

---

### Post by DougieFresh4U on 2006-09-30
Hi newbie8, I don't mean to butt in on your thread, I have been trying to get wine for 2 months now. I just followed what was posted in your thread and ended up w/this::         ~$ winecfg
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory                            I do not know what any of this means and I know it is of no help to you, Hopefully someone will get us on the right path. Anyone?

---

### Post by gertlm on 2006-09-30
I have the same problem at first I must to install the this:

libjack0.100.0-0 - JACK Audio Connection Kit (libraries)
libjack0.100.0-dev - JACK Audio Connection Kit (development files)
libjackasyn-dev - Development files for libjackasyn
libjackasyn0 - The Asynchrounous JACK Library

and the error of libjack is gone, but the file or directory /dev/snd/seq is missing still.

I think is about somthing refer to the sound card but if you set in the audio tab the use of "alsa driver" you have sound emulation on.

btw: this is only a sound issue.

---

### Post by lavikl on 2006-10-04
sorry to bother again but i couldn't find Wine in automatix...
I changed my souces.list file according to what people suggested (only diffrence is that instead of us.ubuntu... it's au.ubuntu....) but synaptic couldn't find wine in the repositories.
After that I installed Automatix but wine is not in my list !

I would appriciate more suggestions.
might it be that there's no wine version for amd64 and that's the reason i can't find it in any repository ?

---

### Post by pay on 2006-10-04
Wine doesn't compile correctly for 64bit linux. Just install the 32bit version. I here people that have had success with it.

---

### Post by lavikl on 2006-10-04
where can i find the 32but version if it's not in any list of my repositories ?

---

### Post by pay on 2006-10-04
It's here
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by Frak on 2006-10-04
Didn't you install wine from synaptics?
and if so, use IE4Lin.

---

### Post by Brownedwg89 on 2006-10-04
use this tutorial for installing wine on 64-bit Ubuntu
[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

---

### Post by handy on 2006-10-05
After you have installed Wine with Automatix, run [WineTools]("http://www.von-thadden.de/Joachim/WineTools/") to install IE.

Install everything in WineTools, & you should have a reliable (cough!) IE.

Just don't install DVDshrink, because for some reason IE interferes with DVDshrink's display? :confused:

By the way, life is much simpler for those of us who run 32-bit...

---

