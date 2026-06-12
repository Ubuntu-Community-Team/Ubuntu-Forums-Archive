---
title: "not liking mplayer..."
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Hranj on 2006-08-20
i installed mplayer for mozilla a little while ago and wmv movies are not showing up. its just audio and controls. how would i fix this? remove the extension or replace with something else? thanks.

---

### Post by Fass on 2006-08-20
Just a shot, but try editing your ~/.mplayer/config file and put something like ```
vo=xv,x11
``` in it. Does that help?

---

### Post by scxtt on 2006-08-20
do you have the correct codecs installed for wmv playback? -- are you sure you're not trying to view wmv10 files?

---

### Post by Hranj on 2006-08-20
ive been trying alot of other videos and some of them work and some of them dont. ex. this website channelchooser.com has internet tv and such but its not showing up its just the audio. the same goes for putfile. but if i run it in VLC MP it works fine. but its not in the browser. so i think without Mplayer it would work fine. so my ? is how would i remove it. thanks.

---

### Post by scxtt on 2006-08-20
how did you install mplayer (if it wasn't installed by default)? -- a simple **aptitude remove mplayer** should work ... if you're talking only about an mplayer-mozilla plugin, you should be able to do something similar (but i don't know the exact name of 'mplayer-mozilla' plugin ... you should be able to find it in a GUI package manager or a **aptitude search ...** for it.

---

