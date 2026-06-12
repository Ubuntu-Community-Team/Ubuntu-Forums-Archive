---
title: "ipod..."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Lisa Y on 2008-02-22
does anyone know of the top of there heads...a program that i can use...to pull music outta my ipod...to my desktop..or to my music folder.....

the thing is...that a year ago...or sometime..i put a cd into my ipod...now that i lost it...::sigh:: i wanted to see if i could make a copy of that cd...but...i cant seem to find one to install on 7.10 that allows me to do that... 


oh btw...my ipod is formated with my windows.....

thanks guys!

---

### Post by Therion on 2008-02-22
[GTK Pod]("http://www.ilounge.com/index.php/ipod-software-linux") should do the trick.

---

### Post by lifewithryan on 2008-02-22
I think I'm slight mis-understanding you...

if
1) you are trying to get your music off the pod, I'd use Banshee.  However, if the stuff is DRM'd then it won't do you any good unless you play it in iTunes.  (But since it was YOUR disk, perhaps the DRM doesn't come into play, I can't remember.

Anyway, if that is the case, here's what ya gotta do.
```

sudo apt-get install banshee

```

That should install the banshee music player.  When it installs, fire it up and then plugin your iPod.  it should detect it.  Select the ipod and start searching for your music.  Banshee will show you the list of songs.  Find the song that you want and right click on it.  It "should" show you the name of the file and I believe the location...(sorry its been a while).
Then you can navigate to the iPod via the file system, (after all its just a hard drive) and then copy the file off the pod to a directory somewhere....HOWEVER, here's the kicker...the file will be named something like XXXX.mp4 (or similar).  After moving it, i'd rename it to make sure you know what it is on your file system.  Once you have them all, you should be able to burn then to an audio cd with any of the numerous tools for linux.

Hope that helps.  I had to use my iPod to restore my iTunes after my mac crashed and thank god I'm a linux user because this saved my purchased collection.

---

