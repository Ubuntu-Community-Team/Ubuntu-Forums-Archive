---
title: "Garbled tracks in Ubuntu"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by autopoietic on 2007-11-21
Hello,
I copied some tracks from my iPod filders to my hard disk. Now when I play them on Amarok or RhythmBox, they seem to be garbled and multiple tracks are written over each track. Is there a way that I can remove the noise? Thanks in advance.


--autopoietic

---

### Post by jordanmthomas on 2007-11-21
Did you buy these from the iTunes store?  If so, they are likely encrypted, which is why they can't be played.

If you look up how to remove encryption from aac files, you should come up with a few tools.  (Burning them to a CD and then ripping the CD works, but it's a real pain)

---

### Post by autopoietic on 2007-11-21
Thanks for your reply. Not really, I downloaded them from other sources. Every track seems to have been over-written with other tracks. The iPod is formatted now, so I only have the local copy on hard disk. Thanks.

---

### Post by jordanmthomas on 2007-11-21
Well, I hate to jump to conclusions, but the only time anything like this has happened to me it was because my hard drive was going dead. 

Anyway, there is a program called audacious that will allow you to edit the sound files.  I believe it even has a remove noise filter.  However, this can be tedious and not perfect.

Now, when you say that multiple files are put in one, are they put on top of each other.  That is, do both songs get played at once?  If only one song is played at a time, you are in luck because you can cut and paste parts of files in audacious (there's other tools for this too, but I don't know what they're called).

---

### Post by autopoietic on 2007-11-21
I bought my Thinkpad just two months ago, so I doubt it is the HDD, especially since everything else seems to work fine. Consider a track X. When I play X, I hear traces of Y or Z once in a while over X. It seems like it added other tracks over the original track. I am trying to install Audacious now. It will still be painful to edit 30 gigs of music - I wonder if there is a tool that can automatically look for noise and remove it. Thanks.

---

### Post by jordanmthomas on 2007-11-21
Well, I am not an audio expert by any means so, I'd like to pass this one off to someone who is maybe.  Once I was wrong with the encryption stuff, I was basically out of ideas.  :)

---

### Post by autopoietic on 2007-11-21
Thank you though!

---

### Post by MrFSL on 2007-11-21
I have never heard of this behavior with iPods but it does sound intriguing. 

So it appears that multiple audio tracks exist in a single file.

You can identify track information using mplayer.

**Install mplayer**
```
sudo apt-get install mplayer
```

**Identify File Info**
```
mplayer /path/to/iPod/file.m4a -identify -frames 0 
```

Post the output of the above command.

---

### Post by ryphix on 2007-11-21
I've had this happen to songs when LEGALLY downloading music by torrent and the download did not complete 100%.

---

### Post by autopoietic on 2007-11-21
slartibartfast@TablaRasa:~$ mplayer /path/to/iPod/file.m4a -identify -frames 0
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /path/to/iPod/file.m4a.
File not found: '/path/to/iPod/file.m4a'
Failed to open /path/to/iPod/file.m4a.


Exiting... (End of file)

---

### Post by MrFSL on 2007-11-21
> **autopoietic said:**
> slartibartfast@TablaRasa:~$ mplayer /path/to/iPod/file.m4a -identify -frames 0
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /path/to/iPod/file.m4a.
File not found: '/path/to/iPod/file.m4a'
Failed to open /path/to/iPod/file.m4a.


Exiting... (End of file)

I'm sorry. When I wrote **"/path/to/iPod/file.m4a"** I meant that you should put in the path to YOUR iPod file that sounds garbled. For instance, if these files are on your desktop it would look like:
```
mplayer /home/username/Desktop/Filename.m4a -identify -frames 0
```

Substitute "username" with _your_ username. Change "Filename.m4a" with the name of _your_ file etc.

Sorry for the confusion.

---

### Post by autopoietic on 2007-11-21
Sorry my bad. Here it is.
slartibartfast@TablaRasa:~$ mplayer /home/slartibartfast/Desktop/Music/iPod/F13/ADAV.mp3 -identify -frames 0
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/slartibartfast/Desktop/Music/iPod/F13/ADAV.mp3.
ID_AUDIO_ID=0
Audio file file format detected.
Clip info:
 Title: Planet Telex
ID_CLIP_INFO_NAME0=Title
ID_CLIP_INFO_VALUE0=Planet Telex
 Artist: Radiohead
ID_CLIP_INFO_NAME1=Artist
ID_CLIP_INFO_VALUE1=Radiohead
 Album: The Bends
ID_CLIP_INFO_NAME2=Album
ID_CLIP_INFO_VALUE2=The Bends
 Year: 
ID_CLIP_INFO_NAME3=Year
ID_CLIP_INFO_VALUE3=
 Comment: 
ID_CLIP_INFO_NAME4=Comment
ID_CLIP_INFO_VALUE4=
 Track: 1
ID_CLIP_INFO_NAME5=Track
ID_CLIP_INFO_VALUE5=1
 Genre: Unknown
ID_CLIP_INFO_NAME6=Genre
ID_CLIP_INFO_VALUE6=Unknown
ID_CLIP_INFO_N=7
ID_FILENAME=/home/slartibartfast/Desktop/Music/iPod/F13/ADAV.mp3
ID_DEMUXER=audio
ID_AUDIO_FORMAT=85
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=0
ID_LENGTH=258.00
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=44100
ID_AUDIO_NCH=2
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
ID_AUDIO_CODEC=mad
Video: no video
Starting playback...


Exiting... (End of file)

---

