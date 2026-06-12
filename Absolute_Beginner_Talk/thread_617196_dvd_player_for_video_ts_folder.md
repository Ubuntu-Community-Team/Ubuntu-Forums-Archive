---
title: "dvd player for video_ts folder?"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by 244f on 2007-11-19
hello :)
i'm trying to figure out what dvd/movie program to play video_ts folders with, i  searched and have no luck.

on windows i used interactual dvd player and it would have an option where you click source and play dvd from folder. can i do that on ubuntu?

---

### Post by stomponthis on 2007-11-19
You can use VLC to play dvd folder (video-ts folders)

```
sudo apt-get install vlc
```

or add/remove software menu

Its the best media player, simple, fast and plays almost anything!

---

### Post by hyper_ch on 2007-11-19
+1 for vlc

---

### Post by biodynamic on 2008-02-05
You can use xine if you edit your ~/.xine/config file so that "media.dvd.device" points to your dvd image folder. Then you can play your video_ts folder by opening your dvd device from xine. If you're using a separate gui you might have to edit its corresponding config file instead. :popcorn:

---

### Post by stchman on 2008-02-05
> **244f said:**
> hello :)
i'm trying to figure out what dvd/movie program to play video_ts folders with, i  searched and have no luck.

on windows i used interactual dvd player and it would have an option where you click source and play dvd from folder. can i do that on ubuntu?

You need to create a video DVD and burn that video_ts folder on there.  You can then use VLC to play the DVD.

---

### Post by leftorvo on 2008-02-05
vlc can do it, so can mplayer:

```

mplayer dvd:// -dvd-device "/media/cdrom0/"

```

and xine:

```

xine 'dvd://media/cdrom0/'

```

---

### Post by Lord Illidan on 2008-02-05
Totem-xine can also do it very easily. Just drag the video_ts folder and drop it onto a player window.

---

### Post by asmoore82 on 2008-02-05
+1 for VLC, it's easier

but Xine has better support for 5.1 Digital Audio.

---

