---
title: "Video playback issues"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by nandan on 2007-08-24
I have been experiencing a strange video playback issue, right from the time i switched to ubuntu. Quite often, the video just does not show up in the player (vlc, movie player, mplayer etc.). If i minimize the window and then again click on it on the taskbar (sorry for the windows references, but I don't know what else they are called :) ) I can see graphics for about half a second, till the time the window 'pops up' from the task bar and comes in the front. Can't seem to make sense out of this behaviour. Could someone please help? This is true for almost all formats. Have no issues with sound (mp3, ogg) playback. Within the browser, I can play youtube videos.
Am on Pentium 4, 700 MB RAM and chipset integrated graphics device (Intel Brookdale)

Thanks.

---

### Post by nonewmsgs on 2007-08-24
your problem is with viewing videos online right?  are you using firefox?  does the same thing happen if you use opera?

---

### Post by nandan on 2007-08-25
Not really. As i mentioned, I can view videos on You Tube etc. even in Opera. But if I save a file to my computer and try to view it, I get this weird output.:confused:

---

### Post by Jose Catre-Vandis on 2007-08-25
run your player from the terminal with the -v option and report the output here.
e.g.

```
mplayer -v yourvideo.avi
```

Also, check your codecs, have you got win32s installed?

For info on installation either use Automatix ([www.getautomatix.com](www.getautomatix.com)) or look here [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by jordanmthomas on 2007-08-25
Are you using beryl / compiz?
If so, you should use X11 output in mplayer / vlc since you have integrated Intel.

(You can right click on an mplayer-plugin and go to properties to set this for firefox)

---

### Post by nandan on 2007-08-25
Hi Thanks for the suggestions...
@ Jose Catre-Vandis

This is what I get when I try to play experience ubuntu.ogg (after putting it on desktop) 

>  VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat experience
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000292] dvdnav demuxer warning: cannot open dvdnav
[00000295] vcdx access warning: Can't get file status for experience:
No such file or directory
[00000295] access_file access warning: experience: No such file or directory
[00000295] cdda access warning: could not open experience
[00000302] vcdx access warning: Can't get file status for experience:
No such file or directory
[00000302] access_file access warning: experience: No such file or directory
[00000302] cdda access warning: could not open experience
[00000290] main input error: no suitable access module for `experience'
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat ubuntu.ogg
No such file or directory
libdvdnav: vm: faild to open/read the DVD
[00000305] dvdnav demuxer warning: cannot open dvdnav
[00000306] vcdx access warning: Can't get file status for ubuntu.ogg:
No such file or directory
[00000306] access_file access warning: ubuntu.ogg: No such file or directory
[00000306] cdda access warning: could not open ubuntu.ogg
[00000307] vcdx access warning: Can't get file status for ubuntu.ogg:
No such file or directory
[00000307] access_file access warning: ubuntu.ogg: No such file or directory
[00000307] cdda access warning: could not open ubuntu.ogg
[00000304] main input error: no suitable access module for `ubuntu.ogg'
[00000281] main playlist: nothing to play
 
I transferred the file to desktop because I wanted it to start from the terminal...am pretty much n00b as far as CLI is concerned.
Where would I get the codec win32s? I read thru ubuntu documentation where they say that automatix 2 is not recommended..what do you suggest?

@jordanthomas
YEs, I am using beryl. I went thru VLC to find the output codec..I found X11, but I do not know how to select/activate it...
I went via Settings> Preferences>video> output modules>X11. There is a blank field at X11. Do I fill something here?

Again, thanks a lot for your help.

---

### Post by jordanmthomas on 2007-08-25
I didn't have vlc so I installed it.  I got the same problem...video opens, then vlc crashes.
Here's how I fixed it:
1.  Open vlc
2.  go to settings -> preferences
3.  make sure 'advanced options' is checked on the bottom right
4.  Click on the arrow beside Video
5.  Click the words on Output Modules
6.  In the right pane, select X11 Video Output in the dropdown box.
7.  I'm not sure if you need to restart vlc here, but I did.
8.  There is no 8

Unfortunately, you have to do this for every program that plays videos and they all have their own way of setting the option.

Anyway, a screenshot speaks a thousand words.

---

### Post by nandan on 2007-08-25
Wonderful! works like a particularly powerful charm!

Am unable to find the settings for mplayer, but since vlc can play so many formats, I guess this takes care of the problem!

Thanks to all once again.

---

### Post by jordanmthomas on 2007-08-25
for mplayer, you can do this:
1.  run gmplayer
2.  right click on controls and go to preferences tab
3.  accept the annoying popup warning.
4.  go to the video tab.
5.  Select x11 as your driver.
6.  restart mplayer.

For mplayer from command line:
```
mplayer -vo x11 /path/to/your/file
```

for mplayer-plugin
1.  right click on the plugin and go to its preferences / properties.
2.  Select your driver there (x11)
3.  reload the page with the video, and you should be set.


^^  in case you want to use mplayer some time.

---

### Post by nandan on 2007-08-26
Whaddaya know, even mplayer's working! :)
Thanks a lot...

---

