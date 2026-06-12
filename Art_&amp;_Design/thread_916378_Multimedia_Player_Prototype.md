---
title: "Multimedia Player Prototype"
date: 2008-09-10
forum: Art &amp; Design
---

### Post by addicted68098 on 2008-09-10
For the most part I have been experimenting with the GTK+ toolkit in C. I have decided to design a prototype media player after a few drafts this is what I came up with. It doesn't do much its just an early prototype of what the out of the box setup should look like.

My theory is that if I remove traditional elements and replace it with more redundant, versatile elements that the end software would be easier and more intuitive to use. The basic design uses 2 "buffers," which can be searched and browsed in multiple styles and the two can be used in sync to mange playlists, media devices, and the actual music library. There are still a lot of elements missing that should be there that I am still very divided on.



Please give me feedback about wether I should go on... thanks,

---

### Post by kostkon on 2008-09-10
It looks good. But what are the real advantages of this approach of having two "buffers".

And, the best option I believe is to use Gstreamer as your multimedia backend.

---

### Post by addicted68098 on 2008-09-10
> **kostkon said:**
> It looks good. But what are the real advantages of this approach of having two "buffers".

And, the best option I believe is to use Gstreamer as your multimedia backend.

Mostly it (should) make it manage things and allow users to mix playback with browsing when compared to the tradition playlist model.

---

