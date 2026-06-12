---
title: "Video broken"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2008-01-05
Hi all,
I have a problem using any media players in a fresh install of Gutsy. Whatever I double-click on to play in (default) Movie Player, the player comes up, begins to buffer, and then freezes. Doesn't matter if it's an .avi, a .mp3... audio/video.. nothing plays. I do have system sounds and all that, and I installed Gnome Movie Player and that works (most of the time), but not being able to play any of the 300+GB of media I have is making me itchy.

I've un-/re-installed totem and whatever else there is (audacity, mplayer, rhythmbox) but still - **nothing** works except gnome player, and only for .avi movies (and even that is hit-or-miss).

Anyone have any other ideas?

---

### Post by Ub1476 on 2008-01-05
```
sudo apt-get install ubuntu-restricted-extras
```

For all codecs so you'll be able to play .avi .mpg whatever..

```
sudo apt-get install vlc
```

If Totem doesn't work, use VLC. They're both great!

---

### Post by reckless2k2 on 2008-01-05
do you have the restricted codecs installed to play/view those media types?

---

### Post by detroit/zero on 2008-01-05
> me@my-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for xxx:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.I tried to install VLC before in either Add/Remove or Automatix (whichever one has it listed) and it said that it conflicted with another installed application. I did just try it again in the terminal and it installed fine.

I'd still like to know why Totem wouldn't work, as it is the default media player..

---

### Post by carrett on 2008-01-05
Try opening a video via the terminal, like:

```
mplayer somevideo.avi
```

and post the output, especially the error-y parts.

---

### Post by detroit/zero on 2008-01-05
```
me@my-laptop:/media/disk/files/Videos$ mplayer Pi.avi
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Genuine Intel(R) CPU           T2080  @ 1.73GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Pi.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  352x208  12bpp  23.976 fps  964.2 kbps (117.7 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
```

At that point no mplayer window is visible, and the terminal is hung until I hit ctrl-c.

I notice two things at the top - "could not connect to socket," and "no such file or directory". I don't know about a socket, but I can assure you the the file "Pi.avi" does exist.

---

### Post by carrett on 2008-01-05
How about dmesg, /var/log/messages or /var/log/syslog, does anything show up in those files/commands when you play the videos?

---

### Post by detroit/zero on 2008-01-05
> **carrett said:**
> How about dmesg, /var/log/messages or /var/log/syslog, does anything show up in those files/commands when you play the videos?
I can't say that I saw anything pertinent in those.. just the usual hardware-/ethernet-related entries.

---

### Post by carrett on 2008-01-05
This is indeed mysterious. Which package provides this "Gnome Movie Player" that you said is the only one that works for you?

---

### Post by detroit/zero on 2008-01-05
It's in Add/Remove under the Sound & Video category. 

No media player has worked since I (fresh) installed Gutsy a week or so ago and I was looking for "official" alternatives.

Gnome MPlayer is the actual title.

---

### Post by carrett on 2008-01-05
Hm, it looks like gnome-mplayer is just a frontend for mplayer, so if it works, mplayer should work too. I really have no clue why it wouldn't work. Sorry, maybe someone else knows!?

---

### Post by detroit/zero on 2008-01-06
I hope so. 

It's just annoying to have to right-click and open with>something other than the default player on every video or piece of music I want to enjoy.

---

### Post by detroit/zero on 2008-01-06
Related note:

That fresh install of VLC player also freezes when loading any type of media file - video or audio of any type of format.

---

### Post by detroit/zero on 2008-01-11
Oddly enough - out of nowhere - I now have full media-playing capability.

My sister sent me an email with a .mov file attachment of my nephews playing or whatever, and when I clicked the attachment, TBird asked how I wanted to open it. Without thinking, I clicked whatever the highlighted option was (Open with Movie Player). 

It worked.

I'm not sure why or what happened. But it's over now.

---

### Post by carrett on 2008-01-11
huh. Well "Movie Player" is totem, if I am not mistaken. Anyway enjoy!

---

### Post by ubuntu-freak on 2008-01-13
My guide might be useful
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

