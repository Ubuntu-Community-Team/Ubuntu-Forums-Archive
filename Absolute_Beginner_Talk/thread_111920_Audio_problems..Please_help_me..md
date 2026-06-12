---
title: "Audio problems..Please help me."
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by ionizd on 2006-01-03
I have copied and am now pasting the last post from another thread I started ([http://ubuntuforums.org/showthread.php?t=101905]("http://ubuntuforums.org/showthread.php?t=101905")). They seem to be much too busy over there for Linux idiots like me. I hope I'm not breaking any rules by doing this. Here's the post:
I am still having problems playing video files. I get the same error as before, and I've nearly lost my mind chasing down different settings and options. Is there a way to get rid of all audio and video players, the entire sound system and any thing else associated with audio and video playback (sort of like uninstalling the device and using driver cleaner in windows), then starting a fresh install of the sound card drivers, the sound system and finally the players?

---

### Post by Gimbo on 2006-01-03
You might want to try downloading a package called debfoster (it should be there in Synaptic).

Once you've done that, type:
```
sudo debfoster
```
in a terminal window.

It will cycle through all your programs, asking whether you want to keep them. If you say no (n) to the media players you want to uninstall, it should be able get rid of all the packages that are only used by those players. Hopefully this will go some way to getting your computer "clean" of all the media stuff.

More info here: [http://ubuntu.wordpress.com/2005/09/30/better-management-of-packages-while-uninstalling/]("http://ubuntu.wordpress.com/2005/09/30/better-management-of-packages-while-uninstalling/")

---

