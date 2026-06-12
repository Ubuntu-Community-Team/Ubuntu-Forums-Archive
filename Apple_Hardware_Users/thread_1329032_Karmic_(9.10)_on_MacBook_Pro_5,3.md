---
title: "Karmic (9.10) on MacBook Pro 5,3"
date: 2009-11-17
forum: Apple Hardware Users
---

### Post by catskul on 2009-11-17
I just recently purchased a MacBook Pro 5,3 and went through the instructions available here: [https://help.ubuntu.com/community/MacBookPro5-3/Karmic](https://help.ubuntu.com/community/MacBookPro5-3/Karmic)

I'm not sure if I screwed something up somewhere, but after 3 days of fighting I have still not been able to get sound working. I have therefore decided to reinstall, start fresh, and try again. But this time, I'm going to document my step by step for the sake of others trying the same thing.

-------------------------------
I will be following instructions,
[INDENT][https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)[/INDENT]
and
[INDENT][https://help.ubuntu.com/community/MacBookPro5-3/Karmic](https://help.ubuntu.com/community/MacBookPro5-3/Karmic)[/INDENT]
Let me start with what I know/have set up already.

[LIST]
[*] rEFIt is installed on my system
[*] I've created 3 additional partitions 
[LIST]
[*] [*] sda3 - ext4 - /
[*] [*] sda4 - ext4 - /home
[*] [*] sda5 - swap
[/LIST]
[/LIST]

----------

1. Partition from Mac OSX:
[INDENT]Already done
originally had to resize down OSX partition, and create hfs partition to hold the place for the forthcoming linux partition [/INDENT]

2. Boot up Karmic CD
[INDENT] Caveats: to get the CD to boot I had to hold 'c' during boot
no cd boot option showed for me in the rEFIt menu.
I selected the install option this time (instead of booting to the live cd, and then installing)[/INDENT]

3. Install
[INDENT] Chose the default keyboard (and not the USA-Macintosh that I was tempted to.)
Chose "Specify partitions manually"
Selected sda3 for root as ext4 (though I thought to make it ext3 since I heard some rumor that you can reach ext3 from OSX)
Selected sda4 for /home as ext4 
sda5 automatically selected as swap
wait for install to complete
restart[/INDENT]

5. Check Audio
[INDENT]restart
try audio tests from "System>Administraton>System Testing" with headphones in. No luck.
try aplay -l from terminal. Reports:
```
card 0: NVidia [HDA NVidia], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
aplay /usr/share/sounds/alsa/Noise.wav
produces nothing[/INDENT]
6. Get Wifi working
[INDENT]wifi applet in panel shows that wifi is not working.
"System>Administration>Hardware Drivers" shows nothing (I have the impression that last time, when I installed in livecd version, it at least showed up here)
Use "System>Administration>Synaptic Package Manager" then "Settings>Repositories" to select "Installable from CD ROM" option
"Reload" in Synaptic
Re-check "Hardware Drivers" and still see nothing
Use synaptic to install "bcmwl-kernel-source"
restart
wireless works
[/INDENT]


7. Add in repositories to APT
[INDENT] Instructions suggest to add the mactel-support ppa from jaunty, but this runs counter to the instructions on the mactel-support ppa page. In light of the conflict I first did what makes more sense to me and add the karmic ones like so:
```
sudo add-apt-repository ppa:mactel-support
```
... but afterwards I realized that the karmic ppa does not have all the packages..(wtf?)
so added the jaunty ones as well.
I also want the latest nvidia drivers (190) so I will add a ppa that supplies it
```
sudo add-apt-repository ppa:nvidia-vdpau
```
(jockey aka "Hardware Drivers" did not seem to pick up that another nvida driver had become available)[/INDENT]

8. Start installing and configuring necessary packages
[INDENT]install sensors and fan packages* (not actually when I installed these)
edit /etc/modules to load them
restart to allow those to be loaded and perhaps for jockey to reinitialise and find nvidia drivers
jokey still doesn't show nvidia 190 drivers.
use synaptic to find and install all packges with nvida-190 in them
recheck jockey and dont see them.
install all possible upgrades.
attempt to turn on effects.
accept message that says drivers need to be downloaded and installed (despite having already installed the 190s)
fails with "installArchvies() failed" possibly because I had synaptic running at the time.
Check jockey once again and finally see that the 190 drivers show up.
Enable them.
Per message, restart to allow them to take effect.

It was actually here that I notice that packages from jaunty ppa were needed.
Notice the instructions are contradictory
-lists many packages "not needed by default"
-lists choice between packages and told to "see below" but there is never any indicaiton below for what to choose.


install dkms stuff
edit /etc/modules
edit /etc/modprobe.d/blacklist

keyboard fn keys for backlighting doesnt seem to work if you only follow the 5.3 instructions. Neither do the ones for the screen brightness adjustment. However keyboard backlight available by command line.
The instructions explicitly state that the fn keys should not work, but in the *next sentence* imply that they should "..even if you lower it with F5..."

You need to install pommed to get them working. It worked for the screen brighness right away, but didn't seem to work for the keyboard backlight. But later I tried it again and keyboard backlight adjustment seemed to be working. May have needed a reset.

Fix this freaking mouse pad thats driving me nutts!
install and run synclient "script" adjusting the max mouse speed down to 1.5 instead of 2.5
and including the syndaemon time out line: "syndaemon -d -t 1"

eff all this synclient ********. Just adjust in system>preferences>mouse>touchpad

Not sure about reserving the lower 200 units for clicking only. I would rather just turn off tap clicking like it is in osx. Not sure how.

Ok and now on to the beast that Was my nemesis last time. Sound

cd /usr/src/
sudo wget [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz)
sudo tar -xxvf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure --enable-dynamic-minors  --without-oss --with-cards="hda-intel"
sudo make
sudo make install

restart

sudo apt-get install gnome-alsamixer
gnome-alsamixer

unmute front speaker
raise volume on both front speaker and surround
check surround box

aplay -l
{{{**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
}}}

aplay /usr/share/sounds/alsa/Noise.wav
SUCCESS !!!
YES!

also go into the sound preferences>hardware and select analog surrond

I believe last time, the kernel had been upgraded automatically because I had selected "proposed" and or "backports" from the repository selector.
[/INDENT]

9. Customize
[INDENT]install art manager from applications>Ubuntu Software Center
access via system>preferences>art manager
try to get backgrounds
wait rediculous amount of time while it downloads 1250 backgrounds (wtf, why not just get thumbnails).
window borders to gilouche


install ubunt-restricted-extras
Install agave to figure out a better color scheme.

install gnome-color-chooser to adjust gnome-panel foregound color
change gnome-panel to black instead of system colors.
change terminal profile to white on black

install CompizConfig settings manager (CCSM)
disable static switcher
enable shift switcher
enable show desktop
enable desktop cube
enable rotate cube
enable trail focus
enable group and tab windows
[/INDENT]



[/INDENT]


*slow going... not lots of free time...be patient*

---

### Post by Bachstelze on 2009-11-17
I don't exactly have a 5,3 (5,5 here) but everything worked pretty much OOTB in Karmic.

---

### Post by catskul on 2009-11-17
They aren't the same hardware (from what I understand). And the instructions are a little different as well. (Though reading through the 5,5 document, I wonder if it might be a better)

Thanks for your attention, but I would have rather you hadn't voted since it doesn't necessarily apply. I'm trying to see what might subtly be different. I don't think you can un-vote, but if you could, I would ask you to.

---

