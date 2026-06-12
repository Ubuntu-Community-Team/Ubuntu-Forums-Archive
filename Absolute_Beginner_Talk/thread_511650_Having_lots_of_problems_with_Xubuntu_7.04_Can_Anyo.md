---
title: "Having lots of problems with Xubuntu 7.04 Can Anyone HELP?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Wolfraptor1 on 2007-07-28
Hello and Greetings, this is my first time really using Linux and relying on it as an operating system. It seems my laptop (Toshiba M35X) CD/DVD Combo drive died and when it did it took my Windows XP Home disc and its own Recovery DVD with it. Anyway; I think I like Linux, it looks and feels extremely powerful and intuitive when you get into it, but I still need some help.
     I'm running Xubuntu 7.04 (Feisty Fawn) and I've been tinkering around with it for a few days to try to get things set up. The only problem is I now realise it's alittle more difficult than I initially anticipated. Below I'll provide my computer's specifications and then I'll ask the questions that I need help with.


CPU: Intel Celeron D Processor (2.53 GHz)
MOTHERBOARD: MSI PM8MV-3 w/ VIA Chipset
RAM: 2x 512 MB Kingston DDR400 MHz (1024 MB)
GRAPHICS: Diamond Stealth S120 128 MB (ATI Radeon 9550)
SOUND: Creative Labs SoundBlaster Audigy2 ZS
HDD: Maxtor DiamondMax 7200 RPM 120 GB (IDE Interface)
CD DRIVE: Lite-On 52x/48x/52x
DVD DRIVE: HP DVD840i Super Multi (DVD-R/RW/DL) w/ LiteScribe
PSU: Logisys 480 Watt

     Firstly, I was having problems with my video; but I fixed most of them with the ATI Linux Proprietary Driver. However; I'm still having trouble, I can't get absolutely any video to play, it doesn't matter what format it is, just says it won't play I get a message saying something like, VideoOut Error (vo) Wont Initialize. I have alot of videos spanning alot of formats including MPEG 1/2/4, AVI, DiVX, XViD, and MKV; and none of them will play using mplayer though I've downloaded almost every codec I can find.
     Now, we come to my second problem; issues with sound. As stated above I am running a SoundBlaster Audigy2 ZS but at the same time there are also on-board audio jacks on my motherboard. I've gotten my sound to work a few times but it's been pesky at best, whenever I reboot my machine my sound is dead, I get absolutely nothing.
     when I go into the Mixer to set it, it gives me a "Default" option with settings and it also registers both my sound card and my on board audio. I think the computer is confused as to which one to initialize on startup; and I need help to fix this problem. Does anyone know how to set the SoundBlaster as the default audio output for Xubuntu?
     My third problem, pertains to video again, I'm having problems getting DVDs to play; as in they won't at all. My computer will handle reading a data DVD but will not read a conventional DVD whatsoever. it doesn't give me an error message or anything it just stops working whenever I try to load a DVD to watch it.

So we come down to the three questions I really need to ask:

1.  I installed the Proprietary Linux Driver for ATI, and it enabled me to use transparencies and shadows, but it will not allow me to play videos of any sort; can someone help me figure out how to get them to work?
2.  I have on board audio jacks and a SoundBlaster Audigy2 ZS; whenever I reboot the sound dies no matter which I'm using and I was wondering if maybe I could fix it so my soundBlaser initializes on startup, can someone help me?
3.  I'm having problems getting any form of DVD Video to play at all from my HP DVD840i and I need help getting it so that I can watch DVDs again, can anyone help me with this?

     I hope that I've posted my questions clear enough; and given the examples of the problems I'm having well enough to explain what's going on. I'm a newbie to Linux but I'm not to computers and I'm absolutely stumped. Thank you all for taking the time to read this and thanks again for taking the time to consider helping me. I hope to use Linux for a long time, and I also hope to be a member of the forums here for a long time. Again, thank you all.

---

### Post by scholzilla on 2007-07-28
Hi,

I hope you stick with it. I've torn my hair out many days, but it's worth it. For video, I've found that I have much more luck with Ogle than with totem. In fact, I've removed totem. Also, have you installed the medibuntu codecs? You can get them [here]("http://medibuntu.sos-sts.com/"). You may also need some other plugins. I wish I could remember which video-related ones I had to install, but if you read through some of the posts on this forum, you'll find them. 

As for sound, Ubuntu is very buggy. For instance, there is a kernel update that completely disables my sound, and there are similar bug reports on launchpad. I'm hoping the next distro will take care of these issues. That being said, many potential problems are not bug related, but just a matter of finding the right plugin to play whatever format you want to play. The medibuntu codecs take care of many of these.

Hope this helps!

---

### Post by Toet on 2007-07-28
With mplayer you need to fiddle around with the options to get it going. If you start up mplayer, you can do a right click on the video window, and go to preferences. There you go to video, and try out several settings. I now have it running with the gl2 driver.

The same way you can select a sound driver which works. Then if you start to get going you can try the other tabs. Buffering (increase the buffer memory)  and syncronizing are also important for performance.

Mplayer rocks, you will find out if you have the patience to find it out. Together with memcoder you can do load of things, for example batch converting entire drives of mp4's (or whats that thing m4u, dunno, but you can convert about anything)  to mp3, etc.

Have a nice time finding things.

---

### Post by Toet on 2007-07-28
On the soundcard issue: I have a external usb audio device. Most simple way for me was to dissable the onboard audio device.

If this is not to your liking, I think the way to go is to adjust your alsa-base file. I did that myself (following some howto), but am not an expert on that.

---

### Post by 3rdalbum on 2007-07-28
What you need to do to play DVD is go to [www.medibuntu.org](www.medibuntu.org) and follow the directions there to add their repositories to your system. Then, in Synaptic Package Manager, reload the package list and then install the "libdvdcss2" package.

---

### Post by deadgobby on 2007-07-28
To get DVD. mpeg and ect.. to play you need to install restricted formats. This is easy and not very hard at all. This may be why you are in wounder why DVD will not play.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
 further more your system is has nuff speed to run Gnome or KDE. Xubie is a lite weight o/s for people with older systems. 
Gobby

---

### Post by ugm6hr on 2007-07-28
> **Wolfraptor1 said:**
> 1.  I installed the Proprietary Linux Driver for ATI, and it enabled me to use transparencies and shadows, but it will not allow me to play videos of any sort; can someone help me figure out how to get them to work?
2.  I have on board audio jacks and a SoundBlaster Audigy2 ZS; whenever I reboot the sound dies no matter which I'm using and I was wondering if maybe I could fix it so my soundBlaser initializes on startup, can someone help me?
3.  I'm having problems getting any form of DVD Video to play at all from my HP DVD840i and I need help getting it so that I can watch DVDs again, can anyone help me with this?


Not an expert - but had a few thoughts....

1. Perhaps try VLC (find it in Synaptic Package Manager) - it plays more video formats than anything else, and has all codecs included.  I installed a few of the plugins too - but I don't think you need all of them.
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

2. Not sure about this - I only have 1 sound card, but I have had to mess about with alsamixer / amixer commands... *alsamixer* can select a sound card:
```
alsamixer -c 0
alsamixer -c 1
```
These should chose between the cards - if so - perhaps you could add it to autostarted apps?

3. Don't know - but perhaps VLC may solve this problem too...

---

### Post by Wolfraptor1 on 2007-07-28
Alright, I installed the medibuntu repositories and libdvdcss 2 but this is the error message it gives me when I try to run a dvd (28 Days Later) through gxine:

"THE XINE ENGINE FAILED TO START"

and then...

"No demuxer found - stream format not recognized"

and as for DVDs ogle actually plays them....very nice...but still no sound....

mplayer gives me a Fatal Error when I try to start a video. This is the Readout:

"Error opening/initialising the selected video_out (-vo) device"

I still have no sound the readout it gives me when I go into "Applications >> Settings >> Mixer Settings" is as Follows:

default
#0 VIA 8237
#1 Audigy 2 ZS [SB0350]

Every time I get the sound working, I reboot and it's down again it keeps defaulting, does anyone know how to fix this? btw Thank you all for helping me through this.

---

### Post by tomcheng76 on 2007-07-28
for sound
i use alsamixer
then
```

alsamixer
sudo alsactl store 0

```
to save it as default, u gonna play arround  with alsamixer  and alsactl

---

### Post by Wolfraptor1 on 2007-07-28
so if I run:

"sudo alsactl store 0"

It'll store that particular sound solution as my default?

---

