---
title: "Use VLC to Play Videos in Firefox"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by PMatt on 2007-06-04
How do I get firefox to play videos with VLC? Totem doesn't work with WMV and some other formats, but vlc works fine.

---

### Post by luckyd on 2007-06-04
> sudo apt-get install mozilla-plugin-vlc :p

---

### Post by Michaelt74 on 2007-06-04
This may help, read from 'Multimedia codecs' onward.

Good luck!

---

### Post by Michaelt74 on 2007-06-04
Sorry, here's the link

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

### Post by PMatt on 2007-06-04
Nevermind, that link helped

---

### Post by daimaru on 2007-06-04
could you add the resolved flag to your post

---

### Post by PMatt on 2007-06-05
Is there anyway I can get VLC to embed in firefox? It works fine clicking on each video to launch them in VLC, but it's not very convenient.

---

### Post by PMatt on 2007-06-05
bump

---

### Post by komputes on 2008-03-12
bump - Firefox: how do I play all embedded content with VLC
(sorry if I hijack this thread but I believe opening a new one wouldn't help) Actually, I encourage everyone to leave a reply to this thread if they find a need for vlc to be included on ubuntu as a default player and can easily be integrated into firefox.

As we all know VLC is awesome :cool:  !!!

IMHO, VLC should be included with Ubuntu - it is THAT integral in my everyday process and makes the totem pole look like a stem. Since it can read all types of video/audio, how can it be that a user is unable to select it as a firefox plug-in for different types of files. I can't seem to specify how Firefox handles files with plugins, it is only showing Totem (see screenshot). 

I have already installed mozilla-plugin-vlc, yes I cannot access it from within firefox preferences.

---

### Post by mgmiller on 2008-03-12
You may need to uninstall totem-mozilla.  Look in synapatic for it.

Also, there is a fix for wmv in totem. 
I forget where I found this, but it will install a newer component of gstreamer that hasn't been backported to Gutsy yet.

---

### Post by wolfen69 on 2008-03-12
> **mgmiller said:**
> You may need to uninstall totem-mozilla.  Look in synapatic for it.

Also, there is a fix for wmv in totem. 
I forget where I found this, but it will install a newer component of gstreamer that hasn't been backported to Gutsy yet.

removing totem is a good idea. but i use mozilla mplayer for web, and it works great.

---

### Post by mgmiller on 2008-03-12
> **wolfen69 said:**
> removing totem is a good idea. but i use mozilla mplayer for web, and it works great.

Actually, I use the mediaplayerconnectivity extension for Firefox which lets me pick any of multiple players depending on file type, but this extension causes the videos to play in a separate window instead of embedding in the browser.

---

### Post by komputes on 2008-03-13
@mgmiller: I have tried media player connectivity. I want embedded video in the web page I am watching and not an external program. I also want this video to be handled by VLC (including flash video - .flv content). media player connectivity simply does not offer that.

@wolfen69: I completely removed totem from my system, including the mozilla plugin. All of a sudden, the vlc plugin was recognized but only on certain file types (see screenshot).

When changing .mov handling to VLC Multimedia Plugin, I see "(no video)" where the video should be (see screenshot #2).

When I open an OGG or MP3, they are downloaded instead of played (even though I told firefox to handle them with the VLC Multimedia Plugin)

---

### Post by mgmiller on 2008-03-14
I just tried a trailer at the apple web site and it plays embedded just fine using Totem as the default player.  
Since you have removed Totem from your system, did you try the mozilla-mplayer plugin as wolfen69 suggested?  You would have to uninstall the vlc-mozilla plugin first.

---

### Post by komputes on 2008-03-14
> **mgmiller said:**
> I just tried a trailer at the apple web site and it plays embedded just fine using Totem as the default player. 

Since the title of the post is "Use VLC to Play Videos in Firefox", i was guessing you would understand that I am trying to force everything to go through the mozilla vlc plugin, so that everything embedded would be handled by VLC Multimedia Plugin (mozilla-plugin-vlc), not mplayer, gstreamer, totem or a firefox add-on or VLC as an external application.

---

### Post by 300890 on 2008-04-07
> **komputes said:**
> Since the title of the post is "Use VLC to Play Videos in Firefox", i was guessing you would understand that I am trying to force everything to go through the mozilla vlc plugin, so that everything embedded would be handled by VLC Multimedia Plugin (mozilla-plugin-vlc), not mplayer, gstreamer, totem or a firefox add-on or VLC as an external application.
The mozilla-mplayer plugin works fine for me :-)


```
sudo apt-get install mozilla-mplayer
```

---

### Post by komputes on 2008-04-07
The mozilla-mplayer plugin works. I know this, but I want to force VLC to handle all media within firefox.

---

