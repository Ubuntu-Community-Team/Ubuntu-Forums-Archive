---
title: "please help with accessing files?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by darkwarrior0404 on 2006-07-11
I have a second hard drive which is NTFS, I have some movies located on that drive, is there any way I can access them? I can access through the terminal, but not sure how to go about clicking it's "link" on my desktop because it says I do not have priveldges to, and once I do, how do I play the .wmv files? Please help!

root@ubuntu:/media/sdb1/movies       <---thats where they are located](*,)

---

### Post by Emceay on 2006-07-11
have you tried nautilus?
alt+f2 gksudo nautilus

That's what i've learned to do when it talks permission smack.

---

### Post by darkwarrior0404 on 2006-07-11
well that worked, how do I play .avi, .mov, and .wmv as well as .mpeg? Thank's a lot, the gksudo nautilus worked

---

### Post by Jasper Houtman on 2006-07-11
WMV is a restricted format, you need w32codecs in order to be able to play them (mplayer & Xine).

You can use Synaptic to get the codecs if you already updated your sources list. If not then do a search for restricted formats, there's a Howto on this forum.

---

