---
title: "Video Available through websites"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Gester on 2007-09-01
I can't seem to get any sort of video to play when I'm on a website.  For instance, game highlights on NFL.com.  If someone could tell me in complete idiot's language what I need to do it'd really be helpful.  (Meaning, I don't what people mean when they say to mount a drive or anything, I've spent a lot of time in windows and some time in dos but very little time in anything else.)  Please educate me.

---

### Post by Seisen on 2007-09-01
Do you have flash installed? If not search for flashplugin-nonfree in Synaptic. Also you need to have the multiverse repository enabled too.

---

### Post by Majorix on 2007-09-01
I checked the site you mentioned, and it seems they are using Flash. You have to get the flash player using
```
sudo aptitude install flashplugin-nonfree
```

If it says anything about the package not being available, go to System > Admin > Software Sources and check everything there (making sure multiverse is in there too) and it should work.

---

### Post by pjones0404 on 2007-12-07
i am also trying to view the videos on nfl.com and i am unable to. i installed the non-free plugins and it still does not work.

can anyone tell me what i need to install to watch these videos?

---

### Post by jordanmthomas on 2007-12-07
You may want the mplayer-plugin for firefox.
It's in the repositories, but I don't know the name of the package exactly.  It is aptly named and shouldn't be tough to find thouh.

---

