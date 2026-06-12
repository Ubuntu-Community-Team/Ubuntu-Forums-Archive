---
title: "PowerMac G4 733Mhz Sound Issue"
date: 2008-06-09
forum: Apple Hardware Users
---

### Post by irwing on 2008-06-09
Hi everybody,

I'm here again with my problem, i've searched in all ubuntu powerpc forums and hadn't find a solution. The sound works fine thru the 10 first secons, than the app. (RhythmBox,Exaile...) deads. I really need help 'cause I work with audio, and I'm losing time and money...

Tryng to change between devices(ALSA,OSS,PulseAudio) i got this message:

ALSA - audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

PulseAudio Sound Server - audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused.

I'm using Ubuntu Hardy, kernel 2.6.24.18-powerpc

 cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.15 emulation code)
Kernel: Linux Dexter 2.6.24-18-powerpc #1 Wed May 28 19:29:28 UTC 2008 ppc
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
PowerMac Tumbler (Dev 21) Sub-frame 0

Audio devices:
0: PowerMac Tumbler

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: PowerMac Tumbler

---

### Post by daladheri on 2008-07-19
I am having the exact same problem!! I have the same machine too. Really makes me mad! Any solution?

---

### Post by oswaldkelso on 2008-07-20
I have a g4 733 running debian and sound can be a pain, just on this machine. but I found the easiest way to fix it after all the usuall alsaconfig stuff is run: 

ekiga

After I set my devices in ekiga usb and  PowerMac Tumbler work?

---

### Post by sms0611 on 2009-03-13
Hi Guys,
   Did you manage to get this problem sorted out?

   I am running the same hardware with Hardy installed and have no sound at all. But having added snd-powermac to etc/modules I now have all the sound options just no sound
  
   When I run lshw or lshw-gtk no sound device is shown

   I read  on one of the apple support sites that this may have something to do with the cmos battery being flat. Ever heard of this?
   
   As I am new to the Mac/Ubuntu thing I have not as far as to change it yet but in my case it could be a possibility as the hardware has been sitting around doing nothing for 2 years.

Any more ideas?

---

### Post by sms0611 on 2009-03-28
Hi Guys,

   I have finally solved the PowerMac G4 sound problem.

   Sound is now working fine via inbuilt sound card and speaker also the headphones work.

   If anyone is interested in knowing how I've done it please feel free to contact me.

---

### Post by oimon on 2009-04-09
steve - please can you provide your Howto on fixing the sound?
cheers

---

### Post by sms0611 on 2009-04-09
Hi Oimon,

  Will do, no problem, just give me a day or so if you will to get my notes into a form more understandable than they are at the moment- You know how it is here in southern Spain, nothing ever happens quickly especially during Easter week.

---

### Post by sms0611 on 2009-04-09
Hi Oimon,

   You're a lucky man, the wife has had to work overtime so I've had time to do this for you. Enjoy and good luck,

OK. First a few ground rules.

This works for Ubuntu 8.04 on a PowerMac G4 Quicksilver with a PowerMac-Tumbler soundcard. It may work on other configurations but, hey, I haven't tested it on anything else.

I don't know if all of the below is absolutely necessary but this is exactly what I did and it worked, I'll leave it up to you to decide how much or how little you want to do.


**Add sound card module to the system**
 
```

sudo nano /etc/module

add the following line at the end

snd-powermac

```

**NEXT**

```

sudo nano /etc/rc.local

add the following lines before the line reading exit 0

amixer sset &#8216;Auto Mute&#8217; off
amixer sset &#8216;PC Speaker&#8217; on

```

**Reboot the system**

**Add Video and Sound. **

I can't honestly say why this should be necessary but it does seem to be even if you don't use VLC

Install VLC + VLC plugin for ALSA via Synaptic Package Manger

**Install latest ALSA version ALSA v.1.0.19**

Go to the following page and at the end of the original post you will see a list of files

[http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137")

The following is the one you want

File Type: tar  	AlsaUpgrade-1.0.x-rev-1.16.tar

Then almost follow the posted advice. Mine works.

Short Alsa-Upgrade script install instructions:
1. download the script and save it somewhere (click on the file)
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.x-rev-1.16.tar
4. sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di

the -di stands for download and install which (unfortunately) is missing from the original post

This will take at least 15 minutes so go and get a beer or a cup of coffee.

**Run the alsa configuration program.**

 Also missing from the original post

```
sudo alsaconf

```

Select PowerMac-Tumbler

then keep selecting OK to let the program do its job.

**Start up VLC**

Under edit->preferences->audio->output modules

select ALSA

exit

**Reboot the system**

You should now have a working sound and video system.

---

### Post by oimon on 2009-04-10
thanks for your post - i'm sure many others will appreciate after a google search gets them there.

after reading your post and knowing it was possible, i spent more time looking at my problem. it turned out to be far more trivial than your own - the main volume was turned up (as shown by the volume mixer), but PCM volume was at zero. rather simple but annoying if you aren't sure that your sound card is working at all.

thanks again
oimon

p.s. i'm running 9.04 beta on ibook G4 1.42ghz for anyone else who stumbles on this thread

---

