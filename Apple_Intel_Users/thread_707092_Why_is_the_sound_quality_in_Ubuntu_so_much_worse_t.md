---
title: "Why is the sound quality in Ubuntu so much worse than Mac OS X? (MBP 3rd gen)"
date: 2008-02-25
forum: Apple Intel Users
---

### Post by Abysmal on 2008-02-25
I'm an audio/visual quality nut by nature, and it's one of the reasons I chose the MacBook Pro (Santa Rosa) in the first place..that and its ability to run all the OSes. I've gotten my custom color profile loaded into Ubuntu easily enough to make the screen look gorgeous, but now I'm stumped on the sound quality.

For being tiny notebook speakers, they sound great, but they only seem to sound that good in Mac OS X. In Ubuntu they sound low and muddied with much less range (this also applies to headphones and all sound output). It's bad enough to my ears that I just cannot use Ubuntu if it's not able to be corrected.

Is there some kind of global EQ or even some bass and treble sliders that I could use? I'm on ALSA using the Intel HDA ICH8 sound chip, I even explicitly specified the mbp3 model in /etc/modprobe.d/options (to no benefit). At this point I have no idea how I can improve the sound to match Mac OS X. Maybe there is some bleeding edge version of ALSA that improves ICH8 support?

Any help is greatly appreciated.

---

### Post by Bubba64 on 2008-02-25
The Audacity music player has a lot of manipulation capabilities I am not sure due to just starting to use it a couple of days ago. It is in add remove

---

### Post by ronocdh on 2008-02-25
I noticed this too. I had to futz with the audio levels (I used gui, not alsamixer) in order to find a balance. I'm confident that OS X limits the levels sent to the speakers... for instance, when listening to music in OS X, if I crank the volume, it doesn't get that loud. Try the same thing in Windows, and it's completely satisfactory.

Same goes for Ubuntu. It's completely ignorant of leveling practices of the speakers, much like how battery life is often not as good in Ubuntu as in OS X.

If I right-click on the volume icon in my system tray and go to "open volume control," I can under the File menu of the shown window choose between two devices. I've settled on on maxing out the PCM under the "HDA Intel" device, then scaling the Volume for the "SigmaTel" device back to 70% or so. This works great for me.

Important: set up your audio controls so that when you press F4 and F5, the level of the Volume for the SigmaTel device is changing. I believe that by default, the PCM will be changed, which can lead to ugly distortion and all sorts of other horrible audio artifacts.

---

### Post by BIGtrouble77 on 2008-02-25
I have a regular macbook, but I noticed that the volume bars in the mixer weren't mapped correctly.  For me, it seemed like the Master volume was increasing the treble.  As a result, the sound quality was absolutely horrible.  After I deciphered which volume bars were doing what, things started sounding right again.  Might want to look into that.

-bt

---

### Post by cyberdork33 on 2008-02-25
yea that sounds typical of most Macs. run alsamixer and you can access all channels and switches. I noticed that I would get poor sound quality if some channels were up high, but backing off certain items would allow me to increase volume up and down without issue.

Also, as mentioned, the channels are not mapped correctly, so some sliders do not operate what they say. For instance, the Master channel does nothing for me.

---

### Post by Abysmal on 2008-02-25
None of that seems to have made a difference unfortunately; the problem isn't any kind of crackling or distortion, it's just that Ubuntu has sub-par sound quality compared to OS X. It seems to me like there's far too much emphasis on the mids. It's really unfortunate because I very much want to switch to Ubuntu.

Does anyone know of any global EQ or global bass/treble controls I could use? It seems like that's my only option apart from an updated ALSA driver (unless I can route everything through JACK?). It doesn't make much sense to me because a driver's a driver and should just play whatever sound the hardware is capable of.

---

### Post by Bubba64 on 2008-02-25
I noticed that on my gutsy program the crackling was associated with the 3d settings when I turn it down it goes away this does not answer all of your problems but I thought it wouldn't hurt to mention it.

---

### Post by cyberdork33 on 2008-02-25
> **Abysmal said:**
> None of that seems to have made a difference unfortunately; the problem isn't any kind of crackling or distortion, it's just that Ubuntu has sub-par sound quality compared to OS X. It seems to me like there's far too much emphasis on the mids. It's really unfortunate because I very much want to switch to Ubuntu.

Does anyone know of any global EQ or global bass/treble controls I could use? It seems like that's my only option apart from an updated ALSA driver (unless I can route everything through JACK?). It doesn't make much sense to me because a driver's a driver and should just play whatever sound the hardware is capable of.
it is more likely that OS X does some post processing to the audio.

---

### Post by handy on 2008-02-26
Unfortunately over the last 28months of distro hopping, including some non-Linux kernel based OS's, I have found all of them to have inferior sound quality to that which I had been used to on the dreaded Windows, & also on the G4 Powerbook that we have had for years.

The OS X sound is wonderful on the iMac, & I won't watch a movie under whatever Linux distro' is also installed on the iMac until the sound issue is sorted.

I wonder what the Ubuntu Studio people have learned about this problem?

---

### Post by cyberdork33 on 2008-02-26
> **handy said:**
> I wonder what the Ubuntu Studio people have learned about this problem?I think they pipe everything through jack.

---

### Post by handy on 2008-02-26
> **cyberdork33 said:**
> I think they pipe everything through jack.

I have never really used jack.  Is it a complicated process & does anyone have a quick link to a how-to that they can point me at?

---

### Post by BIGtrouble77 on 2008-03-06
I'm not sure what the root of your problem is, but I can say one thing for sure... Sound quality, in general, is not worse in Linux than OSX.  I do audio production in Logic Studio on my OSX partition and the sound quality is exactly the same for me.  Sound goes through my Firewire 410, but I do mixing with the onboard sound and I can say for certain that the quality through my studio monitors is the same in Linux.

---

### Post by Abysmal on 2008-03-11
Well it must be due to an immature ICH8 driver for the 3rd gen MBP, because I can say with certainty that the sound quality is poorer in Ubuntu for me (the mids are too boosted). I'm not using Sound Enhancer in iTunes or anything like that either, it's that way across the board. 

The weird thing is I recall Windows sounding just as poor (I want to check again now), so I don't know what's going on. I'm excited about PulseAudio in 8.04 though, and hope it solves my problem. 

But geez, a simple global equalizer would take care of this easy; it's 2008 Linux what's up

---

### Post by cyberdork33 on 2008-03-11
[http://jackaudio.org/](http://jackaudio.org/)

---

### Post by hvw on 2008-06-01
In Hardy (amd64) for me it's sounds good now!
kernel is 2.6.24-17 (current header, correct me if i wrong), i 've installed PulseAudio followed by:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)[INDENT]  sudo apt-get install [COLOR=Navy]libasound2-plugins[/COLOR] [COLOR=Navy]"pulseaudio-*"[/COLOR] [COLOR=Navy]paman[/COLOR] [COLOR=Navy]padevchooser paprefs pavucontrol pavumeter[/COLOR][/INDENT]Change default sound device to PulseAudio.
Just in case, i've also installed [COLOR=Navy]alsa-firmware linux-backports-modules linux-restricted-modules[/COLOR]
After restart, i've decided that several programs can simultaneously play audio, but it sounds ugly. So, the second step was build alsa:
[http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/](http://kubasik.net/blog/2008/03/31/sound-problems-in-ubuntu-hardy/)
I've installed [COLOR=Navy]module-assistant[/COLOR]. Than run in terminal:
[INDENT] sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
[/INDENT] restarted and than sound quality got exellent.
PS: be patient when building it. It takes time. Don't worry. Time is your frend.

---

### Post by hvw on 2008-06-01
actually, it sounds better, but not perfect.

---

### Post by hvw on 2008-06-01
And only after install [COLOR=Navy]jackd[/COLOR], [COLOR=Navy]linux-rt[/COLOR] and change kernel from[COLOR=Navy] -generic[/COLOR] to [COLOR=Navy]-rt[/COLOR] one it souds like in Mac OS X !
[http://ubuntuforums.org/showthread.php?t=780072](http://ubuntuforums.org/showthread.php?t=780072)

---

### Post by hvw on 2008-06-02
I don't know why, for me sound quality is exellent only if system boots with [COLOR=Navy]lilo[/COLOR], not [COLOR=Navy]grub[/COLOR]. With the same realtime-kernel.

---

### Post by mealz on 2008-06-08
Hi, I'm not sure whether this is you problem, but I have been investigating the sound on my C2D macbook and found that there are more than 2 speakers in the Apple notebooks, There are independent volume controls in Linux, but they must be hidden in OSX.

My macbook has 3 speakers, I believe the MBP has 4.

For me, in the kmix panel for 'HDA Intel':
'Front' L&R: High frequency internal speakers
'Surround' L&R: Headphone output 
AND
'Surround' Right channel is the 3rd speaker in the macbook (mid range).

Audio will sound bad if only one of these sliders are up.
With only the 'Front' slider up, the sound is very tinny.
with only the 'Surround' slider up, the sound is full of midrange.

To get good sound, a balance in the two levels is required, and then use the 'pcm' control as the volume that you generally vary.

I don't believe Ubuntu has inferior sound quality.  The problem is instead due to the unusual way that apple designed the speaker system on these laptops. 

I suspect that OS X, having knowledge of this unusual configuration sets this balance accordingly and hides it from the user.

---

### Post by mealz on 2008-06-08
Hi, I'm not sure whether this is you problem, but I have been investigating the sound on my C2D macbook and found that there are more than 2 speakers in the Apple notebooks, There are independent volume controls in Linux, but they must be hidden in OSX.

My macbook has 3 speakers, I believe the MBP has 4.

For me, in the kmix panel for 'HDA Intel':
'Front' L&R: High frequency internal speakers
'Surround' L&R: Headphone output 
AND
'Surround' Right channel is the 3rd speaker in the macbook (mid range).

Audio will sound bad if only one of these sliders are up.
With only the 'Front' slider up, the sound is very tinny.
with only the 'Surround' slider up, the sound is full of midrange.

To get good sound, a balance in the two levels is required, and then use the 'pcm' control as the volume that you generally vary.

I don't believe Ubuntu has inferior sound quality.  The problem is instead due to the unusual way that apple designed the speaker system on these laptops. 

I suspect that OS X, having knowledge of this unusual configuration sets this balance accordingly and hides it from the user.

---

### Post by psyke83 on 2008-06-11
Hi,

I don't have any Mac hardware, but I did make a discovery about Sigmatel audio chipsets on laptops. On my Dell Inspiron 510m (with a Sigmatel STAC9750,51 / ICH4 chipset), here is an overview of the audio quality under different conditions:

1. Windows XP, using generic WHQL "Intel AC'97 Audio" drivers: audio sounds bad. Built-in laptop speakers sound distorted at medium to high volume (almost as though the speakers are loose/damaged) with bad frequency response (high quality audio sounds closer to 22050Hz).

2. Windows XP, using Sigmatel drivers from Dell: audio quality is very good, sounds are richer with no distortion even at high volume.

3. Ubuntu (also Fedora, openSUSE and I presume all Linux distributions): audio quality is identical to case 1 above (bad).

After doing some research, I discovered that Sigmatel's XP drivers have a built-in 10-band equalizer. Even though there is no Control Panel applet or GUI to configure these bands, all the bands and their gains are visible from the Windows registry. Oddly enough, if you edit any of the bands via the registry, they reset to defaults upon a reboot.

After doing some hacking I realized that EQ settings are not stored in the driver, but in the laptop's BIOS, and the generic AC'97 driver does not use these settings. I chatted with somebody (who may or may not work for Dell... under the condition of anonymity, heh) and they confirmed my theory; it seems that Sigmatel chipsets contain proprietary extensions to handle equalization, of which neither ALSA or OSS can exploit.

Although we may not be able to expose the same part of the hardware to use hardware EQ, we have other solutions. For Hardy/PulseAudio users, I wrote a guide that includes instructions to set up a 15-band EQ with settings that gives my laptop perfect sounding audio. All I can suggest is that you give it a shot and see if it helps you too!

Here's the guide, and Part D deals with the EQ: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by cyberdork33 on 2008-06-11
This forum is an archive. Please post in the new Apple users Forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

