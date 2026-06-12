---
title: "Wma Files"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by gettinit on 2008-04-17
OK,
I have installed amarok, all the plug ins I could find and I still can't play all my files. I can play about a third of them and the rest I get an error message. 

Also when I go directly to the file and click on the song I want it opens the movie player, to get anything to work I have to open amarok and get the file form there. 

Any ideas?

---

### Post by benson444 on 2008-04-17
Try installing the w32codecs using the codes here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I always install vlc and mplayer as they seem to play most things. Then right-click a file > properties > open with, and change it to amarok or what ever you want.

---

### Post by gettinit on 2008-04-17
Ok installed both and I still get an error message saying no available decoder and then the location of the file?

---

### Post by bumanie on 2008-04-17
Can you cut and paste the exact error message and post it. Knowing the exact error may help. You could also try > sudo apt-get install restricted-extras

---

### Post by gettinit on 2008-04-17
-The movie player said:
The playback of this movie requires a audio/x-asf-unknown decoder plugin which is not installed.
 

-I nstalled the vplayer and it looks like its reading it but no sound.

amarok says:

There is no available decoder.
file:///media/disk/Documents and Settings/mattdaniels/My Documents/My Music/Bailey Rhodes Band/Bailey Rhodes Band/02 Track 2.wma


Am I missing an audio plug in?

---

### Post by gettinit on 2008-04-17
Also how do I create a link to my Music Folder from my desktop so its easier to get to?

---

### Post by benson444 on 2008-04-17
Do you have ffmpeg and gstreamer0.10-ffmpeg installed? Maybe try mplayer if you haven't already.

You can make a link by right-clicking > make link, and then drag it to the desktop.

---

### Post by bumanie on 2008-04-17
Ensure you have medibuntu added to your /etc/apt/sources.list (I think that was already suggested). Then try this code in terminal
> sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

---

### Post by timcredible on 2008-04-17
is the file drm'd (encrypted)?  i mean, did you buy it from someplace online?  except for emusic and amazon's newly re-done mp3s, they're all encrypted and you can only play them on the machine you used to buy them - they won't even play on another windows machine.  fwiw, the new amazone mp3s that are unencrypted are very good quality 256Kbps recordings.

---

### Post by thiebaude on 2008-04-17
You can drag and drop your music folder from the Places menu right onto your desktop.

---

### Post by SunnyRabbiera on 2008-04-17
there is the chance that you have a DRM'ed file, there is nothing we can do for you there.
WMA is known to work in linux, I know I got it working but you have to consider DRM

---

### Post by gettinit on 2008-04-17
Bumanie:
I have installed the medibuntu from earlier and then tried your package and got this message.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate


I tried the mplayer and still nothing. 

, I ripped it from cds using Windows media player on the xp side of my machine 

Im using a Dual boot machine so I am trying to play music from that file on the Ubuntu side of my machine. Is that my problem?
If so I still don't understand why I can play some of the files...

BTW, thanks for all of your help. I enjoy using  ubuntu and am really trying to phase out the other side of my machine!

---

### Post by gettinit on 2008-04-17
Don't know what DRM'ed is...

---

### Post by SunnyRabbiera on 2008-04-17
what version of windows media player might I ask?
I know newer versions of WMP encrypt their files, and use the newer WMA format.

and DRM= digital rights management
look it up here:
[http://en.wikipedia.org/wiki/Digital_rights_management](http://en.wikipedia.org/wiki/Digital_rights_management)

---

### Post by gettinit on 2008-04-17
Verison 11

---

### Post by gettinit on 2008-04-17
Well that has to be what it is then, but I still don't understand why I can play some of them...

---

### Post by SunnyRabbiera on 2008-04-17
then there lies most of your problem.
You see the files WMP 11 encodes in WMA will only work for WMP11.
If possible you can just re load those disks and re rip them.
I know it sounds annoying but its your best bet, re rip the disks to .ogg or even MP3's, you will be better off....
heck MP3 is more open source friendly these days then WMA

---

### Post by gettinit on 2008-04-17
Well crap so they, are trying to encode it specific to the windows player similar to the way apple was using I tunes. Thats why I was using the Windows player!  Ugg... 

Well can you recommend a media player that I can use in both ubuntu or WMP?

Or are you saying rip them again just with  the file ext. MP3?

---

### Post by SunnyRabbiera on 2008-04-17
well you can use VLC in windows, it can actually handle WMA 11 files on windows and you can convert them to MP3's using that as it has a audio/video converter...
just keep in mind it is not perfect.
But your best bet is to re rip the CD's, really you are better off.
as for the file format, yes you can use sound juicer one of the apps for CD ripping to convert your files to MP3 on linux providing you have all that is needed.
I know I can do that

---

### Post by gettinit on 2008-04-17
I'll probably just re-rip. for sake of saving space can I rip them in linux and then play them using WMP on the XP side of my machine.

---

### Post by SunnyRabbiera on 2008-04-17
Sounds feasible, you can see your linux drive in windows correct?

---

