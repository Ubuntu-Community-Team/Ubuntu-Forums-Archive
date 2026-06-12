---
title: "which codec? gstreamer0.10 or medibuntu-repo?"
date: 2007-08-23
forum: Apple PPC Users
---

### Post by frog_pilot on 2007-08-23
After installing ubuntu on my powerpc, first I opened synaptics and installed all available gstreamer0.10 codecs (good, bad, ugly, alsa, ffmpeg, gl, esd), as I do it on normal PC's, but totem don't want to play my avi-files. I didn't try anything else yet...

After reading this [Java, video codecs, and DVD playback]("https://wiki.ubuntu.com/PowerPCFAQ#head-33ae73d3b565e8c5b3c470bafabc452695423381") I ask myself, if I do have to uninstall the codecs and libdvdcss3 from the normal repositories before installing the medibuntu-alternatives?

Aren't the normal gstreamer codecs working on PPC-architecture?

---

### Post by stmiller on 2007-08-24
I don't think libdvdcss is in the standard ubuntu repos ? 

Medibuntu has the mplayer codecs and libdvdcss, mainly, among other things which Ubuntu does not distribute. Your avi file may need those codecs. (ppc-codecs)

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by frog_pilot on 2007-08-24
To be clear I have only the standard-repo in my sources listand added the sections universe, multiverse and the backports. I think on an ppc-installation, I will find only packages for ppc in synaptics.

Thats why I opened synaptics and added the packages (which I found in synaptics after adding the stated sections):

gstreamer-0.10-***
totem-gstreamer
xine-ui
libxine***
libdvdcss3
vlc

Thats what I did also on i586 machines.

When I'm opening avi-files with vlc, it will close  immediatly after start. (later I could post the terminal-feedback).

When I'm opening avi-files with totem, it stays black and freezes.

When Im opening avi-files with xine-u, it plays the file (i think it has it's own codecs and don't uses the gstreamer-frontend) but the sound is like muted (very quiet with highest volume-settings).

When I put a DVD in the drive, the xine-ui will close immediately after choosing DVD-playback.

Will there be any conflicts when I keep the stated packages and add these from the medibuntu-repo, or would it be better to uninstall the gstreamer-things and other packages?

---

### Post by stmiller on 2007-08-24
There's no libdvdcss3 listed in [http://packages.ubuntu.com](http://packages.ubuntu.com)
?

And you are right xine uses the ppc-codecs (win32codecs) and is different from gstreamer. I've had problems with anything xine on my Powerbook, and stick to the gstreamer backend.

Have you installed ppc-codecs ?

And as far as xine quiting when trying to playback a DVD, have you set up the drive location, audio and video settings in xine setup?

---

### Post by frog_pilot on 2007-08-24
My fault... It was libdvdread3.

I am starting now adding medibuntu to my sources list and installing ppc-codecs. Gstreamer-0.10 from the ubuntu-repos I will keep on my hd until there occure any errors.

by the way: this said vlc after starting in a console:
```
mpunk@PUNIX-G4:~$ vlc
VLC media player 0.8.6 Janus
[00000291] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
No accelerated IMDCT transform found
Segmentation fault (core dumped)
mpunk@PUNIX-G4:~$ 
```

may be this is also the reason for the sound-problem with xine???

---

### Post by stmiller on 2007-08-25
Could be an alsa/sound problem it looks like. What is the output when you run

alsamixer

Does it start ok?

---

### Post by frog_pilot on 2007-08-26
Als-Mixer is starting OK.

After installing the ppc-codecs from medibuntu-repo, I can play avi-files with totem. But when I want to play it with vlc-player, it crashes during the opening of the file. When I start vlc on the terminal it gives the following feedback:```
VLC media player 0.8.6 Janus
[00000336] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.iec958
No accelerated IMDCT transform found
Segmentation fault (core dumped)
``` but it plays about 2 seconds with picture+sound before crashing :confused:

But vlc-player plays encrypted DVD's. And when I try to open the same DVD with totem it feedbacks, that there aren't the necessary plugins installed. (libdvdcss2 is installed).

---

