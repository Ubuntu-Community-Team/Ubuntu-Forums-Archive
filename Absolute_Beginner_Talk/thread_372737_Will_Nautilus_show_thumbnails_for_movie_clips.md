---
title: "Will Nautilus show thumbnails for movie clips?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-02-28
I have recently migrated movie clips from backup discs (from former XP OS). Does Nautilus have an option that will show a thumbnail view instead of the roll-of-film icon for movie clips? It is hard to remember what some of them are by the names.

---

### Post by invalid on 2007-02-28
Yes, it will show you a preview slide of the video.

---

### Post by invalid on 2007-02-28
Sorry, I forgot to mention how :)

I don't know of a convenient way, but it can be done with gconf-editor.
Traverse to desktop > gnome > thumbnailers and enable the option here.

---

### Post by MetalMusicAddict on 2007-02-28
> **67GTA said:**
> It is hard to remember what some of them are by the names.

LOL! Yeah, porn is like that. ;)

In Nautilus, Edit->Preferences. Then pick the "Preview" tab. All your options are there.

Video thumbnails are also generated differently depending which backend you use with Totem.

ie: totem-gstreamer or totem-xine. With totem-xine you'll need the w32codecs and with totem-gstreamer you'll need to make sure you have the proper gstreamer packages installed.

---

