---
title: "XFmedia + MP3 Codec"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by ray.rogers on 2006-08-22
I need to get an MP3 codec for my XFmedia, so I don't have to use XMMS.  I dabbled with Automatix, as well as messing with my repositories in Synaptic to try to find one, but can someone just give me a package name I can apt-get?  I am looking for something simple, if possible.

---

### Post by Nick Garvey on 2006-08-22
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Install the package gstreamer0.10-plugins-ugly.
(sudo apt-get install gstreamer0.10-plugins-ugly)

---

### Post by ray.rogers on 2006-08-22
that didnt seem to work, any other ideas?

---

### Post by 3rdalbum on 2006-08-23
You didn't give much information. Did the package install? If it didn't, what error message did it give?

Are you sure you have enabled the Universe and Multiverse repositories? Do:

```
sudo nano /etc/apt/sources.list
```

Make sure all the lines with URLs in them don't have a "#" symbol before them. If they do, delete the #. When that's done, press Control-X, then the Y key, then the Enter key. Then type:

```
sudo apt-get update
sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by ray.rogers on 2006-08-23
I recived no errors when I did the first, and I followed your instructions and recived no errors.  If I load a few songs into xfmedia, and hit play, it just skips them all, like moves on, then on, then on, about every second.  Curious, eh?

---

### Post by whizbaby on 2006-08-29
> **ray.rogers said:**
> I recived no errors when I did the first, and I followed your instructions and recived no errors.  If I load a few songs into xfmedia, and hit play, it just skips them all, like moves on, then on, then on, about every second.  Curious, eh?

Had quite the same problem for a while 'til I found this page:

[http://wiki.ubuntuusers.de/Codecs](http://wiki.ubuntuusers.de/Codecs)

Basically they recommend to install libxine-extracodecs from multiverse because Xfmedia DOES NOT WORK AT ALL (quite a usefull information) with the gstreamer package.

After installing I experienced no further problems, so try it and run that Xfmedia to see if this resolves the problem. (you may have to install libxine-main1 first but perhaps it's done automatically, and for comfort install totem-xine (removes totem-gstreamer) so totem becomes useable too)

good luck!

---

### Post by whizbaby on 2006-08-30
Does not-posting-anymore mean you're cured?

---

### Post by psycosmyth on 2006-08-30
i concour whiz, I had the same issue, it cured my problem

---

### Post by ray.rogers on 2007-01-27
Greetings, again.
I have been using XP and Xubuntu back and forth since my origional post.  Every other time I go onto Xubuntu, I follow this thread for my music on another haddrive.  This time, however, it is not working.  I am not sure if it is a FAT32 or NTFS drive, maybe that is a cause?  Please help, this time it is not working,

---

### Post by Vomit-Orchestra on 2007-02-11
If you cannot see it on a windows partition this is generally because it's been formated to linux.
We are the cancer and the communists of the computer world.

---

### Post by whoscheesemine on 2008-03-17
Nothing on this thread got mp3's to work for me, however, a little googleing led me to this 

```
sudo apt-get install libxine1-ffmpeg

```

that worked fine

---

