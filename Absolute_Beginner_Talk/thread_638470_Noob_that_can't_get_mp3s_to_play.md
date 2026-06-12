---
title: "Noob that can't get mp3s to play"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by amyfamb7 on 2007-12-12
I have been using gutsy for about a week now, but am frustrated because I can't get my mp3s to play. First I installed the gstreamer packages and when I tried to play a song in totem or rhythmbox it played the first few notes and totally crashed my system.  I have downloaded ubuntu restricted extras after reading a post in the forums only for the same thing to happen. What am I doing wrong? Are there codecs that I'm missing? Will someone please walk me through what I need. Thanks :)

---

### Post by corowakid on 2007-12-12
I use Amarok, and it does all you want with MP3 files.

I downloaded the program thru Synaptic, and all dependencies were downloaded as well. It appears as a menu item, and can compile playlists, can get cover art etc. I tried a few others, but this is by far the most comprehensive and easy to use program. I access my music from a FAT32 external drive with no problems. HTH

---

### Post by kpkeerthi on 2007-12-12
> 
totally crashed my system


Hmm.. that is weird. Run totem from command line and post the log when it crashes. As ubuntu is totally crashing, I advice you to redirect the output and error messages to a file  error.log so you can look at the file after reboot.

```

totem /pat/to/file.mp3 2>&1 error.log

```

---

### Post by meborc on 2007-12-12
... disregard... wrong post :(

---

### Post by hyper_ch on 2007-12-12
You can add the medibuntu repos and install the w32codecs there (not sure if it's them that enables MP3 support). Additionally I do install those stuff here:

```

aptitude install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer ubuntu-restricted-extras libk3b2-mp3

```

You don't need all of that but with it, mp3 should work.

---

