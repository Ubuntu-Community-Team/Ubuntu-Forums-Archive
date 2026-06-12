---
title: "How to use WINE???"
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by Robroy11976 on 2005-11-23
Hi .. anybody here could help me how to use WINE???

---

### Post by Grimoire on 2005-11-23
What exactly do you need help with? Installing wine or how to use it?

---

### Post by Robroy11976 on 2005-11-23
Actually ... both !!! I tried to install wine thru Synaptic package manager which it installed wine ... and i think it was libwine .... Is it done? or do i have to install anymore packs???  Then after that, i don't know how to use it

---

### Post by Grimoire on 2005-11-23
If you used Synaptic then it should be installed fully and I don't believe you need anything else to run it!

Once you have it installed the easiest thing I've found is to install xwine (a GUI for wine) by using

```
 sudo apt-get install xwine
```

Then run from a terminal 

```
 xwine 
```

Simply use Start>Launch to run .exe programs.

Also, I believe that .exe files are automatically associated with wine when you install it so if you simply double click on an exe in Nautilus it should run automatically with wine.

---

### Post by Robroy11976 on 2005-11-23
I did install wine already ... but i can't locate the xwine in the synaptic list ... i just tried to download it manually.  Any repositories where i could download xwine????

---

### Post by Grimoire on 2005-11-23
Here is my sources list:

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

deb http://download.videolan.org/pub/videolan/debian sarge main
     
deb-src http://download.videolan.org/pub/videolan/debian sarge main

```

Not sure which repository it's in - probably the multiverse ones at the beginning. Just in case you aren't sure how to edit your sources:

In a terminal type

```
sudo gedit /etc/apt/sources.list
```

Edit your sources appropriately, save and then run 

```
sudo apt-cache search xwine
```

And see if it turns up!

---

### Post by Grimoire on 2005-11-23
Just remembered - after you change your sources remember to run

```
sudo apt-get update
```

Before running the search!

---

### Post by Robroy11976 on 2005-11-23
Ok thanks .. i'll itry it out now

---

### Post by Robroy11976 on 2005-11-23
More or less same sources as me ... except that you're running on breezy while i'm on 5.04 version

---

### Post by Robroy11976 on 2005-11-23
I just download xwine manually instead .. but i'm having problems compiling it since it requires build essential package which needs cdrom to be installed ... Since my current cdrom is damage ... how could i install build essential without searching for the cdrom drive and just download from the web???

---

### Post by etc on 2005-11-23
Wine Devs have been saying not to use xwine, the latest wine comes with winecfg.

---

### Post by Grimoire on 2005-11-23
1. You can get build-essential from apt-get with 

```
sudo apt-get install build-essential
```

2. It may be easier to get xwine like this:

Download the rpm from 

[http://freshmeat.net/redir/xwine/18804/url_rpm/xwine-1.0-1.i586.rpm](http://freshmeat.net/redir/xwine/18804/url_rpm/xwine-1.0-1.i586.rpm)

In a terminal:

```
sudo apt-get install alien
```

Once alien has installed

```

cd <path to where you downloaded the rpm>
sudo alien -i <name of rpm>.rpm

```

This will generate a .deb file in the same location. Install this by using

```
sudo dpkg -i <name of deb file>.deb
```

And that should work!

---

### Post by Grimoire on 2005-11-23
> Wine Devs have been saying not to use xwine, the latest wine comes with winecfg.

Haven't heard about this - I've been using xwine and it's been fine but if there is another better way to use wine I'm all ears! :)

---

### Post by xelink on 2005-11-24
I just figured this out right now, I could be wrong, but...


[QUOTE=http://help.ubuntu.com/starterguide/C/faqguide-all.html#addingbackports]2.4.	

How do I add backports?
	

Backports are newer versions of applications made available for the current stable release of Ubuntu.

   1.

      Start Synaptic by selecting System->Administration->Synaptic Package Manager from the desktop menu system.
   2.

      In Synaptic choose Settings-> Repositories.
   3.

      Click on Add and then Custom.
   4.

      Paste the following line into the box:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

   5.

      Click Ok and then click Yes when it asks you to reload. Backports is now available.[/QUOTE]

[QUOTE=ign]sudo dpkg-reconfigure xserver-xorg[/QUOTE]

seems to work...

---

### Post by bengtfalke on 2005-11-24
Does anybod have a link to where I can download Internet Explorer 5.5. I can only find version 6....
regards/falke

---

