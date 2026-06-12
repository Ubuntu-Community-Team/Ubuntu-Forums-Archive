---
title: "Rythmbox Problem"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-06-08
Hi,

I've installed all the codecs that let me play aac and I can play the files but I can't play them in rythmbox, it just doesn't recognise them at all.

Any help please?

---

### Post by timetunnel on 2006-06-08
I had the problem as well and if I remeber right I solved it by just installing all the different gstreamer-plugin* packages: 

gestreamer0.10-plugins-good
gestreamer0.10-plugins-bad
gestreamer0.10-plugins-bad-multiverse
gestreamer0.10-plugins-ugly
gestreamer0.10-plugins-ugly-multiverse

One of these packages solved the problem and Rhythmbox started playing AAC files. But I have no idea which one. And I have the w32codecs and gstreamer0.10-ffmpeg installed, of couse.

---

### Post by timetunnel on 2006-06-08
I'm using Dapper, so the list of packages will be different if you're still using Breezy.

---

### Post by Dr Von Bon Bon on 2006-06-08
Thanks.

I am using Dapper now. I need to change the thing on my name :-\" 

Anyway, I couldn't find the files in the terminal but I managed to find them in Synaptic and it appears to be working.

Many thanks.

---

### Post by mattalves on 2006-12-12
I have all the packages installed and still my Rhythmbox doesn't play the aacplus stream from Radio Paradise. Any idea what might be happening, anyone?

Cheers

---

