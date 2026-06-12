---
title: "Audio stopped functioning in my Ubuntu 7.04"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-07
Until two days ago, the audio was working fine on the Youtube site. Now when the computer boots up, the usual Ubuntu 7.04 brief music does still play when the screen appears. But if I go to Youtube, no audio plays.

If I put in an mp3 CD the OS recognizes it fine and the disc mounts on the desktop. And if I open the gnome Rythm Box Music Player, it recognizes the CD as an mp3 disc and lists the files on the disc properly. It tries to start playing but the counter never moves from 0:00 and the play function switches over to pause. No sound ever comes.

If I open the Audacious music player, it says "The following files could not be played. Check that (1) they are accessible; (2) you have enabled the media plug-ins required." Well, I believe the files are accessible because the disc is successfully mounted on the desktop and both the above audio programs are recognizing the files. 

I never tried these above audio programs before today, but I know the audio was playing fine in any Youtube video until 2 days ago. Now no audio comes at all in Youtube, and nor does it come in either of the two audio applications above.

I've already downloaded the following, if anyone would say they are needed:

MPlayer
VLC media player
"Ubuntu restricted extras"
libdvdcss2, libdvdplay, libdvdnav, and libdvdread
w32 codecs

What do I need to do to get my audio working again?

---

### Post by Crafty Kisses on 2007-06-07
> **swarup said:**
> Until two days ago, the audio was working fine on the Youtube site. Now when the computer boots up, the usual Ubuntu 7.04 brief music does still play when the screen appears. But if I go to Youtube, no audio plays.

If I put in an mp3 CD the OS recognizes it fine and the disc mounts on the desktop. And if I open the gnome Rythm Box Music Player, it recognizes the CD as an mp3 disc and lists the files on the disc properly. It tries to start playing but the counter never moves from 0:00 and the play function switches over to pause. No sound ever comes.

If I open the Audacious music player, it says "The following files could not be played. Check that (1) they are accessible; (2) you have enabled the media plug-ins required." Well, I believe the files are accessible because the disc is successfully mounted on the desktop and both the above audio programs are recognizing the files. 

I never tried these above audio programs before today, but I know the audio was playing fine in any Youtube video until 2 days ago. Now no audio comes at all in Youtube, and nor does it come in either of the two audio applications above.

I've already downloaded the following, if anyone would say they are needed:

MPlayer
VLC media player
"Ubuntu restricted extras"
libdvdcss2, libdvdplay, libdvdnav, and libdvdread
w32 codecs

What do I need to do to get my audio working again?
You can try uinstalling the codecs and drivers you installed, and see if it works then. :-?

---

### Post by swarup on 2007-06-07
> **Codename said:**
> You can try uinstalling the codecs and drivers you installed, and see if it works then. :-?

Why would that help?

I also wanted to mention that I've also downloaded and installed these:

GStreamer extra plug-ins (codecs to play mp3, sid, mpeg1, mpeg2, AC-3, DVD (without encryption)
GStreamer ffmpeg video plug-in (codecs to play mpeg, divx, mpeg4, AC-3, WMV, and asf files)
GStreamer plug-ins for mms, wavepack, quicktime, musepack (codecs to play)

So I do not see why anything would be missing, for playing audio. Does anyone have any further ideas? Do others also think it would be worthwhile to try uninstalling and reinstalling all the codecs?

---

### Post by swarup on 2007-06-07
I wonder whether the audio could have been disabled or "turned off" somehow. I would know how to check for this in Windows, but I have no idea how to do so in Ubuntu. Is it a possibility that this could have happened, and is there a way to check?

---

### Post by Crafty Kisses on 2007-06-07
> **swarup said:**
> Why would that help?

I also wanted to mention that I've also downloaded and installed these:

GStreamer extra plug-ins (codecs to play mp3, sid, mpeg1, mpeg2, AC-3, DVD (without encryption)
GStreamer ffmpeg video plug-in (codecs to play mpeg, divx, mpeg4, AC-3, WMV, and asf files)
GStreamer plug-ins for mms, wavepack, quicktime, musepack (codecs to play)

So I do not see why anything would be missing, for playing audio. Does anyone have any further ideas? Do others also think it would be worthwhile to try uninstalling and reinstalling all the codecs?

Well you did say it stopped working 2 days ago, so you should try to uninstall the stuff you installed, and see if it works after everything is gone, I was just trying to give some advice, also is this before or after you installed the drivers?

---

### Post by swarup on 2007-06-07
> **Codename said:**
> Well you did say it stopped working 2 days ago, so you should try to uninstall the stuff you installed, and see if it works after everything is gone, I was just trying to give some advice, also is this before or after you installed the drivers?

I've all these drivers installed for several weeks. 

However one thing I did do around two days ago or so--until then the audio had been working fine but video was not working quite right and I wasn't sure whether it was because I have a slow computer (celeron 433 mhz, Ram 288 MB) or because the video wasn't yet set up right. So I had gone to an Ubuntu guide webpage where it gave terminal command lines for installing two or three items like libdvdcss2 and a couple other items. So I entered those lines in terminal. I'm not sure whether the audio problems started after that or not, or because of that or not. All these things are so complex and beyond what you can analyze that it's all just a sort of guesswork like trying to maneuver around deep down in some dark cave with no lights.

---

### Post by swarup on 2007-06-07
I just tried playing the mp3 in Totem movie player and it opens fine and the whole program acts like it is playing the track. The counter is counting and the progress bar moves. And no error message.   .....but no sound!

And audacity also imports the mp3 file just fine and shows the entire file's wave form. But no sound.

Any ideas?

---

### Post by swarup on 2007-06-07
There must be a way to check and see if the sound has been disabled. How can I check for that?

---

### Post by durrell on 2007-06-07
Open a Terminal window and type "alsamixer". Check to make sure they aren't muted, or turned way down. That's how I fixed my laptop sound problem. If you see MM under any of the bars, that means they're muted.

---

### Post by swarup on 2007-06-07
> **durrell said:**
> Open a Terminal window and type "alsamixer". Check to make sure they aren't muted, or turned way down. That's how I fixed my laptop sound problem. If you see MM under any of the bars, that means they're muted.

All the lines are way up high, except two which are on MM. I don't know how to unmute them, and I also don't know whether they matter. They are the "3D Contr" lines.

---

### Post by marym on 2007-07-09
I too have had the problem of sound not working.  I ran alsamixer in terminal and two bars have MM.  Now I know they are nothing to do with my name, but there was no response to the previous poster's question.  

How do you "unmute" the sound?

---

