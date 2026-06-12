---
title: "[SOLVED] How do I get VLC a default player"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Dumpy Dumpster on 2008-01-06
I still have a problem to make VLC my default player.  I have already changed Removable Drives and Preferences > Multimedia setting to read 'vlc %m' and I know that one should right click on the movie > properties > Open with.. But no VLC option available.  Also I have tried to 'add it', but again VLC does not appear as an option in the list.  The programme is installed and works as I can 'drag and drop' into it.  Surely there must be a SIMPLE way of making an approved Ubuntu player default?

---

### Post by philinux on 2008-01-06
Is vlc actually installed. Please ignore if it is. It's not installed by default. Either use add/remove or synaptic.

In removable drives etc. the command I have is. ```
vlc dvd://
```

---

### Post by wheredidrealitygo on 2008-01-06
default player or what? video files (.avi, .mpg, etc), sound files (.mp3, .wma, etc), dvds, network streams?

You kinda have to be more specific. If you're looking to make it default for video files, right click the video file in question, go to properties, then the "open with" tab, point it to vlc.

You can do that with any particular filetype to make it played in VLC by default.

---

### Post by meho_r on 2008-01-06
> **Dumpy Dumpster said:**
> I still have a problem to make VLC my default player.  I have already changed Removable Drives and Preferences > Multimedia setting to read 'vlc %m' and I know that one should right click on the movie > properties > Open with.. But no VLC option available.  Also I have tried to 'add it', but again VLC does not appear as an option in the list.  The programme is installed and works as I can 'drag and drop' into it.  Surely there must be a SIMPLE way of making an approved Ubuntu player default?

If VLC is installed and doesn't appear in the list, you could try: Properties > Open With > Add... > Use a custom command and type in vlc (or full path to vlc)

---

### Post by Dumpy Dumpster on 2008-01-07
Thank you meho_r.  Typing in the command did the job.

---

### Post by meho_r on 2008-01-08
You're welcome. Glad to hear that it helped :D

---

