---
title: "Playing DVD movies and music files"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by linuxneeewb on 2007-12-28
I recently installed Ubuntu but cannot figure out how to play DVD movies or some sound files. I would appreciate if you could walk me through the steps to do this including how to install codecs if necessary. Any and all help is appreciated. Thanks.

:guitar:

---

### Post by stchman on 2007-12-28
> **linuxneeewb said:**
> I recently installed Ubuntu but cannot figure out how to play DVD movies or some sound files. I would appreciate if you could walk me through the steps to do this including how to install codecs if necessary. Any and all help is appreciated. Thanks.

:guitar:

Follow my procedures on my site in my sig.  I have procedures for encrypted DVD playback and MP3 playback in the Multimedia section.

---

### Post by taurus on 2007-12-28
Try to install the ubuntu-restricted-extras package either from synaptic or from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by nathandelane on 2007-12-28
In order to play DVDs you will need to instal d e c s s, which is available in the installer/updater (I think it's in the Applications menu/K menu/ or Ubuntu logo menu), you may also need to install some codecs and a player.  My favorite player in VLC, available in the installer/updater as well. Music files should just play also in VLC or any other player by default aside from the codecs thing. MP3 is a proprietary (non free) format, so if you're trying to play MP3's then you may need to install LAME, which is an MP3 codec.

Hope that helps.

Breakdown of what to install
- d e c s s (it's really one word, I'm paranoid)
- VLC (if you don't like the pre-installed player[s])
- LAME
- Any other video/audio codecs you want, like DIVX

Nathan

---

### Post by nathandelane on 2007-12-28
Taurus is smarter than I. Listen to him :)

Nathan

---

### Post by linuxneeewb on 2007-12-28
Thanks

:popcorn:

---

### Post by ingram on 2007-12-28
[http://medibuntu.org/](http://medibuntu.org/)

You may want to give that site a read. If you want a summary on just how to enable DVD playback let me know. 

My first install some years ago took me awhile to figure out DVD playback but once you learn the ropes it is easy enough to do.

---

### Post by jkrtest on 2007-12-29
I tried everything suggested here ad I still can't get VLC to play DVDs.
I followed the link: [http://www.stchman.com](http://www.stchman.com) and installed the libdvdcs2.
Immediately got prompted for a file update, did that, no luck.
VLC is the default player and fires up when a DVD is inserted, but that's pretty much it.
VLC lists the title briefly, so it can access the drive.

BTW, the "sudo apt-get install ubuntu-restricted-extras" doesn't work, that package doesn't exist.
One other thing I did before, right after installing VLC, was instaling the libdvdread3 package that was recommended elsewhere.

Any idea where I should start troubleshooting?

thx,
=k

---

### Post by doorknob60 on 2007-12-29
You need to enable more repositories first, don't worry, it's easy. Just go to System>Administrations>Software Sources, type in your password, and check off all the boxes under Downloadable From the Internet. Then try installing ubuntu-restricted-extras.

---

### Post by jkrtest on 2007-12-29
@doorknob60:
that's correct, it's downloading 112 MB of files now...

---

### Post by coffen on 2007-12-29
You could check out this HowTo
--> [http://ubuntuforums.org/showthread.php?t=651946](http://ubuntuforums.org/showthread.php?t=651946)

---

### Post by jkrtest on 2007-12-29
um, nope.
Followed both suggestions, Taurus' and coffen's, but VLC still won't play a DVD.

Thoughts?

---

### Post by Goliathofdavids on 2007-12-29
I am having a similar problem, I have ubuntu restricted extras and all gstreamer plugins installed and still I can't get any dvds to play

---

### Post by The Great BM on 2007-12-30
Add me to the list of people with DVD playback problems.  I've installed every plugin that has been recommended (like the Medibuntu ones), and while I get some playback, all of the DVD playing software that I have tried to view the DVD with has crashed.  VLC Player will close itself, Totem tells me that libdvdcss2 is not installed (but it is), and Xine gives me this error:

[IMG]http://img175.imageshack.us/img175/4573/xineerrorsps2.gif[/IMG]

Is there something else I need to install, or is this an issue with my hardware?  Thank you.

---

### Post by jkrtest on 2007-12-30
Ok, I found that after installing anything, it really helps to do a soft reboot (ctrl+alt+backspace).
Not sure if that's technically sound, but after rebooting, VLC started to play DVDs. The menu wouldn't work (just the sound), but I could move right to the first chapter and the video would play, albeit with lots of jumps and jerks.
So I reinstaled libdvdcss2 and even the libxine1-ffmpeg and I rebooted and it worked.
Issue resolved.
Vista played the DVD right off the bat, BTW.

As for hardware needs - GreatBM, how much RAM do you have? Can you play other media files, like .AVIs?

---

