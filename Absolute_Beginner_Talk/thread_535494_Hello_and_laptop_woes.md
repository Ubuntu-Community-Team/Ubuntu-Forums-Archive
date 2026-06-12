---
title: "Hello and laptop woes"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by -=WaLrUs=- on 2007-08-26
Hello to everyone.

New to the forum and sort of new to Ubuntu.
Previously installed Mandrake, RH and Suse on my old desktop.

My beloved laptop died today, and I decided now would be a good time to put Unbuntu Studio on. So I have, I am sitting here in lovely Unbuntu desktop.

So far so good, install went well.  I need to tweak a few things and hence this post.

I can't seem to configure sound on this system.  My laptop is a Samsung R45.  I am considering installing XP to make getting drivers easier etc.

However I really don't want to do that.

So any tips for sorting out libs and deps for my sound?  Total beginner to Ubuntu, so need to see what devices I am using etc to get correct libs.

Also music player totem the best or VLC better?

Backup Sbackup seems pretty good or any better ones for regular DVD backup?


I've tried searching but to no avail.


Any help greatfully received.

---

### Post by Happy_Man on 2007-08-26
For  your sound, have you tried ```
alsamixer
``` and made sure that the bars are up all the way?

For out of the box everything, VLC is better. If you want, you can install the gstreamer plugins so that Totem will play stuff. 

I'm not sure about the DVD backup..... someone else probably will though. 

For a good guide to getting started with ubuntu: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by -=WaLrUs=- on 2007-08-26
hi,

Thanks for the quick reply,  where would I find said program?

*Please forgive me if I don't reply for quite sometime, as I have a family to look after also*

---

### Post by -=WaLrUs=- on 2007-08-26
ok,

when I try to play an audio CD , not MP3 or OGG type i get the following error:

"Couldn't display "cdda:///dev/hdc".
There was an error launching the application.


[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by jimrz on 2007-08-26
> **-=WaLrUs=- said:**
> hi,

Thanks for the quick reply,  where would I find said program?

*Please forgive me if I don't reply for quite sometime, as I have a family to look after also*

from your panel go to System>Administration>Synaptic Package Manager and search "alsamixer" or from the Terminal
```
sudo apt-get install alsamixer
```

I think this can also be installed via "Add/Remove" at the bottom of the "Applications" menu

---

### Post by -=WaLrUs=- on 2007-08-26
get the error message 

Reason: Could not open resource for writing.

when going near sounds.

Possibly try standard Ubuntu?

Any other ideas?

---

### Post by anewguy on 2007-08-26
Let's start at some basics and move up from there.

(1) Do you have a little speaker icon on your top bar?

(2)  Click on Applications, move down to Accessories, then over and click on Terminal.  When that window opens, type  "lspci"  (without the quotes) and post that back here as well.

With that information, we can hopefully find an existing tutorial or message thread for your sound.  If not, we'll work on getting it working.:)

---

### Post by -=WaLrUs=- on 2007-08-27
I have the little icon in top right next to network connection with a cross by it.

In terminal I get the response command not found!

---

### Post by louieb on 2007-08-27
> **-=WaLrUs=- said:**
> In terminal I get the response command not found!
  
The **lspci **command is included in every Linux distribution I have tried.  Might want to try it again. Remember it is case sensitive. If you still get the command not found message then your install has more problems that just sound.

---

### Post by vincentvee on 2007-08-27
you shouldn't really have any dependency problems, like was said in the first reply, go to alsamixer, looking to play mp3 files, you should get automatix from here
for dvd backup of data i don't use any backup software, i just drag and drop in K3B, which is a kde burning program, but works fine under gnome
two other kde programs that you might find useful are k9copy for copying dvd's and amarok, media player, better than totem by far, better than vlc too i think anyway
good luck with it

> **-=WaLrUs=- said:**
> Hello to everyone.

New to the forum and sort of new to Ubuntu.
Previously installed Mandrake, RH and Suse on my old desktop.

My beloved laptop died today, and I decided now would be a good time to put Unbuntu Studio on. So I have, I am sitting here in lovely Unbuntu desktop.

So far so good, install went well.  I need to tweak a few things and hence this post.

I can't seem to configure sound on this system.  My laptop is a Samsung R45.  I am considering installing XP to make getting drivers easier etc.

However I really don't want to do that.

So any tips for sorting out libs and deps for my sound?  Total beginner to Ubuntu, so need to see what devices I am using etc to get correct libs.

Also music player totem the best or VLC better?

Backup Sbackup seems pretty good or any better ones for regular DVD backup?


I've tried searching but to no avail.


Any help greatfully received.

---

### Post by -=WaLrUs=- on 2007-08-27
Thanks for info on k3b etc.

Still the same error in terminal though!

---

### Post by -=WaLrUs=- on 2007-08-27
my bad, got this response to lspci:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
08:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:07.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
08:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)

---

### Post by -=WaLrUs=- on 2007-08-27
ok,

It looks like updating the ALSA drivers will solve my problem.

I have downloaded the alsa driver,lib and utils version 1.0.14rc4 from alsa-project.org.

I don't know what to do now, something like this:

./configure --with-oss=yes --with-sequencer=yes --with-kernel=/lib/modules/`uname-r`/build

:confused:

---

### Post by vincentvee on 2007-08-27
how did that work out for you??


> **-=WaLrUs=- said:**
> ok,

It looks like updating the ALSA drivers will solve my problem.

I have downloaded the alsa driver,lib and utils version 1.0.14rc4 from alsa-project.org.

I don't know what to do now, something like this:

./configure --with-oss=yes --with-sequencer=yes --with-kernel=/lib/modules/`uname-r`/build

:confused:

---

### Post by -=WaLrUs=- on 2007-08-28
I get this back:

bash: uname-r: command not found
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by -=WaLrUs=- on 2007-08-28
ok,  I have updated ALSA to 1.0.14rc4

using :

    *

      Install the required tools 

sudo apt-get install build-essential ncurses-dev gettext

    *

      Install your kernel headers 

sudo apt-get install linux-headers-`uname -r`

    *

      Download the latest version of alsa from [WWW] Alsa project (driver, library, and utils) to a directory (eg. ~/downloads). In the following we assume that the latest version is 1.0.14. Please change this in accordance with the one you downloaded from the Alsa project site.
          o

            [WWW] alsa-driver
          o

            [WWW] alsa-lib
          o

            [WWW] alsa-utils 
    *

      Setup installation directories 

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14.tar.bz2
sudo tar xjf alsa-lib-1.0.14a.tar.bz2
sudo tar xjf alsa-utils-1.0.14.tar.bz2

    *

      Compile and install alsa-driver 

cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

    *

      Compile and install alsa-lib 

cd ../alsa-lib-1.0.14a
sudo ./configure
sudo make
sudo make install

    *

      Compile and install alsa-utils 

cd ../alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

Note that you must have the curses library installed to be able to compile alsa-utils. You can install it with this command from a terminal: sudo apt-get install libncurses5-dev

    *

      Reboot 


WHen I rebooted I had lots of sliders but no matter which combination I used still no sound!

Any ideas?

---

### Post by notwen on 2007-08-28
Have you double checked alsamixer to make sure all volumes are turned up?  Also once you get your sound working, you may want to follow the guide [here]("http://ubuntuforums.org/showthread.php?t=413625") to obtain all the appropriate codecs/plugin for audio/video playback. =]  Good luck w/ getting your audio working.

---

### Post by -=WaLrUs=- on 2007-08-28
all up to max, only tryuing to play an audio CD via VLC at the moment.  CD plays but no sound!

---

### Post by anewguy on 2007-08-30
Well, I have not experience with your particular setup, but I can tell you what worked for me - maybe it's worth a try to see if it helps or not.

First off, this is going to sound a little confusing and counterintuitive, at least it did to me, but it did work:

- double click your sound icon on the top bar
- be sure the correct device is selected - if not go to file/change device and make the change
- click on edit/preferences
- scroll through the list and if you see "External Amplifier" be sure it is checked
- close out of preference
- click on "Switches"
- look for "External Amplifier" and be sure it is NOT checked
- exit out of ALSA mixer
- click on system/preferences/sound
- click on the "Sounds" tab
- try clicking the "play" next to Log In or Log Out and see if you have sound

I have no idea if this will work for you.  I know I had no sound and for the life of me could not find out why.  Then I found a post on the net (it may have even been back in this forum somewhere) that said to try this and indeed it worked.  Seems weird to turn on the amplifier in the preferences but then turn it off in the switches, but it worked.

Good luck to you!:)

---

