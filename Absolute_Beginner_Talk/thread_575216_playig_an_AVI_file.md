---
title: "playig an AVI file"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by scripttron75 on 2007-10-13
i have a movie i want to play from my laptop, it is a avi file, i installed VLC and played it with that but there is no video only sound what can i do to fix this?:confused:

---

### Post by overlord.gaurav on 2007-10-13
Do this in a terminal:

```
sudo aptitude install totem-xine libdvdcss2 acidrip brasero  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse banshee libxine-extracodecs
```

..after this is done, play your movie, it should work fine!

---

### Post by rsambuca on 2007-10-13
> **overlord.gaurav said:**
> Do this in a terminal:

```
sudo aptitude install totem-xine libdvdcss2 acidrip brasero  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse banshee libxine-extracodecs
```

..after this is done, play your movie, it should work fine!

If you are suggesting that the OP install totem-xine and remove totem-gstreamer, then why add all the gstreamer plugins?  If the avi isn't working with vlc, it likely isn't a codec issue.

---

### Post by ajmorris on 2007-10-13
in order to play the avi in vlc or any other media player, you need w32codecs installed, search through synaptic to find the package of this or a similar name as i cant quite remember the exact name :P I think it is called w32codecs.

---

### Post by overlord.gaurav on 2007-10-13
> **ajmorris said:**
> in order to play the avi in vlc or any other media player, you need w32codecs installed, search through synaptic to find the package of this or a similar name as i cant quite remember the exact name :P I think it is called w32codecs.

I'm not very sure of that. Because, I am on 64 bit ubuntu and I installed the w32codecs recently after realising a necessity for real player codec. I never had a problem playing avi files in Totem and VLC.

---

### Post by rsambuca on 2007-10-13
> **ajmorris said:**
> in order to play the avi in vlc or any other media player, you need w32codecs installed, search through synaptic to find the package of this or a similar name as i cant quite remember the exact name :P I think it is called w32codecs.

Actually, for the most part vlc uses its own codecs, except for a couple of ffmpeg ones.  It certainly doesn't hurt to have the w32codecs, though.  To get the w32codecs, you need to add the medibuntu repositories.  [Instructions are here]("http://medibuntu.sos-sts.com/repository.php").

---

### Post by overlord.gaurav on 2007-10-13
I guess, the medibuntu method is for 64 bit ubuntu.
For 32 bit ubuntu, you can install w32codecs by following the [guide here]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?").

---

### Post by rsambuca on 2007-10-13
> **overlord.gaurav said:**
> I guess, the medibuntu method is for 64 bit ubuntu.
For 32 bit ubuntu, you can install w32codecs by following the [guide here]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?").

Both ways work.  The medibuntu method works for both, by the way.

---

### Post by mysurface on 2007-10-13
mplayer works better, you may wanna try to play movie in terminal

mplayer myvideo.avi

mplayer support many shortcut keys, check out [here]("http://linux.byexamples.com/archives/172/mplayercommon-keystroke-and-manipulation-of-subtitle/").

---

