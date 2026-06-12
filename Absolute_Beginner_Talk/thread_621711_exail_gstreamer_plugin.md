---
title: "exail gstreamer plugin?"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-11-24
everytime i try to play a song in exaile it says that You do not have the appropriate Gstreamer plugin installed to play this file

---

### Post by Partyboi2 on 2007-11-24
Have you installed the plugin's?
Open up add/remove and do a search for gstreamer plugins

---

### Post by fedex1993 on 2007-11-24
it came up with mplayer and piding in ad ad remove also i dont know what plugins i need to install

---

### Post by fedex1993 on 2007-11-24
okay i found at that was just an error that i fix but know i found that it is say ```
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3

```

---

### Post by ryanVickers on 2007-11-24
are you absolutely sure you've installed all the plugins?  I would get **all** the gstreamer (just type it in the search box at the top), the "(k)ubuntu extras", and if possible and/or necessary, xine :p

---

### Post by Partyboi2 on 2007-11-24
To install the ugly plugin that you need:
```
sudo apt-get install gstreamer0.10-plugins-ugly
```

---

### Post by fedex1993 on 2007-11-24
ty sudo apt-get install gstreamer0.10-plugins-ugly worked perfectaly

---

### Post by Partyboi2 on 2007-11-24
Happy to help:)

---

