---
title: "Need some help with a few things"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by bmoney017 on 2006-06-12
So I decided to build a new computer and put ubuntu on it. Everything was running great, until I started to do a few things. I wanted to update firefox, but when I went into the update file I couldnt get anything to work. I tried clicking on the 'updater' thing, but nothing happened, because ubuntu did not know which app. to use. Same thing happened when I tried to install flash player.

My second problem is trying to playback AVI and WMV files. An error message comes up saying, "There were no decoders found to handle the stream, you might need to install the corresponding plugins". Any help would be great

---

### Post by Nikusan on 2006-06-12
[QUOTE=bmoney017]So I decided to build a new computer and put ubuntu on it. Everything was running great, until I started to do a few things. I wanted to update firefox, but when I went into the update file I couldnt get anything to work. I tried clicking on the 'updater' thing, but nothing happened, because ubuntu did not know which app. to use. Same thing happened when I tried to install flash player.

My second problem is trying to playback AVI and WMV files. An error message comes up saying, "There were no decoders found to handle the stream, you might need to install the corresponding plugins". Any help would be great[/QUOTE]

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by taurus on 2006-06-12
You are using the latest version of firefox so what do you want to upgrade to what!  If you want to check to see if there is any update or not, open a terminal by clicking Applications -> Accessories -> Terminal and type
```

sudo apt-get update
sudo apt-get upgrade

```
And for your flash plugins and codecs, use Automatix to install all that and more.  Here's the link for Automatix...
[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by bmoney017 on 2006-06-12
I am using two different computers. The one which I want to update has firefox 1.0.7 or something like that. My XP laptop has the current version of firefox. Ill read over the stuff you guys gave me and try and go from there. Thanks

---

### Post by Nikusan on 2006-06-12
[QUOTE=bmoney017]I am using two different computers. The one which I want to update has firefox 1.0.7 or something like that. My XP laptop has the current version of firefox. Ill read over the stuff you guys gave me and try and go from there. Thanks[/QUOTE]

Are you running Ubuntu 6.06 (dapper drake)?

---

### Post by taurus on 2006-06-12
There is an update for firefox, 1.5.0.4, if you are running Dapper...

---

