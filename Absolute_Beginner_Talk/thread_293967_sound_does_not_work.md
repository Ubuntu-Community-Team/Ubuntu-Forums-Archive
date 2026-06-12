---
title: "sound does not work"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by kpictjl on 2006-11-05
Help please, I can't make my sound work.  The sound on this machine worked fine under windows but I've since done a clean install of Edubuntu and I can't make the sound work.  I've tried to follow the [Comprehensive Sound Problems Solutions Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") but it gets me no where.  I tried booting to a live CD version of Mepis but that didn't help.

I think everything is un-muted.  The aplay command tells me the linux see's my sound card.  It on board sound on an asus tuv4x mb.

any ideas?

```
bighead@pacman:/usr/src$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media PCI CMI8738], device 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media PCI CMI8738], device 2: CMI8738 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by JayTee on 2006-11-06
open a terminal and type alsamixer. Make sure all the volume levels are adjusted properly and that none of the outputs are muted. Use the tab keys to switch between Playback settings, Capture settings and All. Use the up down arrow keys to increase decrease volume and use the left right arrow keys to switch between the various channels  like PCM, Front, Rear, Surround, Center if you have a 5.1 Surround capable sound system. Note: On my system I have to have PCM volume adjusted high to get output.

---

### Post by rdxdude on 2006-11-06
also have the same problem except I have an onboard Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller.  Did what the comprehensive guide told me to do.  Also turned on everything using alsamixer.  My laptop also sees the driver and all just can't get any sound. any help would be awesome thanks.

---

### Post by kpictjl on 2006-11-06
I did the alsamixer thing.  All volumes are 77% or better and all channels are "green" or unmuted.

I'm stumped.

---

### Post by kpictjl on 2006-11-06
I also hate to add that the sound worked a few weeks ago using windows vista.  I didn't want to get sucked into the whole vista thing so I replaced vista with edubuntu.  So, unless my speakers/sound card failed in the past 2 weeks I don't think it's a hardware failure.

This Linux Sound HOWTO doesn't seem to list my chipset. 
[http://tldp.org/HOWTO/Sound-HOWTO/x96.html]("http://tldp.org/HOWTO/Sound-HOWTO/x96.html")

It shows these 2 C-media chipsets, but not mine...I think...CMI8330 sound chip
CMI8338/8378 sound chip

---

### Post by ...acid on 2006-11-07
I had a similar problem.  Last week I installed Kubuntu, and sound worked fine, out of the box...  Sound stopped working a week later, so I reloaded.  Now, it didn't even work at all.  So I tinkered with a few things, I have sound working on my onboard sound chip, although it is very very faint.. However my SoundBlaster Live! 5.1 doesn't work for jack.  It worked last week. so confused. :(

---

### Post by rdxdude on 2006-11-08
just wanted to bump this thread cause some of us need a little help out here.  Any at all would be appreciated thanks.

---

### Post by kpictjl on 2006-11-12
i'm punting.  i've just purchased a new sound card for $14.  I'll post how it goes.

---

### Post by kpictjl on 2006-11-14
I guess I'll keep posting my trials and tribulations until something works!

My new soundcard arrived and I've installed it but yet, no joy:(

System -> Preferenced -> Sound recognizes the card as Sound Fusion CS46XX.  Tigerdirect.com calls the card Diablotek Crystal Relitic 4.1 Channel PCI Sound.  The chipset is CRYSTAL-4620.  

So, now I've tried 2 completely different sound hardware cards (1 PCI and 1 on board) and neither work.  I'm thinkings it's not the sound card.  I tried a different set of speakers and no luck.  

My other Dapper Drake machine has an ensoniq AudoPCI card and the sound works fine.

---

### Post by mdsmedia on 2006-11-14
Just to add another (possibly similar) complication, the sound on my HP Compaq nx6120 notebook worked fine with Dapper....for some time....then all of a sudden on bootup the mute light was turned on and although I could control sound settings, turn mute on and off within the OS, the mute light stays on and I can only get sound through my headset.

I ran the Edgy LiveCD the other day and the sound worked (it was really nice to hear :) ) and sound works when I boot into XP (not so nice to hear ;) ). I get the feeling something was tripped during a Dapper update of some sort but have had no response to a couple of threads I've started.

---

### Post by kpictjl on 2006-11-17
I booted to a live CD of Damn Small Linux and the sound works.  So I know it's not my hardware.  mdsmedia's post above also proves it's not the hardware.

---

### Post by tonymene on 2006-11-18
> **...acid said:**
> I had a similar problem.  Last week I installed Kubuntu, and sound worked fine, out of the box...  Sound stopped working a week later, so I reloaded.  Now, it didn't even work at all.  So I tinkered with a few things, I have sound working on my onboard sound chip, although it is very very faint.. However my SoundBlaster Live! 5.1 doesn't work for jack.  It worked last week. so confused. :(
Exactly the same thing happened to me. I have Ubuntu and Kubuntu Edgy (AMD64 vers) on two partions and SB Live worked fine last week. For the last 3 days  it hasn't worked on both distros, but the integrated audio device works faintly.

---

### Post by kpictjl on 2006-11-19
Next, I booted to a Live CD with Edubuntu 6.10 (Edgy).  The sound worked fine.  I figured what the heck, I then updated from Dapper to Edgy using the procedure listed here [http://ubuntuguide.org/wiki/Ubuntu:Edgy#Ubuntu_Updates]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#Ubuntu_Updates").

Still no sound...

---

### Post by Felix Jay on 2006-11-19
I too have no sound - absolute mystery as I had it and only when I updated using automatix 2 did I lose it - it's a real ](*,)

---

### Post by kpictjl on 2006-11-19
Can everyone on in this thread make their sound work when booting from a live cd?  If so, what does the live cd do different than an install?

I'd really like to learn what is going on.  Is there really a bug here?

I'm considering following the steps listed here [http://alsa.opensrc.org/cmipci]("http://alsa.opensrc.org/cmipci").  But I'm concerned since it says things like, "Now insert the modules into the kernel space."  In my experience so far with linux my humble needs haven't involved compiling or doing anything with the kernel.  Am I really to that point?

---

### Post by kpictjl on 2006-11-20
> **JayTee said:**
> open a terminal and type alsamixer. Make sure all the volume levels are adjusted properly and that none of the outputs are muted. Use the tab keys to switch between Playback settings, Capture settings and All. Use the up down arrow keys to increase decrease volume and use the left right arrow keys to switch between the various channels  like PCM, Front, Rear, Surround, Center if you have a 5.1 Surround capable sound system. Note: On my system I have to have PCM volume adjusted high to get output.

Success!  It looks like JayTee was on to something.  However I did it a little different.  I ran alsamixer and muted everything.  I then double clicked on the little microphone near the date on the desktop (I think it's this tool /usr/lib/gnome-applets/mixer_applet2).  I then unmuted Master and PCM.  Viola! Sound.  I could have used alsamixer, but the mixer_applet helped me focus.

Now I've gone back into alsamixer to see what the settings are...
Card: C-Media PCI CMI8738
Chip: Cmedia PCI
The following are unmuted; Master, PCM, IEC958 5V
Everything else is muted.

Something in my sound settings was obviously causing a conflict.  I'm just happy it works!

BTW, in my searching I found this nifty page with lots of sounds to use as samples, [http://www.findsounds.com/types.html]("http://www.findsounds.com/types.html").

---

### Post by munkydust on 2006-11-23
That's fixed mine. It was the PCM volume that had to be turned up. It was working before so I don't know how it got turned down. Cheers JayTee!

---

### Post by rdxdude on 2006-11-26
what exactly is pcm volume and why does that need to be turned up to the highest?

---

### Post by mdsmedia on 2006-12-09
Mine still doesn't work. My internal soundcard didn't work, but a headset worked. I broke my headset (with 1.6mm jack) and bought a USB headset....now the USB headset won't work either.

It works fine in XP but not in Ubuntu....

The problem I have is that the MUTE light comes on during bootup. Although the volume controls work in Ubuntu, I get no sound. I've tried the alsamixer controls in terminal, and none is muted.

Sound worked fine using the Edgy LiveCD. Sound worked fine in Dapper for some time, then I'm guessing one of the updates messed it up.](*,)

---

### Post by ubromtoo on 2007-04-03
KPICTJL :

    thank you for the findsounds link :) 

     I've never been able to get any up/volume response on the iec958

thingo in alsamixer. it wil mute/unmute o.k., but can't get the up arrow to

do anything.

    Have spent many hours reading MANY threads and trying many 

suggestions.

      In utter despair, wil now go chocolate myself into sugarshock lol

---

