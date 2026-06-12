---
title: "Can't play mp3 with amarok..."
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by ckarymesogeios on 2007-08-27
Dear all, As I am a new user of ubuntu linux, I was told that **amarok** is one of the best media players.The problem using it ,is that I cannot play any mp3 or wma files. The message that appears is the following "no mp3 support" even though other programs seem to play mp3's.Any help,\?

---

### Post by Perfect Storm on 2007-08-27
You might want to read up on this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mysticmatrix on 2007-08-27
Use 

```
sudo apt-get install libxine1-ffmpeg libxine-extracodecs
```

This will install all needed codecs

---

### Post by ckarymesogeios on 2007-08-27
Thnx for the help...

---

### Post by daimyo505 on 2008-01-10
Hello I'm another Linux noob. I'm trying to get Amarok to play mp3's but have failed several times.

I am running ubuntu gutsy gibbon 7.10
mounted my ntfs drive and copied my mp3s to the linux desktop (I use the other HD as a backup)
I started Amarok, got the error saying not able to play mp3

I tried to install mp3 support through Amarok. It said to restart Amarok. I did and still no mp3 support.
I tried the commands:
/usr/lib/amarok/install-mp3
sudo apt-get install libxine1-ffmpeg
sudo apt-get install libxine1-ffmpeg libxine-extracodecs

in all the cases I get errors. Like package has no installation candidate.
In the add/remove programs I see that libxine is already installed.

Any suggestions? Thanks in advance.

---

### Post by GavinZac on 2008-01-10
use Exaile, its better and made for Gnome.

run these commands to install the medibuntu codecs

> **LowSky said:**
> ```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

```
sudo apt-get install w32codecs
```

search more!

---

### Post by monte48lowes on 2008-01-10
You will have to enable the repositories. [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Mike

Edit: Happens every time. Someone posts a better answer while I am typing mine.

---

### Post by billgoldberg on 2008-01-10
> **daimyo505 said:**
> Hello I'm another Linux noob. I'm trying to get Amarok to play mp3's but have failed several times.

I am running ubuntu gutsy gibbon 7.10
mounted my ntfs drive and copied my mp3s to the linux desktop (I use the other HD as a backup)
I started Amarok, got the error saying not able to play mp3

I tried to install mp3 support through Amarok. It said to restart Amarok. I did and still no mp3 support.
I tried the commands:
/usr/lib/amarok/install-mp3
sudo apt-get install libxine1-ffmpeg
sudo apt-get install libxine1-ffmpeg libxine-extracodecs

in all the cases I get errors. Like package has no installation candidate.
In the add/remove programs I see that libxine is already installed.

Any suggestions? Thanks in advance.

Download the following package from synaptic package manager.

**amarok-xine** from the medibuntu repositories, I think that should do the trick.

If you don't have the meditbuntu repositories go to synaptic package manager. Press "settings -> repositories -> third party software -> add" and give this in:

```
http://packages.medibuntu.org/
```

Then hit the reload button and search for it amarok-xine.

---

### Post by stchman on 2008-01-10
> **ckarymesogeios said:**
> Dear all, As I am a new user of ubuntu linux, I was told that **amarok** is one of the best media players.The problem using it ,is that I cannot play any mp3 or wma files. The message that appears is the following "no mp3 support" even though other programs seem to play mp3's.Any help,\?

This will get MP3s up an going on your system.

```
sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse


```

---

### Post by daimyo505 on 2008-01-10
I currently don't have internet at my home where the linux machine is. I am using my work computer to ask the questions on the forum. (windows machine)

I don't believe I will be able to get the internet for some time. Hence I cannot do the internet updates. :(

Is there another way to get the updates like downloading them to a USB stick and then putting them on Linux?

Thanks again.

---

### Post by GavinZac on 2008-01-10
> **daimyo505 said:**
> I currently don't have internet at my home where the linux machine is. I am using my work computer to ask the questions on the forum. (windows machine)

I don't believe I will be able to get the internet for some time. Hence I cannot do the internet updates. :(

Is there another way to get the updates like downloading them to a USB stick and then putting them on Linux?

Thanks again.download the .deb files and run them at home with gdeb (i think thats the name :S)

---

### Post by stchman on 2008-01-10
> **GavinZac said:**
> download the .deb files and run them at home with gdeb (i think thats the name :S)

He must make sure and download all the dependencies as well.  Ubuntu is very tied to having internet access.

---

### Post by zvacet on 2008-01-10
[This](http://www.nonetdebs.homeip.net/) can be what are you looking for.

---

### Post by GavinZac on 2008-01-10
> **stchman said:**
> He must make sure and download all the dependencies as well.  Ubuntu is very tied to having internet access.

very true. a friend of mine gave it a try but unplugged. silly really in this day and age considering 90% of what a computer is useful for now is the internet.

---

### Post by daimyo505 on 2008-01-12
OK, I got internet at home now. I've done updates via the package manager for ubuntu, and I've also done the updates for the medibuntu. I've done the graphical packages install from Amarok and restarted Amarok, my computer (twice).
Yet still no mp3 playback!

Is it possible that I copied the files from the NTFS drive onto the linux HD and kept them in windows format or something?

Help!

---

### Post by daimyo505 on 2008-01-12
I've now done the add/remove programs and added:
Kubuntu restricted extras
restarted Amarok still no mp3 support.
I then did the add/remove programs:
Ubuntu restricted extras
restarted Amarok and still no mp3 support.

I am starting to get desperate here. :(

---

### Post by daimyo505 on 2008-01-12
Still desperate I tried old commands. When I did this command it worked!!!

sudo apt-get install libxine1-ffmpeg

I tried the full command with "libxine-extracodecs" and it would cause the command to fail.

---

