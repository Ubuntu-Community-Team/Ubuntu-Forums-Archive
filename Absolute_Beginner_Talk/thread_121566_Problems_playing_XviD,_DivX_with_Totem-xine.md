---
title: "Problems playing XviD, DivX with Totem-xine"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by lapeste on 2006-01-25
I installed Breezy a couple of months ago and then installed totem-xine to play my video files... It has worked really fine all this time, but suddenly yesterday it stopped playing XviD and DivX files.  I don't understand why as they are the exact same files I have had in my HD for some time now, but now it gives the error 

"Video codec 'XviD' [or Divx 5] is not handled. You might need to install additional plugins to be able to play some types of movies"

I am new to linux and I don't know if this may be related to something else I might have changed in my system (can't think of anything, except the automatic upgrade things).

I know Mplayer will do it but I don't see why I can not get Totem to work properly again.

If anybody has any ideas for this, or at least a way to know what codecs are installed in my system... That would be helpful.

---

### Post by Zahrber on 2006-01-25
Install the codec pack from Automatix, to see if it can fix it. You may have broken something in an upgrade. I haven't played many movie files lately but have had lots of upgrades come down through synaptic.

---

### Post by lapeste on 2006-01-25
Thanks for the prompt answer.  I reinstalled the multimedia codecs with automatix but still totem-xine wont play DivX.  I then installed the media players with automatix also (totem-xine, vlc and beep) and vlc will play the files.  I guess that should have to do.  But still I don't understand what happened to totem-xine  - is there anyway to check the multimedia plugins, or what xine can play? I am new to all this but I would really like to understand how it works and what can I do with it.

---

### Post by Perfect Storm on 2006-01-25
You can try this and see if it helps:

```
sudo apt-get install gstreamer0.8-plugins gstreamer0.8-lame gstreamer0.8-ffmpeg gstreamer0.8-plugins-multiverse
gst-register-0.8

```

---

### Post by lapeste on 2006-01-25
Thank you AI, I tried but still got the same problem.  Should I try totem with gstreamer instead of xine?

---

### Post by Perfect Storm on 2006-01-25
Worth to try you can always change back. Although I don't use xine, totem or both. VLC do all the thing and play all the media files I have.

---

### Post by xequence on 2006-01-25
A second vote for VLC. It plays ALL videos on my computer =)

---

