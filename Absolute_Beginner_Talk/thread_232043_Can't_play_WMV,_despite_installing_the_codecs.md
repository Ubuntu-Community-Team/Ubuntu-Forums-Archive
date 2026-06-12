---
title: "Can't play WMV, despite installing the codecs"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by Sirron on 2006-08-08
So far, very impressed with Ubuntu Dapper.

However, I can't seem to play WMVs. I followed the instructions on this page [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats), and installed all the gstreamer plugins, and the w32codecs.

But when I try to open a WMV file in Totem, it reckons:

"You do not have a decoder installed to handle this file. You might need to install the necessary plugins."

And I can't view ASX streams either.

I know they're Windows formats and all, but a lot of my stuff is in Windows Media formats...

I can play WMVs in Gxine, but the audio starts to lag behind the video and ends up like 3 seconds out of sync.

Did I forget a package or what?

---

### Post by slakkie on 2006-08-08
Try to install mplayer, and if you use firefox for browsing, install mozilla-mplayer as well.

```

sudo apt-get install mplayer
sudo apt-get install mozilla-mplayer

```

And by the codecs installed, I assume you mean the following pacakge: w32codecs
You can find this out by doing the following

```

dpkg --list | grep w32codecs

```

dpkg --list will show you all currently installed packages, see the man page for more info ('man dpkg').

I would also install the following package as well while we are at it: libdvdcss2. Its for DVD playback.

---

### Post by Sirron on 2006-08-08
Cheers, works pefect

---

### Post by JPMaximilian on 2006-09-07
I can playback video now using the above fix, but the audio doesn't work.  Any tips?

---

### Post by linuxpenguin on 2006-09-07
I'm getting "Cannot find codec matching selected -vo and video format 0x33564D57" even though I did install w32codecs.

---

### Post by fatsheep on 2006-09-07
I have all of the above installed but all I get is audio on .wmv videos in Mplayer Movie Player.  I get the same exact message as linuxpenguin did.

---

