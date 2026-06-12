---
title: "[SOLVED] Getting Nomad jukebox zen to work under banshee"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-20
Hi, banshee recognizes it but I cannot copy from it or sync with or anything. all the files on it are grayed out, I cannot play them. Any body care to give a head? In the mean time I will try out Gnomad...

Static Void

EDIT:  People, if you need your jukebox zen syncronized then run this command in the terminal:  sudo apt-get install gnomad2
then just insert you password.

before launching gnomad2 plug in your jukebox and then... your on your way to making playlists and adding delting stuff from your juke box :D

---

### Post by staticvoid on 2007-09-20
Ok wow... Gnomad2 works perfect. Gee, I'm embarrest: would some one please delete this post, lol.

....Static Void

P.s. this could be a HOW-TO  :D I'll edit the post above

---

### Post by papajew on 2007-10-28
Hi I am completely new to ubuntu.  I have an older model nomad jukebox zen mp3 player.  I loaded gnomad2.  It recognizes the jukebox and it see's teh music files on my computer but it doesn't transfer the files.  I have them in mp3 format which has worked in teh past, and when I select the files and hit the add arrow it says it's transfering but when I check the playlists or all tracks listing the tracks don't show up and they don't show on the jukebox either.  Is there an allternative or workaround for this issue?

---

### Post by staticvoid on 2007-11-06
go to add/remove... and  search for gstreamer. add all the codecs :) maybe that might work... also, check for the latest version of gnomad2. Maybe google alternatives?
[http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)

sv

---

### Post by tajunta on 2007-11-10
> **papajew said:**
> Hi I am completely new to ubuntu.  I have an older model nomad jukebox zen mp3 player.  I loaded gnomad2.  It recognizes the jukebox and it see's teh music files on my computer but it doesn't transfer the files.  I have them in mp3 format which has worked in teh past, and when I select the files and hit the add arrow it says it's transfering but when I check the playlists or all tracks listing the tracks don't show up and they don't show on the jukebox either.  Is there an allternative or workaround for this issue?

I had the same problem and boy I spent time trying to figure it out. First I did what was told above about the gstreamer plugins, didn't work with that alone but I found out that the playlists (and possibly other data files that are not mp3) you might have on your jukebox do not work, so I removed all playlists and data files, only leaving the mp3s there. Now the transfer doesn't freeze and it works allright. 

I haven't tried making a playlist with Gnomad2 now, I'll try if it works too. I would think that you can make a playlist, just the old ones on the jukebox made it crash.

---

