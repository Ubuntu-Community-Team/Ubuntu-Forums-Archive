---
title: "configure alsa?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by thelegionnaire on 2007-06-15
so i how do i set up the alsa drivers?

---

### Post by thelegionnaire on 2007-06-15
bumpity bump bump

---

### Post by BHelts on 2007-06-15
what kind of sound card to you have?

---

### Post by BHelts on 2007-06-15
Update to the latest version of alsa

{These instructions do not interfere with the Ubuntu package structure or other kernel modules - in other words, the changes seem drastic however they are simply adding greater functionality to an existing kernel module

      Install the required tools
```

sudo apt-get install build-essential ncurses-dev
```

      Install your kernel headers

```
sudo apt-get install linux-headers-`uname -r`
```  

      Download the latest version of alsa from Alsa project (driver, library, and utils) to a directory.
[alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2")
[alsa-lib]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14a.tar.bz2")
[alsa-utils]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2")

      Setup installation directories

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14rc4.tar.bz2
sudo tar xjf alsa-lib-1.0.14rc4.tar.bz2
sudo tar xjf alsa-utils-1.0.14rc4.tar.bz2
```

      Compile and install alsa-driver

```
cd alsa-driver-1.0.14rc4
sudo ./configure
sudo make
sudo make install
```

      Compile and install alsa-lib

```
cd ../alsa-lib-1.0.14rc4
sudo ./configure
sudo make
sudo make install
```

      Compile and install alsa-utils

```
cd ../alsa-utils-1.0.14rc4
sudo ./configure
sudo make
sudo make install
```

      Reboot

much of this was borrowed from [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto").
It will install the latest version of alsa.

---

### Post by KIAaze on 2007-06-27
Should be:
> ./configure
make
sudo make install

and not:
> sudo ./configure
sudo make
sudo make install

"sudo" should be avoided when not necessary.

edit:
Mmh, it seems you build in "/usr/src/alsa". In that case, the sudo is indeed necessary.
But why build it there?
I'll have to try it on my PC. If it can be avoided, I think it's better to avoid it.

---

### Post by Anarchy965 on 2007-06-27
Where do I have to download the tar.bz2 files to?

---

### Post by KIAaze on 2007-06-28
If you want to follow his tutorial exactly, you'll have to download them to ~/downloads/ (this means /home/<username>/downloads).

---

### Post by CityofAsh on 2007-07-02
Build it where ever just login as root.

```
sudo su
```

then enter your root password.

No need for sudos..

~City

---

### Post by KIAaze on 2007-07-03
When you use sudo, the password is stored for a while anyway by default, so it's better to use sudo, since it only gives root permissions for one command which is safer.

---

### Post by CityofAsh on 2007-07-03
Yeah i hear ya about safer. I always have 1 root console in text mode open. Hell i know people who startx as root :D and they have no problems.

---

### Post by Pyroja on 2008-07-04
Hey folks. I'm a newb when it comes to these things <.< I was following those wonderful directions a few posts back, but unfortunately, make spit some errors back at me.. Wondering if any of ya'll could help me out?

make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.14'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/alsa/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2

Thanks in advance!

---

### Post by KIAaze on 2008-07-04
Is that the output of "make" or "make install"?

If it's "make", then you are doing something wrong: It shouldn't be running in /usr/...

You should run "make" as a normal user somewhere in your home directory.
Once this is passed without errors, you can run "sudo make install".

If the error message is from "make install", I don't know what causes it.

But why are you trying to install alsa 1.0.14?

The latest version from the repositories (for hardy) is 1.0.16.
[http://packages.ubuntu.com/hardy/alsa-base](http://packages.ubuntu.com/hardy/alsa-base)
And the latest stable version available is also 1.0.16:
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

The instructions above are probably still correct but contain outdated links. You should get the necessary files directly from here: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

But why do you need to install alsa from source? Are you having sound problems with pulseaudio?
It's easier to just run:
```
sudo apt-get install alsa-base
```
if you want to install alsa.

---

### Post by KIAaze on 2008-07-04
I changed the instructions given by BHelts earlier.
Instead of configuring and building as root, you should do it as a normal user in your home directory.
I believe it's better that way:

Update to the latest version of alsa

{These instructions do not interfere with the Ubuntu package structure or other kernel modules - in other words, the changes seem drastic however they are simply adding greater functionality to an existing kernel module

      Install the required tools
```

sudo apt-get install build-essential ncurses-dev
```

      Install your kernel headers

```
sudo apt-get install linux-headers-`uname -r`
```  

      Download the latest version of alsa from Alsa project (driver, library, and utils) to a directory.
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
In the following, replace <version> with the version you downloaded. (or easier: press tab twice to autocomplete the name.)

      Extract folders:

cd <directory where you downloaded the files>
tar xjvf alsa-driver-<version>.tar.bz2
tar xjvf alsa-lib-<version>.tar.bz2
tar xjvf alsa-utils-<version>.tar.bz2[/CODE]

      Compile and install alsa-driver

```
cd alsa-driver-<version>
./configure
make
sudo make install
```

      Compile and install alsa-lib

```
cd ../alsa-lib-<version>
./configure
make
sudo make install
```

      Compile and install alsa-utils

```
cd ../alsa-utils-<version>
./configure
make
sudo make install
```

      Reboot

Note:
```
./configure
make
sudo make install

```
is the standard way of compiling from source.
More info here:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
(yes, you could use "sudo checkinstall" instead of "sudo make install"...)

---

### Post by Pyroja on 2008-07-04
Ah, ok, it all makes sense now. My mistake!

I'm configuring alsa because.. Well, I've really no idea how to use any of the sound stuff, and I was trying to get mu audio output from the SPDIF jack on the SB Live card in this system, so that I can pick up from the SPDIF input on another system (Running WinXP, which I am more than capable with, unlike Linux, where I'm still a newb).

So I s'pose I oughta search around for some Pulse audio tutorials or somesuch thing now...

---

### Post by KIAaze on 2008-07-05
I don't even know what SPDIF is. ^^'
But from a quick google search, I think you might be able to solve your problem very easily:
[http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF](http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF))

From reading it quickly, it seems all you have to do is unmute/activate the IEC958 mixer.

You can do this by using alsamixer or the Gnome volume control.

_Solution 1:_
The Gnome volume control is most likely already installed.
Just right-click on your volume applet and select "open volume control".
Alternatively, you could also launch it with the "gnome-volume-control" command.

Once it's open, click on "Preferences" and check the box next to IEC958.
Close preferences, go to the "Switches" tab and check the box et voilà!

_Solution 2:_
alsamixer can easily be installed by running:
```
sudo apt-get install alsa-utils
```

Then just run it, move to IEC958 using the arrow keys and unmute it by pressing "m".
Press escape to exit.

**_Some more info of interest:_**
_Installing software:_
Just in case you haven't been there yet:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

_Pulseaudio:_
[Pulseaudio]("http://www.pulseaudio.org/") is the new sound system used since Ubuntu 8.04. It apparently creates a virtual device used by [ALSA]("http://www.alsa-project.org/main/index.php/Main_Page"), [OSS]("http://www.opensound.com/") and [ESD]("http://www.tux.org/~ricdude/overview.html") (whatever those things are).
It allows having different volume settings for each application among other things.

_Ubuntu Studio:_
[Ubuntu Studio]("http://ubuntustudio.org/") is a special version of Ubuntu aimed at multimedia artists.
You can install it without reinstalling by installing all the *ubuntustudio* packages in synaptic:
```
ubuntustudio-audio - Ubuntu Studio Audio Package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins Package
ubuntustudio-controls - Ubuntu Studio Controls is a small app that changes A/V settings.
ubuntustudio-default-settings - Default settings and artwork for the Ubuntu Studio desktop
ubuntustudio-desktop - Ubuntu Studio Desktop Package
ubuntustudio-gdm-theme - Ubuntu Studio - GDM theme
ubuntustudio-graphics - Ubuntu Studio graphics Package
ubuntustudio-icon-theme - Ubuntu Studio Icon theme
ubuntustudio-look - Ubuntu Studio look
ubuntustudio-menu - Menu for Ubuntu Studio
ubuntustudio-screensaver - Ubuntu Studio screensaver
ubuntustudio-sounds - Ubuntu Studio's GNOME audio theme
ubuntustudio-theme - Ubuntu Studio look - GTK and Metacity theme
ubuntustudio-video - Ubuntu Studio video Package
ubuntustudio-wallpapers - Ubuntu Studio - Wallpapers
usplash-theme-ubuntustudio - Usplash theme for Ubuntu Studio

```
Of course you don't have to install all of them (ubuntustudio-controls seems most interesting).

[B]Important:
Ubuntu Studio comes with a realtime kernel instead of the standard kernel. This can be an issue with some proprietary drivers.[/B]
(I had problems with a wifi driver for example.)

---

### Post by hudarsono on 2008-07-14
I also tried to install alsa-1.0.14 since my alsa-1.0.16 have no sound

There is another forum that suggest install 1.0.14. By the way, I have downloaded source to ~/Desktop , then run
#./configure --with-cards=hda-intel
#make 

but got this error to
[HTML]make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/hudarsono/Desktop/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/hudarsono/Desktop/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/home/hudarsono/Desktop/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/home/hudarsono/Desktop/alsa-driver-1.0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [compile] Error 2
[/HTML]

I've already run make on home directory, any suggestion?

---

### Post by KIAaze on 2008-07-17
> **hudarsono said:**
> 
There is another forum that suggest install 1.0.14. By the way, I have downloaded source to ~/Desktop , then run
#./configure --with-cards=hda-intel
#make 

Could you tell me where this was suggested?

I think your problem comes from the fact that alsa 1.0.14 is not compatible with your kernel or compiler (gcc/g++) version.
At least that what's a few Google results suggest. (Personally, I don't understand the error message at all.)

This one was the most interesting:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463001](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=463001)

Maybe you should create a new post for your sound problem.
Don't forget to specify the sound card you have and post the output of this command:
```
lspci -v
```
(You can limit it to the part concerning the sound card of course. ;) )
_______________

> I've already run make on home directory, any suggestion? 
That's useless.
The "make" command only works where a "Makefile" is. That's simply a text file named "Makefile" (or "makefile" or "GNUmakefile").

So you have to run it in the extracted source folder otherwise you'll get this message:
```
make: *** No targets specified and no makefile found.  Stop.
```

Advanced info: To specify a Makefile with a special name use "make -f <filename>".

---

### Post by M4rotku on 2008-07-19
I followed this guide to try and get my microphone to work.  It didn't get the mic working, so that must be another problem, but now I'm having problems with Amarok and web pages that have sound.  Is there any way that I can downgrade to my previous version of alsa?

---

### Post by KIAaze on 2008-07-23
Sorry for the late reply.

There is a possibly easy way to downgrade alsa.
Just remove the alsa package using "sudo apt-get remove <package>" and then download and install the older version from [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

However, you may run into dependency problems. (That's why I said "possibly easy")

Also, there are several ALSA packages: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=alsa](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=alsa)

I suppose you would need to downgrade alsa-base, alsa-firmware-loaders, alsa-oss,  alsa-tools, alsa-tools-gui,  alsa-utils.

Installing alsa v1.0.14 from source unfortunately seems to be a bit problematic and I don't have time to figure it out right now.

---

