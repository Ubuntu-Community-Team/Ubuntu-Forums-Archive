---
title: "no sound in firefox"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by thomeboy on 2008-02-14
I've had ubuntu for a few weeks now and have never had to come to the forums. My problem is that I can't get my sound to work in firefox. Streaming audio will not work in youtube or myspace. I can get video but no audio. I had a sound problem with mplayer also and I found a thread telling me to change audio to ESD, which DID work.

However nothing seems to work with firefox. This is a recent change, my sound was working fine until today. The only thing that I can think of that I've changed was that I also installed Opera because a website I needed to go to didn't work in firefox. 

I've tried multiple solutions to this problem as there were many similar problems when I googled it. I tried making an .asoundrc file and that first confused me and second didn't work. I've also tried reinstalling flash 9 plugins and that did nothing.

The only thing I can think of is that it is the same problem as mplayer, as mplayer used to work and then suddenly didn't and I changed it to ESD and now it works.

Any help would be much appreciated.

---

### Post by Zeroangel on 2008-02-14
Well, if anything which uses the ALSA soundsystem (as opposed to OSS) launches and takes over your sound system, then some apps which use OSS will be unable to play audio. As a test try launching firefox using the command "aoss firefox" and see if that helps ya. It will make firefox use ALSA instead of OSS.

---

### Post by thomeboy on 2008-02-14
ya I just read that in another forum.

I tried it and the terminal showed this error:

ALSA lib pcm.c:2105:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so

So then I read up on that and installed libasound2-plugins and typed asoundconf unset-pulseaudio. Now i type aoss firefox and I don't get an error but I also don't get sound.

The only reason i installed pulseaudio whatever was to try and fix this problem and it seemed to just make it worse.

This is killing me, I loved Ubuntu until this started happening.

---

### Post by Bubba64 on 2008-02-15
there are plugins in synaptic and in Firefox add ons that may help check this post in todays list  Sound Stuttering version 7.10

---

### Post by thomeboy on 2008-02-15
I already had those plugins. My sound was working before, it just suddenly stopped working and the only change I can think of is installing opera.

---

### Post by Bubba64 on 2008-02-15
I Don't no if this will help but here is a link on alsa-oss installation regarding a bug in flash
[www.linuxquestions.org/questions/linux-software-2/video-but-no-sound-in-firefox-453292/](www.linuxquestions.org/questions/linux-software-2/video-but-no-sound-in-firefox-453292/)
It is from 2005 but the alsa-oss together may be the key. Have you checked in synaptic if alsa-oss is on.

---

### Post by thomeboy on 2008-02-15
Yeah I had already seen that thread and tried doing the solutions on there which didn't work.

Maybe the problem is due to my two sound cards? I had a crappy onboard one and put in a cheap sound blaster, i think the 16 bit one. I set the default card as Audio PCI which is the sound blaster but that did nothing. I have no idea why firefox will no longer play sound. I also tried running firefox as root and that did nothing. 

It seems there is nothing I can do to fix this annoying problem and to me its a big enough problem to go back to XP.

---

### Post by thomeboy on 2008-02-15
I solved the problem.


I had to install:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

and after it worked. I think I had the same problem as a lot of other people and I was following a guide in which it told me to download that file but the link to it was broken so I found a mirror and apparently the mirror I found was either not the same thing or for some reason didn't work. However this link did work and if anyone else has this problem, then this should work.

---

### Post by Bubba64 on 2008-02-15
The only thing we don't know is the program your running and the computer you have. Personally I have never had any problem like your having, but with more info posted you will probably get an answer from somebody who knows what you can do. Linux can be a little frustrating at first and but after you get a good understanding it works great. I don't know the terminal lines to get a read out of the right info to isolate your problem so that it can be quickly fixed, sorry I couldn't be more helpful. I just read you solved the problem as Mr Burns always says Excellent.

---

### Post by Zeroangel on 2008-02-15
Congrats!

If your sound gives ya any more grief, try disabling the onboard sound in the BIOS, running 2 soundcards can sometimes make sound programs act batty.

---

### Post by z0mbie on 2008-02-15
Is this a bug? Does anyone know? Maybe Pulse will fix this in Hardy.

---

