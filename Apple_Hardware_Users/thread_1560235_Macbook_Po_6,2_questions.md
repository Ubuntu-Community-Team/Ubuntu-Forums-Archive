---
title: "Macbook Po 6,2 questions"
date: 2010-08-24
forum: Apple Hardware Users
---

### Post by oboewan on 2010-08-24
So I'm considering installing Ubuntu on my MBP 6,2 (15" i5 2010 and all that jazz).

I've been reading the page on that particular model on the wiki and it says:

1. The "Sensors (Temps & Fans)" section is listed as "needs manual install" with the notes "Temperature, fanspeed, environmental light and keyboard backlight can be controlled over the sysfs exported interface at /sys/devices/platform/applesmc.768/." Pardon me for being a noob, but what, exactly, does that mean? What, exactly, do I have to install? Will I have to do manual tweaking to get the fans working and the temperature in range? Or will the system handle that automatically? The former would be an ABSOLUTE GAME-BREAKER for me; I would rather my system not overheat. Also, on a less-important note, does this mean that the ambient light control for screen and keyboard lighting works?

2. According to the wiki, mbp-nvidia-bl-dkms, pommed and btusb have not, at press time, been updated in the repos to support this particular model; instead, I'll have to use the alternate versions located [here]("http://ubuntuforums.org/showthread.php?p=9247034") and [here]("http://ubuntuforums.org/showthread.php?t=1469437"). Is this still true?

3. Also according to the wiki, if you want to use an mDP-VGA adaptor to connect a display smaller than 640x480, you need to add 
```
Option "NoEDID" "True"
```
to your xorg.conf. Two questions: where in the file do you put it (I know next to nothing about xorg) and would it be a good idea to do this anyway?

4. It says in the wiki that I need to manually select the driver for the AirPort card. Is it correct to assume that I need to be connected to Ethernet to do so? Is there any way I can download it before doing the actual install?

---

### Post by math- on 2010-08-24
Hi Oboewan,

I have a mbp pro6,2 too. I have installed ubuntu 10.04 a few minutes ago. 
I follow the wikipage just like you.

**1. The "Sensors (Temps & Fans)"**

I don't know, I'm confused just like you.
[B]
2. mbp-nvidia-bl-dkms, pommed [/B]

The packages are updated now. Don't follow the link.  (I don't try btusb at this time)

**3. Xorg.conf**

 You have to put this line in the Section called "Device".

[B]4.Wifi card

[/B]Yes, you  need a linked connection to install wifi driver.

---

### Post by furok23 on 2010-08-25
kudos for the edid true location... that was really making my brain itch last night...

in regards to #1, your already set. butttt if you notice, everything is still hellllla hot. i was searching the forums and came across [this (scroll to bottom)]("http://art.ubuntuforums.org/showthread.php?t=1467062") which is an automatic fan control script.

while you can hear the fans, it gives me the peace of mind seeing my internals at a lower temp (i also installed an internal temp sensor applet).

yours to decide

---

### Post by dngfng on 2010-08-26
Hi - Swedish Wings programmed a Great Daemon that takes care of Fan Control - have got it working on my MacBook Pro 6,2

[http://ubuntuforums.org/showpost.php?p=9765062&postcount=24](http://ubuntuforums.org/showpost.php?p=9765062&postcount=24)

Its still pretty fresh so if you find any bugs just give him a shout.

Also I would suggest just to follow the steps listed here:

[https://help.ubuntu.com/community/MacBookPro6-2/Lucid](https://help.ubuntu.com/community/MacBookPro6-2/Lucid)

As far as I can tell everything (apart from proper fan control) including the in build camera works out of the box by now - obviously you have to activate the proprietary drivers from Broadcom and nvidia separately.

---

