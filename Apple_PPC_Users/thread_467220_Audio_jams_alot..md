---
title: "Audio jams alot."
date: 2007-06-07
forum: Apple PPC Users
---

### Post by [censored] on 2007-06-07
Audio files only play for the first few seconds and then jam. Haven't tried vids, but I suspect it's the same story.

Basically, I'll try playing an mp3 or a wavfile, in either xmms, mplayer or vlc, and it only gets as far as the first few seconds of the track before it just jams.

Any help would be appreciated. Thanks in advance.

System: Emac G4, 700Mhz, 384 meg ... feisty ppc.

---

### Post by avtolle on 2007-06-07
[censored], the bug below might be related to your problem. I ran into a similar issue with my G4 Cube running the desktop CD when I was trying to use Rhythmbox. It crashed, generating an automatic bug report, which was determined to be a duplicate of the one below. After installing 7.04, I changed the playback default in the Multimedia Selector to USB, and I 've been able to use XMMS (after configuring), Rhythmbox, to play CDs and streaming audio. Totem plays video with sound. VLC plays video, no audio. There are no system sounds. When I try to test, I get an error message. 

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/89130](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/89130)

---

### Post by [censored] on 2007-06-07
thanks avtolle. So it's a kernel bug? I've discovered that installing kenel 2.6.17-10-powerpc fixes the problem.

Pity I can't have a more up to date kernel, and play multimedia files.

---

### Post by stmiller on 2007-06-07
Yeah I made a bug report on the alsa bug tracker. I think everyone is stumped. I'm going to ask around a little more before making a report on the kernel bug tracker, to make sure it's a valid bug and not ubuntu specific.

---

### Post by avtolle on 2007-06-07
stmiller, it may be Ubuntu specific, or it may be Gnome specific, given what little I could discern from the bug report, etc. While the absence of system sounds is no more than a bit annoying, I would like to have them.

---

### Post by stmiller on 2007-06-07
EDIT: Woops, I thought this was the bug in question:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652)

I wonder if they are related.

> **avtolle said:**
> stmiller, it may be Ubuntu specific, or it may be Gnome specific, given what little I could discern from the bug report, etc. While the absence of system sounds is no more than a bit annoying, I would like to have them.

There's a thread here on gentoo with the same problem of my above linked bug, but seems is solved with a more recent alsa and snd-aoa:

[http://forums.gentoo.org/viewtopic-t-548091.html](http://forums.gentoo.org/viewtopic-t-548091.html)

The frustrating thing is that I tried varying newer alsa releases and kernel releases and the bug was still there for me.

---

