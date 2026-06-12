---
title: "Movie Player Quit working????"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-03-10
For some reason, totem started playing videos sluggishly, if at all. Mplayer refuses to play anything. Most of these are mpeg or avi. where should I start?? totem was working fine before, and I havent touched my system at all.

---

### Post by taurus on 2007-03-10
What's the output when you run this from a terminal?

Applications -> Accessories -> Terminal
```
gmplayer movie.avi
```

---

### Post by HgBoy on 2007-03-10
error opening/initializing the selected video _out (-vo) device

---

### Post by taurus on 2007-03-10
Go into Preferences and change the video driver to "x11".  Close it and open it again and see if you can play your .avi now.

---

