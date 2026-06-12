---
title: "[SOLVED] Plugin for wmv and mpg files"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Dumpy Dumpster on 2007-12-28
From The Ubuntu Guide, I installed 'libdvdread3', 'totem-xine' and 'libdvdcss2' in order to play DVDs.   During the installation, I noticed that a gsteamer (no further details) file was being removed.   Totem now says that I need to install plugins to play wmv and mpg files.  What do I need to install, or re-install, that will not clash with the DVD playback installation files?

---

### Post by Hallvor on 2007-12-28
Try installing codecs again:

```
sudo apt-get install w32codecs
```

and 

```
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

For DVD playback: 

```
sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
```

If nothing works,I recommend installing VLC media player. It will play anything with its own codecs.

```
sudo apt-get install vlc
```

---

### Post by Dumpy Dumpster on 2007-12-28
Many thanks,Hallvor.  Your last suggestion worked fine and duly installed. If I can ask two other quickies as you know your way around:
1.  I notice some threads have 'SOLVED' added to the thread name.  How do I do that?
2.  How can I get quickly back to my posted threads without re-entering the question and using the search facility?
Once again thanks and all the best.

---

### Post by xzin on 2007-12-28
> **Dumpy Dumpster said:**
> Many thanks,Hallvor.  Your last suggestion worked fine and duly installed. If I can ask two other quickies as you know your way around:
1.  I notice some threads have 'SOLVED' added to the thread name.  How do I do that?
2.  How can I get quickly back to my posted threads without re-entering the question and using the search facility?
Once again thanks and all the best.

1.  Go to the top of the thread, click Thread Tools, there "Mark this thread as solved"
2. Click on search and choose "Find All Your Threads"

I hope this helped :)

---

### Post by Dumpy Dumpster on 2007-12-29
Many thanks once again!

---

