---
title: "how do you play mov files with vlc or totem?"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-12-01
I installed the w32codecs but my mov files still do not play well.  the video is blurry and distorted.  What should I do?

---

### Post by pappo on 2005-12-01
I also had trouble with Totem, so I just did the following:

sudo apt-get install xine

Xine has been able to display every movie type file I have thrown at it, including the Microsoft types.
Give it a try, I think it is a more tha suitable replacement for Totem.

---

### Post by tseliot on 2005-12-01
Or
```
sudo apt-get install totem-xine
```

If it asks you to remove gstreamer, say yes

Then Totem will use the xine engine

---

### Post by Danielle on 2005-12-01
hi, i just tried the xine engine with Totem. when i played the video it says it closed unexpectedly but carries on playing the sound. when i play the large-h264.mov with VLC there's video but no sound :( how can i watch my video? i was going to play them at the same time, but i'm doing a virus scan atm and it all takes up too much CPU :( can you help me? i'd like to use VLC if possible. thanks

---

### Post by MegaBill on 2006-05-02
I've done everything this thread has said to do, but I still get error messages like "Video codec 'Advanced Video Coding (H264)' is not handled. You might need to install additional plugins to be able to play some types of movies" when trying to play .mov files.  What's the deal guys?

---

### Post by SeanTater on 2006-05-03
The same happens here - Kubuntu Dapper beta 6

---

### Post by MarcG on 2006-07-22
> **MegaBill said:**
> I've done everything this thread has said to do, but I still get error messages like "Video codec 'Advanced Video Coding (H264)' is not handled. You might need to install additional plugins to be able to play some types of movies" when trying to play .mov files.  What's the deal guys?

Just bumping this thread. I'm having the same problem.

--Marc

---

### Post by hotani on 2006-09-08
After attempting to play some movie trailers from Apple, h264/.mov, the entire Ubuntu desktop slowly came to a screaching halt. First sound died. No applications had sound. After attempting to log out, the desktop froze and nothing was responsive. ctrl+alt+backspace restarted the dektop manager, but still no sound. A full reboot was necessary to restore order.

Is it safe to assume H264 is not supported at this point?

---

### Post by MiniJames on 2006-09-14
bump.

---

