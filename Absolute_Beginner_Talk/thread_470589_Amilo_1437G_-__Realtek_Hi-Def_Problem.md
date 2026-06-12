---
title: "Amilo 1437G -  Realtek Hi-Def Problem"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by si_harp on 2007-06-11
Hi all,

First off, like a  lot of people, its my first time using Linux, have only used a Knoppix Live CD for backup before.  I have installed Ubuntu 7.04 on a triple boot system alongside with XP and Vista.  Triple boot setup works fine, using Vista's bootloader and edited it to find Ubuntu using EasyBCD.

In Ubuntu my laptops speakers wouldn't work however the headphone jack worked and even the volume dial worked with that too.  I thought it would be best to try and install the Realtek drivers... so I followed the instruction on this page, however using the newest drivers on realteks website...

[https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloM1437G](https://wiki.ubuntu.com/LaptopTestingTeam/FujitsuAmiloM1437G)

I followed all the step at the bottom till step 4.  When trying *vi /target/etc/hotplug/blacklist* it went to a black screen with a few blue ~ along the left side, here I was supposed to blacklist...

snd_hda_intel
snd_hda_codec

Tbh I was not too sure what to do here.

Now whenever I try to log into Ubuntu it come up with an error "session only lasted less than 10 seconds..."
Error seemed to be.. "x-session-manager:error while loading shared libraries:libasound.so.2: cannot open file..."  I can still log into the terminal though.

I tried reconfiguring the xserver-xorg but this did not change anything.

I would much appreciate if anyone can suggest how I can fix this and recommended what drivers I should install for my laptop, (has an AC880 realtek high-def audio chip) in order to get everything working.

Please bear in mind I'm pretty new to this.  I've spent a few hours searching for solutions but havnt had much luck.

Many thanks to repliers.

Si

---

### Post by renzokuken on 2007-06-11
i had the ALC883 sound chip and that didnt work on my laptop either.

i fixed it by simply updating to a newer version of alsa-driver.

go to [www.alsa-project.org](www.alsa-project.org) and download the latest alsa-driver (1.0.14) to your home folder.

then run the following to compile and install it.

```

sudo apt-get install build-essential
tar xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver*
./configure
make
sudo make install
```

reboot and see if the sound works

EDIT you can still do this thorugh the terminal if you dont have a GUI by donwloading directly using wget

```

[color=blue]wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2[/color]
sudo apt-get install build-essential
tar xjf alsa-driver-1.0.14.tar.bz2
cd alsa-driver*
./configure
make
sudo make install
```

---

### Post by si_harp on 2007-06-11
Hi renzokuken,

Thanks a lot for the suggestion.  I cant get into the GUI so I tried what you suggested through the terminal.  It all went ok (took a while tho) however I still cant get into the GUI.  Comes up with the same error as before...

"x-session-manager:error while loading shared libraries:libasound.so.2: cannot open file..."

I also tried...

sudo apt-get remove alsa

This had no effect either!

Any other ideas?  Thanks again

Si

---

### Post by si_harp on 2007-06-13
I have also just been looking around at other threads online and have tried the following commands, all without any success...

sudo rm /usrulib/libasound.so2   (could not find file)
sudo rm /home/username/.asoundrc (again could not find file)
sudo /etc/init.d/alsa-utils stop      (not found)

Anyone got any ideas?!  I still cant get into Gnome :(

Many thanks. Si

---

### Post by si_harp on 2007-06-15
Anyone? (bump)

---

### Post by renzokuken on 2007-06-15
beats me to be honest.

personally i'd just do a complete reinstall and try again with the newer alsa-driver.......may not be the most efficient way but it seems like you may have accidentally done something to stop it working without knowing what.

---

### Post by si_harp on 2007-06-15
FIXED!  :D

Found this thread [http://ubuntuforums.org/showthread.php?t=461894](http://ubuntuforums.org/showthread.php?t=461894) 

With thanks to engla who suggested trying...
[B]
*apt-get install --reinstall libasound2*[/B]

Fixed the problem, didn't even need to reboot to log on properley!  

Hope this helps someone. Si

---

### Post by Thomas from Toijala on 2007-06-17
I have an AMILO M6450G, very similar to yours. Also my sound did not work, and I totally misunderstood the situation, until I found a text from Fujitsu, telling me to use ALSA-mixer, turn on "PCM" and "side" and mute everything else. To my great surprise IT WORKED. I run Kubuntu, so later I realized that also Kmixer can do the same. I have found so many texts mentioning, as you did, that headphones worked, but nothing else. I suspect they all had perfectly responding machines and just weird mixer-settings. My Realtek ACC 880 at least seems to be perfectly compatible with (K)ubuntu that is otherwise absolutely new to me. Wish you good luck!

---

### Post by si_harp on 2007-06-18
Hi all,

@Thomas from Toijala:  Thanks, I dont have the "side" channel option, however I have managed to fix things...

Have just managed to install the latest ALSA drivers 1.0.14/a and have just figured out all the channels for my soundcard/laptop.

To install the ALSA drivers I followed the instructions on these two links...

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=415685&goto=nextnewest](http://ubuntuforums.org/showthread.php?t=415685&goto=nextnewest)

I installed the driver, lib, oss and utils in that order.  If anyone want the exactly commands I used let me know.

As for configuring the sound in alsamixer.

**HEADPHONES**
This adjust the volume of the headphone out lead only.

**PCM   **     
This adjust the volume of both the internal speakers and the headphone out.  I have configured the volume control in system tray (if called that in ubuntu :S) to control this channel.  Does anyone know what PCM actually stands for tho?

**CD**
I have muted this channel, as otherwise there seems to be a constant noise.

**INTERNAL SPEAKER**
Self explanatory.  The sound that comes out your laptop with no headphones in.


Side volume wheel doesn't work.  I have read this may be due to bug in kernel, but I don't know enough about that!

Thanks everybody for their help.

Si

---

