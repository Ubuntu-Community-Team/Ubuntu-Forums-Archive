---
title: "mplayer plugin - no video"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by davidmaxwaterman on 2006-06-18
Hi,

I installed the mplayer plugin but when I use it to play a video, it only plays the audio.

Has anyone seen this problem before?

TiBook G4/800DVI.
Max.

---

### Post by oswaldkelso on 2006-06-19
Hi. I had some problems with video but using "easy ubuntu" 
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
and Automatix
[http://ubuntuforums.org/showthread.php?t=185604](http://ubuntuforums.org/showthread.php?t=185604) got it working for me.

 I counld'nt get it to work in all browsers. epiphany worked best opera not at all. 
I do get two video windows? and have to close one but apart from that it worked hope that helps

---

### Post by davidmaxwaterman on 2006-06-19
[QUOTE=oswaldkelso]Hi. I had some problems with video but using "easy ubuntu" 
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)
and Automatix
[http://ubuntuforums.org/showthread.php?t=185604](http://ubuntuforums.org/showthread.php?t=185604) got it working for me.

 I counld'nt get it to work in all browsers. epiphany worked best opera not at all. 
I do get two video windows? and have to close one but apart from that it worked hope that helps[/QUOTE]

I had used 'easy ubuntu' too, but it has limited PPC support. Automatix doesn't support PPC at all, the last time I checked.

:(

It was a little while ago - perhaps Easy Ubuntu is worth another try.

Max.

---

### Post by oswaldkelso on 2006-06-19
Automatix does support ppc :)

---

### Post by suoko on 2006-07-17
I have the same problem although I can see the video if I select "fullscreen" (right clicking on the video window in firefox, full-screen)

I had to configure video to X11 before

---

### Post by gThree on 2006-07-17
In Breezy, with the PPC G4 version, MPlayer and FF plug-in worked great.  In Dapper with just one version, not so much ... at least in my experience (Quicksilver G4 733, nvidia).

If you're trying to play latest WMV format, no way to get video in PPC AFAIK.

Otherwise, what suoko said usually works.  Right-click to access settings, make sure you're using xv (or x11), then right-click to select full-screen while playing a clip.  Video should appear.  Also, if you hit full-screen again, video will then sometimes play in page.

Other things I noticed in Breezy:  
Latest Apple trailers have visual artifacts = same in Totem/g-streamer and VLC, ffmpeg issue?  No idea.  But xine works fine.
Totem/g-streamer no longer plays .flv, while MPlayer does.
Gxine FF plugin now works.

So my solution was to switch to the gxine plug-in (or Kaffeine/xine) for FF.  I didn't try Totem/xine plug-in.

Should add that Kubuntu/Konqueror, in my experience, works better than FF for this sort of thing ... at least at the moment.

---

