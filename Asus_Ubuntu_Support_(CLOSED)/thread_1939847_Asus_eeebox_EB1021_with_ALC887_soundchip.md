---
title: "Asus eeebox EB1021 with ALC887 soundchip"
date: 2012-03-12
forum: Asus Ubuntu Support (CLOSED)
---

### Post by spacekiek on 2012-03-12
Hi,

I'm using a Asus Eeebox EB1021 (AMD E450 platform) together with XBMCbuntu.
This works really like a charm, very smooth ... exept no audio ??

The audio chip used is : ALC887 

I've already tried the suggested fix on some forums :

sudo gedit /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=generic

But no luck ...

Alsamixer shows 2 sound cards:

1/ HD audio generic : This sound device does not have any controls
2/ HDA ATI SB: Master / Headphone / Mic / Mic Boost / S/PDIF / SPDIF Default (none are muted)

Any help ? Seems to be a difficult audio chip ... :confused2:


Edit:   I've tried the following

options snd-hda-intel model=auto index=1

and got a sound bar level in the system tray! But no sound? :confused:

---

### Post by nikkkko on 2012-03-26
Did you get any further with this?  I just installed 11.10 on the same box with the same result.

---

### Post by spacekiek on 2012-03-27
Nope ... I installed Win8 for the time being ;-)

---

### Post by nikkkko on 2012-03-27
Well, there are [some other messages around]("http://ubuntuforums.org/showthread.php?t=1903990") by users with the same on-board audio in different set-ups, some of which seem to have had some success.  I'll have another look this evening if I have time and if I get lucky I'll post here.

---

### Post by livecd1965 on 2012-04-16
Same problem here. Had to move to W7-64 bit with my ee.

---

### Post by zeuzzz on 2012-05-13
Upgrade to 12.04 - I got myself a fresh install and headphones are working without additional configuration.

---

### Post by nikkkko on 2012-05-14
Ditto.  Upgraded to 12.04 and sound issues are history.

---

### Post by Jens007 on 2012-05-23
> **nikkkko said:**
> Ditto.  Upgraded to 12.04 and sound issues are history.

I have the same computer, eb1021, however there is still a problem with the hdmi sound. I do not use any propretary driver. from time to time, I do not have sound. When it has happend, there is no HDMI
in the sound settings. In this case I have to restart the computer.
Has somebody the same problem?

---

### Post by akhi3030 on 2012-10-13
> **nikkkko said:**
> Ditto.  Upgraded to 12.04 and sound issues are history.

Hi, I am planning on buying ASUS EeeBox PC EB1021.  Can you please tell me if 12.04 works smoothly out of the box or were there some issues? 

Does all HW work such as audio through HDMI?

Have you or anyone tried using the remote and had any success with it?

---

