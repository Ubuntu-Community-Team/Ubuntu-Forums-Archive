---
title: "No sound with winamp on wine."
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by djgenesis on 2005-12-20
Hey guys, i installed wine today and started using it. I installed winamp v5.x lite. The installation went fine untill the application requested to download an activeX component for mozilla (screenshot 1).  

I d/l and installed it in program files but after the installation, a message comes up and says it cannot locate it (screenshot 2). 

Despite that, Winamp loads normally. But when i am trying to play an mp3 file it brings up an other error message saying that the file is not supported (screenshot 3)

So i go to Options-->Prefs--> Output--> Wave out
to see what soundcard it is trying to use. But instead of detecting my hardware correctly, i see jiberish on "device" (Screen 4) 


Can anyone suggest anything? 
Note that i am fairly new to linux.

---

### Post by Enter on 2005-12-20
can i ask why are you trying to use winamp when theres linux clones like XMMS and BMP, BMP is my personal favourite

---

### Post by djgenesis on 2005-12-20
1)Lets just say that i have been using it for 8 years under windows and it is difficult to overcome the addiction. 
2)Plus xmms crashes everytime i am trying to stream from a specific station so i have to use rhythmbox for it. 
3)Finally i want to get it running for the sake of knowing what's wrong and being able to learn through the process.



May i add for the post that under wineconfiguration-->Audio-->Sound Drivers --> Alsa --> There are no wave out devices.

Whats with all these different sound drivers? (Alsa,Esound OSS etc) ??

---

### Post by djgenesis on 2005-12-20
Oh!! :D I fixed it. I changed the settings for the wine audio configuration to use Esound (which had an available wave out device) and now its playing fine! Oh... i'm happy! :KS
But still , whats with all these sound codecs also in "Multimedia Systems Selector" ??
Can anyone help?

---

### Post by varunus on 2005-12-20
If you want winamp for linux, try beep media player.  Its the successor to XMMS; its much much better, and has the same winamp interface (with some improvements).

However, lets work on getting winamp working.

First, in the wine configuration (available by typing winecfg into a terminal), go to the audio tab.    Set the output driver to ALSA (the advanced linux sound architecture, this will work for 99% of sound cards).  ALSA is the de facto standard for sound on linux; the other one you may want to try is EsounD (an older, different method of outputting sound that still has not yet been completely stripped from GNOME).  The other options won't work/are for different or older linux distributions.

Set Hardware Acceleration to "Emulation" at the bottom; this means that wine will simulate the presence of Microsoft's DirectSound.  The other available options don't work yet; you need to have it set to Emulation for now.  (Eventually, wine will try and use the sound card itself for direct sound instead of converting from directsound to ALSA.  However, setting it to Emulation has no slowdown; I can play games with no sound lag and my computer is several years old.)

OPTIONAL:  The activex errors you're getting are not *that* important; some option winamp components use activex.  You don't have to do this step if you don't want to.  It seems that winamp wants to have the mozilla activex plugin installed.  What you need to do is go to the mozilla website and download Mozilla for *windows.*  Then, you need to install the activeX plugin on it; do it the exact same way you would in windows (get the installer, etc.)

Next, set winamp to use the directsound output plugin instead of the waveout plugin.  After this, try playing songs, and everything should work!

Good luck, and post back any errors/issues...I would still recommend trying out beep media player, or heck, even rhythmbox; I know I used to be a staunch winamp advocate, but trying iTunes (and Rhythmbox, which has the same interface) had be switch in a week.  Its just so much more convenient...

---

### Post by djgenesis on 2005-12-20
Yeap !!! Thanks for the post. I have to say that it was most enlighting. I skipped the "optional" part for the firefox plugin but winamp is playing sweet.
I also took the advice of you both and i downloaded Beep Media Player. Again you are right, it is far less complicated. I will have to get used of the shortcuts i guess but that won't be a problem.

* ALSA (the advanced linux sound architecture, this will work for 99% of sound cards)
Yip, emulation was the problem apparently.

*Next, set winamp to use the directsound output plugin instead of the waveout plugin.
Indeed it's playing sweet.

The only thing BPMx is missing is a "bookmarks" option but i guess i can handle without that. 

Thanks again for all your help.

---

