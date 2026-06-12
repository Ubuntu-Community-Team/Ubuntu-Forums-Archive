---
title: "Rhythmbox MP does not play &quot;MP3&quot; files"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2007-01-09
When I try to play MP3 files with Rhythmbox Music Player I get the error message:
> The GStreamer plugins to decode "MP3" files cannot be found.
I have installed:

gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-a
gstreamer0.10-plugins-good
gstreamer0.10-tools
gstreamer0.10-x

What am I missing?

---

### Post by jem7v on 2007-01-09
I'd guess it's in one of these four:
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse

Read this page for a little more information: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mlissner on 2007-01-09
Also, you might try installing the xine engine for music stuff. I heard it was less buggy as far as music skipping stuff.

---

### Post by jem7v on 2007-01-10
This is also true, I think.  I use the xine engine and listen to my music in Amarok instead of Rhythmbox.

---

### Post by mykalreborn on 2007-01-10
my advice for you is to use amarok:[link]("http://amarok.kde.org/") or exaile:[link]("http://www.exaile.org/trac"), if you don't like kde. and install automatix:[link]("http://www.getautomatix.com/"), so won't have to worry about what engine to use and what-not. ;)

---

### Post by Sef on 2007-01-10
> my advice for you is to use amarok:link or exaile:link, if you don't like kde. and install automatix:link, so won't have to worry about what engine to use and what-not.


Easiest way to install amarok is this:  Applications > Add/Remove > Sound and Video > amarok.   All the dependencies will be downloaded.

For Rhythmbox, read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by mykalreborn on 2007-01-10
> Easiest way to install amarok is this: Applications > Add/Remove > Sound and Video > amarok. All the dependencies will be downloaded.

oh, yeah! you're right:D

---

### Post by Cariboo1938 on 2007-01-10
> **jem7v:** I'd guess it's in one of these four:
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverseRead this page for a little more information: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)NOW IT WORKS
:-\" Thanks jem7v. 
I used ```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
 gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
 gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 
 libxine-extracodecs ogle ogle-gui
``` 
because I could not figure out which file only would do the trick!

---

### Post by jvc26 on 2007-01-10
lol often the easy way to do things - itll tell you which it needed to/didnt need to install when you enter the command and does it itself :)
Il

---

### Post by dandesigns on 2007-09-17
Thanks for the posts. It helped me play MP3's on Rythmbox on my Ubuntu Feisty Fawn.

these packages did the job:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

// Before that, I already tried installing almost all the gstreamer plugins(except the ugly) and the MediBuntu packages but still no go for RythmBox.

---

