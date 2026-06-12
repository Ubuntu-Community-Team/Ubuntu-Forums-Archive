---
title: "can not play music videos - drm problem?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by vbdanl on 2007-01-17
Hi.  I am a ubuntu and linux newbie. -(  i have been trying everything under the sun to get my computer to play music videos from a radio station.  started out with totem, then installed mplayer and half dozen others.  also installed w32 codecs and most stuff from automatix.
when i go to [www.kzsn.com](www.kzsn.com) (local radio station) it has a link for playing on demand 1000's of music videos.  i have played them before from my xp at work and 98 machine at home.  when i select one with ubuntu, i get a gray screen with what appears to be html or some words about what is playing, but never any pictures.  i used to get sound, but now don't get that either, unless i select a sound only recording (not a video).
i am able to go to cnn.com and play news video broadcasts - get both picture and sound.
i went into another website, [www.cmt.com](www.cmt.com), and it gave me a message about my OS could not play the DRM's because of copyright laws.  i wasn't wanting to download them, just play them.  Anyway, since it actually gave me the error message, I was wondering if that is why I could not get the music videos from the local radio station also ?
I was also wondering if it is possible to run windows media player under wine, or if something like that would work ?
thanks.
danl

---

### Post by Zzl1xndd on 2007-01-17
I have ran into this as well, as far as Iv seen theres not much that can be done about it.

---

### Post by peterLinux on 2007-01-17
For what is worth...

I went to [www.kzsn.com](www.kzsn.com) and was able to play video's and sound.
The only thing is that the first video I selected didn't do a thing.
I picked randomly something else right from the mplayer plug-in
(a R.E.M. song) and that played fine... I clicked a couple others and all gave me video & audio

The other one is indeed in bed with M$... so no luck there (Damn DRM)

I use KUBUNTU 6.10 fully patched, upgraded etc
apt-get update
apt-get upgrade
and installed almost everything from automatix (incl mplayer)

Peter

---

### Post by vbdanl on 2007-01-18
I ran apt-get update and upgrade as suggested.  The update seems to pull in a lot of files, but the upgrade says there is nothing to do.  The update seems to miss 2 or 3 files, so I ran it twice.  The second time it missed different files than the first time.  Here is the tail end of what it displayed:
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 7B in 26s (0B/s) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Temporary failure resolving 'archive.canonical.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
dan@Dan-linux-Antec:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I was wondering how do I force mplayer to run when I select the music video?  I have nearly 20 programs listed under the sound&video tab, but am not sure which one is actually being used, or how to force it to use a specific one.  Also am not sure how do I know what "type" of file I will be reading in a given website, such as these music videos, are they .wmv or something else.. how do you know before you play, or does it matter?

I was going to insert a screenshot of my preferences under firefox, but am not sure how. when i cut and paste, i just got a link to my machine file location, not the actual screen.  did a preview, and it also just shows the words for the link, not the actual pic. 
Here are my preferences under firefox.. not sure if something needs changed or not:
Ext SPL opens with Shockwave
Ext QTL opens with QuickTime Plug-in 6.0/7
Ext WM opens with Windows Media Player Plugin
Ext WVX opens with Windows Media Player Plugin
Ext  FLI opens with mplayerplug-in 3.31

that is all that shows.
I selected 3 or 4 music videos, don't get sound or video from any of them.  I get a gray blank screen with the song title and artist name scrolling along the top.
any ideas?
thanks.

---

