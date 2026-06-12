---
title: "Totem won't play w32codecs"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by mysticmatrix on 2007-08-22
I have installed the w32codecs and now I am able to view my .rm and .wmv file, but **only in Mplayer(and its derivatives like Smplayer).**

Is there exist a way to play these files in Totem-gstreamer and VLC?

---

### Post by daradib on 2007-08-23
Totem does not offer to look for or install the appropriate codec when you open a WMV or RM?

---

### Post by mcduck on 2007-08-23
You need to have "gstreamer0.10-pitfdll" installed for apps using gstreamer to access w32codecs.

---

### Post by Hallvor on 2007-08-23
...and VLC uses its own codecs and should play everything except .rm out of the box.

---

### Post by mysticmatrix on 2007-08-24
> **mcduck said:**
> You need to have "gstreamer0.10-pitfdll" installed for apps using gstreamer to access w32codecs.

Pitfdll didnot help me with [this file]("http://www.movies.war-rvr.net/files/bright_wizard_teaser.wmv"). However, pitfdll was able to provide me sound in one other .wmv, on the positive note.

Also as I have read of pitfdll, it only provides support for .wmv and quicktime codecs. Is that true that I would never be able to use .rmvb file in gstreamer-totem?

---

### Post by mysticmatrix on 2007-08-27
Bump

---

### Post by mysticmatrix on 2007-09-28
Bump

---

### Post by angryfirelord on 2007-09-28
Just do what I did: Install every gstreamer 0.10 package available (except for debugging and doc ones).

---

### Post by mysticmatrix on 2007-10-08
Still the file in previous link doesn't works. :(

---

### Post by perce on 2007-10-08
I don't have win32codecs installed and I could listen to the file, but I had no video.

---

