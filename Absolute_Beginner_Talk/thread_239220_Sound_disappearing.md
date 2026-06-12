---
title: "Sound disappearing"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by toykilla on 2006-08-18
For whatever reason sound disappears in flash and Wine applications. MP3 and movies play sound fine. I rebooted and sound worked in flash but then stopped later. It did not come back on in Wine. 

I dont even know where to begin, so any help would be greatly appreciated.

---

### Post by ComplexNumber on 2006-08-18
i'm still trying to find out some (easy to uunderstand) technical details about the various sound servers, how they work, how they interact with each other, and so on.....and i'm getting nowhere fast :-(. 
from what little i know, i would reckon that wine etc uses a different sound server to the default, so when some application that uses the non-default sound server tries to make a sound at the same time as an application that uses another sound server is currently open, no sound comes out.
i thought there was something called /dev/dsp which allows multiple applications to access the sound card at the same time, but i imagine that its only when 2 applications that use the same sound server try to make a sound.

a few observations that i've made:
-if i  run alsa-player, it runs fine and i can hear sound. if i try run an aplication called gtick(a metronome) during the time that alsa-player is open, it will say this:
> Couldn't start metronome.
Please check if specified sound device
and sample file are accessible. when i close alsaplayer, gtick doesn't give that error and plays normally. i think they use different sound servers (as i understand it) - alsaplayer uses alsa and gtick used oss(this is now defunct, i believe).

if this is difficult to understand, thats because i don't properly understand myself. its just based on my own observations and what little i've learnt.

it may well be the same  with wine and your mp3 player.

---

### Post by richardward101 on 2006-08-18
Flash and (presumably) wine use oss, an antiquated sound system that only allows one thing to play at once. ALSA is the more recent version with mixing. Chances are ALSA had control (even if nothing is playing at the time). I assume that you use Totem for MP3s etc. Totem uses ALSA. You can trick Flash (and along with it other firefox plugins) into playing nicely with ALSA as follows:
```
sudo apt-get install alsa-oss
sudo gedit /etc/firefox/firefoxrc
```
now edit the line that says ```
FIREFOX_DSP="none"
``` so that it says ```
FIREFOX_DSP="aoss"
```Of course, I could be barking up the wrong tree. Hope it works.

---

### Post by richardward101 on 2006-08-18
ps, for wine run ```
winecfg
```
and choose ALSA in the sounds section.

---

### Post by toykilla on 2006-08-18
That worked for wine, but still no go in flash.

---

### Post by bamend on 2006-08-19
I tried this and got this error message:
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /root/.kde/socket-bob-desktop.
can't create mcop directory
bob@bob-desktop:~$

What do I do?  I've got Crossover office pro installed.

Thanks,

---

### Post by toykilla on 2006-08-19
Everything works after rebooting, but flash sound eventually disappears again.

---

### Post by ComplexNumber on 2006-08-19
> but flash sound eventually disappears again.
its because of the explanation i gave earlier ;)

---

### Post by toykilla on 2006-08-19
Yes, I know. But how can I fix it or prevent it. Or even just a way to fix flash without rebooting every time. I confirmed that if if play Amarok, then sound in flash dies.

---

### Post by ComplexNumber on 2006-08-19
> **toykilla said:**
> Yes, I know. But how can I fix it or prevent it. Or even just a way to fix flash without rebooting every time. I confirmed that if if play Amarok, then sound in flash dies.
try typing  'killall esd' (i've no idea why this works sometimes, especially considering that esd wasn't being used for any of the applications :confused: ) on the commandline.

---

### Post by toykilla on 2006-08-20
Yeah that didnt work :( . Obviously something needs to be stopped/started or rebooting would not work either, but it does.

---

### Post by richardward101 on 2006-08-20
As a quick and dirty fix (which will only prevent amarok from mucking up the sound) load amarok and go settings->configure amarok->Engine, and then in the xine settings choose alsa as the output plugin. This will not stop other apps from taking control via oss. Ideally what you need is to tell alsa to keep hold of the sound card and not let go. I'm trying to figure that out as I get annoyed with the sound myself. If I do i'll post back.
Hope that helps in the mean time.

---

### Post by richardward101 on 2006-08-20
Actually, Having amarok constantly open using alsa ought to block oss apps (i think). Again, its a dirty hack, but workable untill theres something better

---

### Post by Mooie on 2006-08-21
Is there any way I can get alsa-oss to work with wine? Some programs (World of Warcraft) dont work well with alsa for some reason.  If you know how to make it work with alsa it would be better, but seeing as a lot of other programs work perfectly w/ alsa and WoW is the only one messing up, its probably a problem w/ the coding in wine.

---

### Post by richardward101 on 2006-08-21
I'm afraid I don't have WoW, but if you've selected alsa and only alsa in winecfg and it doesn't like it, you could try installing and using jack instead.

---

### Post by Mooie on 2006-08-22
I currently dont have jack installed, what packages would I have to install to get it working?  does it output alsa (so i would be able to listen to music and play games at the same time)?   Thanks:D

---

### Post by alberto666 on 2006-09-20
And what about firefox 2?

Because I have firefox 1.5 and firefox 2 beta 2 installed on my system, but maybe firefox 2 look for another configuration file (not firefoxrc), because it works with firefox 1.5 but not with firefox 2.0 :(

---

