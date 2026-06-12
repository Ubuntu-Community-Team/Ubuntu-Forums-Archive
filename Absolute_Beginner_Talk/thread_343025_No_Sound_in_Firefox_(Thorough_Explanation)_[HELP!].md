---
title: "No Sound in Firefox (Thorough Explanation) [HELP!]"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by steampunk on 2007-01-20
I realize this is not an uncommon problem. I've read almost all of the threads which involve sound in Firefox. Many of them (in fact, most of them) are attributed to Flash. I can assure you that my problem is broader. For starters, I am using Feisty and I had the same problem in Edgy.

There is no audio output at all when I use Firefox to watch Apple.com movie trailers and  YouTube.com embedded flash videos as well as any streaming audio or video from several sites. I have a feeling that this has little to do with the mplayer-plugin or the flash 9 [stable] plugin. I've tried editing the firefox configuration file to reflect aoss, arts and oss to no avail.

I've also tried symlinking the .esd-1000 file to /tmp/.esd:    ln -s /tmp/.esd-1000 /tmp/.esd
That also did not work.

I uninstalled and reinstalled all of my codecs and plugins from automatix, but this did nothing.

I can hear my theme's sounds (opening and closing windows, resizing windows, etc.) and I can also hear all audio from various movie files. 

Everything works fine except for audio in Firefox. Can anyone assist?

:frown:

---

### Post by steampunk on 2007-01-20
Hmm, well this seemed to work:

1) Create the file .asoundrc in your home directory: sudo vi .asoundrc
2) Paste this into it and save:

> pcm.!default {
        type plug
        slave.pcm "dmix"
}

3) Edit the environment file: sudo vi /etc/environment
4) Paste this into it and save:

> FIREFOX_DSP=aoss

---

### Post by craig700 on 2007-01-22
I enjoy this solution muchly as the long desired sound is back.

Thanks

Craig

---

### Post by Arjunanda on 2007-02-22
Still no sound. Should I start firefox as "aoss firefox %s" or just "firefox %s"?

This is very annoying. Already few times I managed to get the sound working in firefox flash player (youtube) but now again it is gone. Cant remember what I did to make it working, but I assume that time it was adding aoss before firefox command. But for some reason it is no longer working.

---

### Post by r4ik on 2007-02-22
Open terminal, and enter:
Code:

sudo aptitude install alsa-oss

Wait for the install to complete, before typing:
Code:

gksudo gedit /etc/firefox/firefoxrc

A file will open, and in the file you will see:
Quote:
FIREFOX_DSP=”none”
Change this to:
Quote:
FIREFOX_DSP=”aoss”

Good luck !

---

### Post by Arjunanda on 2007-02-22
Yes I had already the alsa-oss installed and firefox started as "aoss firefox". I found that the sound was not working because I had both amarok and xmms playback on pause. Once I quite the players, the sound started working. I also made the change you suggested. So now hopefully it will keep on working :)

---

### Post by DavidFourer on 2007-02-22
Sound was fine for a long time and then yesterday it died on all web sites using flash player in firefox.  I did all the file edits in this thread (relating to aoss) and rebooted, tried running "aoss firefox", no luck.  Are there any ways to troubleshoot and track this down?  Funny thing is it all worked fine untill yesterday.  Must have been the last batch of updates.  How can I find out what they were and return to a previous state?  (I'm beginning to think I shouldn't do any updates between major version changes)  I also wonder if I should remove all the aoss stuff I just added.
*******************fixed this.********************
I guess it was not firefox or flash player.  The whole computer went quiet.  I played around with the "aplay" command in terminal window and couldn't get any sound.  Discovered that my system was muted somehow, even though I never played with any of that.  Right-clicked on the volume-applet icon (next to the date on the top bar on right of screen) to get a menu and un-muted it.  

I learned a lot about flash, alsa-oss, aptitude, where to get help, practice with the terminal, before I found this simple answer.

---

### Post by odzx on 2007-02-23
> **DavidFourer said:**
> Sound was fine for a long time and then yesterday it died on all web sites using flash player in firefox.  I did all the file edits in this thread (relating to aoss) and rebooted, tried running "aoss firefox", no luck.  Are there any ways to troubleshoot and track this down?  Funny thing is it all worked fine untill yesterday.  Must have been the last batch of updates.  How can I find out what they were and return to a previous state?  (I'm beginning to think I shouldn't do any updates between major version changes)  I also wonder if I should remove all the aoss stuff I just added.
same problem for me.
until yesterday everything was ok. today no sound in firefox.
when i run firefox from the terminal i get this message (when playing flash):
> ALSA lib ../../../src/pcm/pcm_direct.c:1509: (snd_pcm_direct_parse_open_conf) Unknown field hint
ALSA lib ../../../src/pcm/pcm_plug.c:1189: (_snd_pcm_plug_open) Unknown field hint

---

### Post by johnbuck on 2007-03-17
Just like to express a big thank you to Steampunk for this solution which work.

I had similar problem as discribed by Steampunk, i.e. Flash 9 has no sound on FF2. however about player like Amarok, Kaffeine has sound.

Has done the firefox.rc with AOSS still not sound, about to reveal back to Flash 7 which has sound until I stumpled upon this post.

---

### Post by sweetestlove77 on 2007-09-09
Help!!! I have tried everything that everyone has said to do and I still do not have sound!!

---

### Post by DouglasAWh on 2008-05-22
Anybody still having these problems in 8.04?

---

