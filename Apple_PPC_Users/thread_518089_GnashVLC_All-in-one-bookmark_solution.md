---
title: "Gnash/VLC All-in-one-bookmark solution"
date: 2007-08-05
forum: Apple PPC Users
---

### Post by Ripfox on 2007-08-05
Ok, so no joy with Gnash 0.8.0 as far as youtube in browser, (yes I installed the moz-plug) So, I tried to use video downloader or all-in-one-bookmark thing and save it to desktop. Renamed it .flv, opened it with VLC, one...two...crash. No love.

Any ideas?

Peace

---

### Post by stmiller on 2007-08-05
Type
```

about:plugins

```
in Firefox and make sure it states the Flash version as 0.8.0

---

### Post by Ripfox on 2007-08-06
Yes it's right...just crashes when I try to play an .flv file in VLC.

---

### Post by Ripfox on 2007-08-14
bump

---

### Post by oswaldkelso on 2007-08-17
If I need to watch youtube video I either use democracy player (now called miro) to down load them or just type kiss infront of the youtube address.e.g

[http://www.youtube.com/watch?v=yVFekhVYCMU](http://www.youtube.com/watch?v=yVFekhVYCMU)

[http://www.kissyoutube.com/watch?v=yVFekhVYCMU](http://www.kissyoutube.com/watch?v=yVFekhVYCMU)


scroll down, right click and save as debian.flv or something. then open with vlc

this method works more better than most but does take away your control.


note this clip has no sound

---

### Post by Ripfox on 2007-08-17
You see, the problem is not obtaining the clips. VLC crashes when you try to play them. I have the latest gnash, and mozilla plugin. Also, Democracy player will not play the videos it downloads.

---

### Post by Ripfox on 2007-08-20
bump

---

### Post by Ripfox on 2007-08-20
As stated, getting the video downloaded is not the problem. VLC crashes with this:

Illegal instruction (core dumped)

And yes I have all the codecs, I am 90% positive, + Gnash 8 and the mozilla plugin for it.

:confused::confused:

---

### Post by Auria on 2007-08-21
Perhaps try another player than VLC?

---

### Post by Ripfox on 2007-08-21
Same results...

cmon' anyone???:):):)

---

### Post by Auria on 2007-08-21
> **ripfox said:**
> Same results...

cmon' anyone???:):):)

If all media players crash then this probably indicates a bug in the underlying library - you should try to identify which library plays flv files, if all players that crash use it, and if so report a bug report there (making sure you have a recent version first of course)

---

### Post by joninkrakow on 2007-08-22
I don't bother with Gnash or VLC. I use the commandline youtube-dl tool, downloading the files via the command line, and watch the files in the default video player. It's worked fine for me. In fact, in my experience, this is the fastest way to download YT videos, and you can watch them at your leisure. It may also be possible that VLC will play these files as well. A quick Google should show you youtube-dl. (It's a perl script, so nothing complicated)

-Jon

---

### Post by Ripfox on 2007-08-22
OK...once again it's not downloading the videos I have a problem with. As far as identifying the library that actually plays .flv, I will need some guidance with that.

---

### Post by yousufinternet on 2007-08-22
try to install gstreamer packages using synaptic package manager and play the flv files using totem the defualt player in gnome :)

---

### Post by Ripfox on 2007-08-22
Ugh...totem won't play them either, I tried that a long time ago. I have the gstreamer packages installed shortly after I install Ubuntu.

---

### Post by Auria on 2007-08-22
> **ripfox said:**
> As far as identifying the library that actually plays .flv, I will need some guidance with that.

You may want to list precisely what players you have tried and crashed - VLC alone is not sufficient to draw conclusions

BTW it's Feisty you're using?

---

### Post by Ripfox on 2007-08-23
Feisty, yes. Totem, Mplayer,VLC have all been used.

---

### Post by Auria on 2007-08-23
> **ripfox said:**
> Feisty, yes. Totem, Mplayer,VLC have all been used.

hmm okay... well maybe someone else knows about them more than i do. if no one does you can always ask them and they can redirect you to the correct place to file a bug report

meanwhile i don't understand why it crashes for you and no one else...

---

### Post by joninkrakow on 2007-08-24
> **Auria said:**
> 
meanwhile i don't understand why it crashes for you and no one else...

This is why I suspect that his problem is the files he is downloading. I suspect that they are corrupt. Do you have access to some other system, either Mac or Windows? My flv files I've downloaded not only play on Ubuntu, but also on my Mac. 

This, btw, is why I suggested trying the youtube-dl script. It's for a control group, to see if maybe the files you are downloading are not right, somehow. 

And, btw, if this doesn't work, there's nothing more I can offer. 

Something is wrong with your system--something is corrupted. You've stumped us all, it would seem...

-Jon

---

### Post by stmiller on 2007-08-24
Have you trying using Automatix, other 3rd party repos, or anything else that would possibly break your system? Installed debs from somewhere else? Your system has a conflict.

Have you tried different flash video files? Can you play youtube files okay? Play other types of video okay?

Just start troubleshooting.

---

### Post by Ripfox on 2007-08-24
I have not used Automatix, as Automatix does not support ppc. I have tried .flv files from various sources, same result in any player. Core Dump.

I know the process of troubleshooting, I have been on Linux for a year solid. I just can't see a way out of this, so I guess time to reinstall.

---

### Post by stmiller on 2007-08-24
This person may be having similar problems:

[http://ubuntuforums.org/showthread.php?t=533078](http://ubuntuforums.org/showthread.php?t=533078)

EDIT: Also, is alsa/sound working okay? Does a CD playback? alsamixer comes up ok? What model of mac do you have?

---

### Post by Ripfox on 2007-08-26
Sound works fine, and it's a blue/white imac (g3?)

---

### Post by andi666 on 2007-08-27
Video playback on G3 is broken since Ubuntu 6.06, this also affects Gnash and VLC.

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/74282](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/74282)

andi

---

### Post by Ripfox on 2007-08-27
Ah I see, how did I miss this...:(

---

### Post by Auria on 2007-08-27
> **andi666 said:**
> Video playback on G3 is broken since Ubuntu 6.06, this also affects Gnash and VLC.

[https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/74282](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/74282)

andi

I think you mean 6.10

but yeah this is probably the problem, unfortunately

---

### Post by andi666 on 2007-08-27
> **Auria said:**
> I think you mean 6.10


Oh, yeah, I mean 6.10, sorry.
The bug is really a well known ppc bug, and even though powerpc was a "supported" architecture for ubuntu 6.10, nobody seemed to care.
And I dont think this will be fixed in 7.10.

---

