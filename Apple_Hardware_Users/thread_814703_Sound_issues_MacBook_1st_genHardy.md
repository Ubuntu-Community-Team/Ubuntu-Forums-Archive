---
title: "Sound issues: MacBook 1st gen/Hardy"
date: 2008-05-31
forum: Apple Hardware Users
---

### Post by Aurora on 2008-05-31
Hi,
I'm using a first gen MacBook: Core Duo, 2GHz, 2GB RAM. I have sound through the laptop speakers only, and the level seems low. Here are the outputs of
cat /proc/asound/version
and
cat /proc/asound/card0/codec#0 if it helps:

```
pad@MacBuntu:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on May 19 2008 for kernel 2.6.24-16-generic (SMP).
pad@MacBuntu:~$ cat /proc/asound/card0/codec#0
cat: /proc/asound/card0/codec#0: No such file or directory
pad@MacBuntu:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [18.05dB] [on]
  Front Right: Playback 255 [100%] [18.05dB] [on]
Simple mixer control 'PC Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'BaseFRQ',0
  Capabilities: penum
  Items: '18643' '18643'
  Item0: '18643'
```

I compiled the latest ALSA version and applied the other fixes per the WIKI, but still no sound out.  I would like to use the line/headphone output as well as USB audio devices, such as audio interfaces.  This is my audio production laptop; I would like to migrate away from proprietary OS's and tools, and hopefully still use the hardware I've invested in.

Thanks,

Paul in Seattle

---

### Post by cyberdork33 on 2008-05-31
run 'alsamixer' in the terminal, and you will be sure to see every channel available there. make sure everything is turned up and unmuted. (navigate with arrows, m-key to mute/unmute)

---

### Post by mustang on 2008-05-31
Hi Paul,

I have a first gen too. I didn't need to get the latest ALSA drivers. I just ran "alsamixer" and turned up all the levels.

---

### Post by Aurora on 2008-06-01
Thanks; who knew 'surround' would have to be turned up for normal stereo?  And, I had forgotten about the 'm' key.

Now I have to work on getting it to detect and use my external sound/Midi device, but at least I can escape the tinny laptop speakers.

There is a whole thread devoted to this device, so no need to answer here.  If you think you can contribute, here's the thread:

[http://ubuntuforums.org/showthread.php?t=148467](http://ubuntuforums.org/showthread.php?t=148467)

Two years, nine pages, and still going. Welcome to the world of Linux audio, BWAHAHAHAHA:twisted:

And a shout-out to Maku-d, whose post #49 in that thread revealed the Secrets of the Universe.

--Paul

---

### Post by Aurora on 2008-06-05
Hi,

If anyone's still watching this thread, I installed some Ubuntu Studio packages, and things changed.

Alsamixer only shows one slider, the master.

Audacious plays sound for a few seconds, then goes dead.  Movie Player can play movies with audio, but doesn't seem to play audio files.

Oh, wait...I just tried that same sound file with Rhythmbox, and it plays.  So the problem is not system wide.  Not as bad as I'd feared, but still annoying.  Try opening that Ubuntu Sax.ogg file in the Examples folder in your home directory, and see what happens. Double click and it opens with Audacious; right-click and you can choose an application.  I'm curious to know how this works on other computers.

The good news is, I can play sound through my external sound card/audio interface/MIDI controller, and control sofware synthesizers with it.I have been trying to do this for a year at least; it never worked in Feisty or Gutsy.

I wish I understood this better.  Computer audio is a very complex thing, especially in Linux. [edit] I just discovered that I can mouse over that .ogg file without clicking, and it plays. But double-clicking doesn't work. Hmmmm.

--PD

---

### Post by phetre on 2008-06-08
This sounds like a PulseAudio/JACK problem. I barely understand it at all, but Hans Fugal does. He has a couple of excellent posts on his blog, hans.fugal.net/blog/. It's worth reading the [whole first post]("http://hans.fugal.net/blog/articles/2008/06/04/jack-on-the-macbook"), but here's the bottom line:

> So in summary, if you don't care about dmix but only JACK (or any other application using hw:0, which can be all of them if you change your .asoundrc, but only one at a time), set position_fix=3 for snd-hda-intel e.g. in a file in /etc/modprobe.d/ with a line like this: options snd-hda-intel position_fix=3, and do update-initramfs -uk all. If you want a more balanced setup, where you can have JACK running and other well-behaved ALSA applications can use the sound card, leave the module parameters alone and set up realtime and use the following command to start JACK (or equivalent settings in QJackCtl):

/usr/bin/jackd -R -dalsa -ddefault -r48000 -p1024 -n4 -s

If you want to use PulseAudio in this situation, configure it to use the default ALSA device instead of hw:0.

If you like PulseAudio and JACK both, the ideal situation would be PulseAudio using JACK as a backend, JACK using hw:0 with position_fix=3, and the PulseAudio plugin as the default ALSA device. Unfortunately this is just a theoretical ideal, and doesn't work (yet) because of bugs. [BUT SEE BELOW! -phetre]

And finally, if you have no or limited use for JACK, but want to use PulseAudio, just change your .asoundrc as above to make PulseAudio the default ALSA device, so that all applications, ESD aware or not, use PulseAudio.

And then the next day, he posted a way to get PulseAudio working as a JACK client. I think that's what you need: [http://hans.fugal.net/blog/articles/2008/06/04/pulseaudio-as-a-jack-client]("http://hans.fugal.net/blog/articles/2008/06/04/pulseaudio-as-a-jack-client")

---

### Post by Aurora on 2008-06-09
phetre,

I'm grateful for your efforts. Oddly enough, I also came across this blog today. It's a bit over my head, but I will keep at it.[Edit]  It does appear that he is addressing issues that are different from what I'm dealing with.  Before tackling JACK, I just want basic sound working, which I don't have.  I am using neither PulseAudio nor JACK at the moment, just ALSA.

The sound is behaving completely differently today, though I can't think of anything I changed. Before, I could use RhythmBox to play sound through the internal speakers or the line/headphone out at full volume, and the alsamixer slider turned it up and down.  Today, the sound is faint, and the slider (there is only one) has no effect; I can even mute it and the sound continues.  I am mystified.  I am going to wait until later to mess with it, having already spent too many hours with the computer today.

--PD

---

### Post by xwhisky on 2008-06-26
I have also 1st gen macbook. I have question and I want know if also somebody else has same experiences. I still have problem with -rt kernel from ubuntu. All kernel with -rt makes me complication on start. I have really small chance to boot. Most of times I have message message like:
MP-BIOS bug: 8254 timer not connected to IO-APIC

And this is also happend sometimes with generic kernel, but not so often.

Have someone similar experiences?

Tomas

---

### Post by Aurora on 2008-06-28
> **xwhisky said:**
> 

MP-BIOS bug: 8254 timer not connected to IO-APIC

Tomas

Hi Tomas,

This is a known bug in Ubuntu.  I don't think there is a fix yet.  For now, boot with "Restore"  You may have to hit the 'esc' key when it first starts booting to get the GRUB menu.  Then you can scroll down with the arrow keys; it will say something like "Ubuntu 2.26.xx-18 -rt restore" It will either fail, or you will eventually see a menu with a "return to normal boot" option.  Choose that and it will boot.

This will work much of the time.

Peace,

Paul

---

