---
title: "DVD Plug in problem."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Snoo on 2007-05-13
Hi Folks.

I've been trying to get Fiesty to play DVD's in Totem. I followed the advice page from[url:https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs] here[/url] and I installed libdvd thingy. However no I get a message saying that totem doesn't have the correct plug-in to play the dvd. But no extra clues as to what that plug-in may be.

Can anyone help?

I'm using feisty/Ubuntu/Totem 2.18.1 and the DVD is an original in standard format.

Cheers folks.

---

### Post by Snoo on 2007-05-13
I've also tried everything in the multimedia sticky at the top of the forum.

One dvd telling me it doesn't have the required plug in. The other says it still needs libdvdcss..

---

### Post by Snoo on 2007-05-14
Anybody?? :confused:

---

### Post by aeiah on 2007-05-14
did you install all 3 packages mentioned? libdvdread3, libxine1-ffmpeg, and libdvdcss2

---

### Post by meborc on 2007-05-14
also try to install vlc and play it with that... vlc is powerful player - it can play anything from broken media files to music...

also go to [www.ubuntuguide.org](www.ubuntuguide.org) and read about the dvd playback!

---

### Post by lakersforce on 2007-05-14
I believe that Canonical have recently disabled all support of css encrypted DVD'sand Windows Media Formats files.

---

### Post by meborc on 2007-05-14
but that does not mean that we can't watch dvd's on ubuntu anymore... :)

---

### Post by lakersforce on 2007-05-14
Well, I have libcss2, w32_codecs and vlc installed and I still cant watch it, so that would be a...yes?

---

### Post by meborc on 2007-05-14
hmm, you make me worried... can't test it now... will try later and report back... :(

---

### Post by Snoo on 2007-05-14
> **aeiah said:**
> did you install all 3 packages mentioned? libdvdread3, libxine1-ffmpeg, and libdvdcss2

Hi, yes I installed everything as directed. Still no joy.
I'll try VLC later when I get home and see if that works. Could there be this other issue then?

Cheers guys.

---

### Post by aeiah on 2007-05-14
> **Snoo said:**
> Hi, yes I installed everything as directed. Still no joy.
I'll try VLC later when I get home and see if that works. Could there be this other issue then?

Cheers guys.

vlc and (as far as i know) mplayer both run differently to other media players. they have dvd codecs built in and thus should play your dvds without the other codecs. i find mplayer plays them better but i always seem to be plagued with audio errors when using mplayer, and i suggest installing vlc first and seeing how you go

---

### Post by esoterica on 2007-05-14
I had a simular post going in another forum here, same problem, sort of, at least getting the same error message about not having the correct plug ins installed.

I tried to follow some other advice around here and all of it turned out to be bad advice, did find a working solution to the problem though on another message board. Turned out that it had nothing to do with the plug ins at all even though thats what the error was telling me.

I posted the solution that worked for me here...

[http://ubuntuforums.org/showthread.php?p=2651494#post2651494](http://ubuntuforums.org/showthread.php?p=2651494#post2651494)

---

### Post by Big_Croc7 on 2007-05-14
Another one I'd recommend is gxine - it uses the same engine (gstreamer) as totem, but it handles DVDs better.  Totem, in particular, can't handle DVD menus (at least the older versions - don't know about the version in feisty).  Usually this isn't a problem, as it just starts playing the actual film to start with, but it might be an issue with a badly-configured disc.

---

### Post by meborc on 2007-05-15
> **esoterica said:**
> I had a simular post going in another forum here, same problem, sort of, at least getting the same error message about not having the correct plug ins installed.

I tried to follow some other advice around here and all of it turned out to be bad advice, did find a working solution to the problem though on another message board. Turned out that it had nothing to do with the plug ins at all even though thats what the error was telling me.

I posted the solution that worked for me here...

[http://ubuntuforums.org/showthread.php?p=2651494#post2651494](http://ubuntuforums.org/showthread.php?p=2651494#post2651494)

this has nothing to do with the problem in this thread... as the players eved don't recognize dvd's... no sound no nothing... problems with self-compiled compiz/beryl and resulting video blackness is a common problem... what we are seeing here is just plain not recognizing / not playing dvd's

can't test - don't have any dvd's at home... but really worried :) will try later

---

### Post by Snoo on 2007-05-15
As an update I just tried VLC. Er... It doesn't seem to just play like Totem.

I have to go into the file system and select the cdrom drive. The it shows the video file, then I have to select all the files and open them. Then it locks up!!!

I'm guessing there is an easier way huh?  :confused:

---

### Post by chamberlain2006 on 2007-05-15
Totem works fine with DVD's.  I installed totem-xine and libxine-extracodecs, as well as libdvdread3 libdvdplay4 (i think it's 4) and libdvdcss2.  The menus works great and I've had no problems in Dapper, Edgy, or Feisty (with Compiz running).

---

### Post by Snoo on 2007-05-21
Anybody got anymore ideas on this? I am still unable to play DVD's.. :(

---

### Post by bramvandijk on 2007-05-23
I use VLC, but it takes a little trick to get VLC to play a dvd.

You should click
file -> open directory

Now, navigate to the dvd, in feisty it is mounted in /media/NAME_OF_THE_DVD
where the NAME_OF_THE_DVD is the name of the movie.

The dvd will have 2 subdirectories, AUDIO_TS and VIDEO_TS, select the video one, and click OK.

Now it will start to play the movie, and you will have complete menu capabilities.

Note that I am currently on a windows PC, and therefore I could be making small mistakes.

Another thing that works for me is Ogle, and Ogle-gui.

In Ogle you have to select the dvd mount point (not the video_ts subdirectory as with vlc) and plays OK. The problem I have with ogle is that it doesn't disable the screensaver, and thus every five minutes the screen goes black, unless you move the mouse.

Hope this helps...

---

### Post by Snoo on 2007-05-24
Thanks my friend. I'll give that a go next.

---

### Post by Snoo on 2007-05-24
VLC crashes and dissapears immediately when I try that! :(

---

### Post by Snoo on 2007-05-24
Ogle also crashes... Woe is me!

---

### Post by Snoo on 2007-05-24
Update:
I reinstalled Totem (xine backend) and now it appears to play.

Picture seems to lose it slightly with fast motion. Is this a refresh rate problem??

---

### Post by erat123 on 2007-05-30
got it! from ubuntuguide.org...

install this stuff:
[B]sudo aptitude install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good \
gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
[/B]

and then install this:
**sudo aptitude install w32codecs**


it worked very well for me! hope it works out for everyone else! :popcorn: time for an all nighter family guy marathon!!

---

### Post by meborc on 2007-06-05
i did this - [http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux) and now watching italian job (1969; michael caine)

---

