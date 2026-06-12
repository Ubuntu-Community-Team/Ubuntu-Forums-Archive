---
title: "liblame0"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-10-07
Synaptic swears that I already have liblame0 installed, and that I (or rather *Audacity*) should be able to find the mp3 export library /usr/lib/libmp3lame.so.0.0.0, and exactly there, in fact. Well, it ain't there. I considered removing and reinstalling it, but it appears that I would have to remove a rather long list of related apps along with it. What's going on? What should I do? I downloaded the liblame0 archive to my usual downloads folder and tried to extract it and then move it to the required folder. Is this the problem? Somehow, though, I doubt that I can download to a folder that doesn't allow me to paste to it. I'll give this a try while waiting for replies. TIA.

---

### Post by xander848 on 2006-10-07
Dont know if this is what your asking for but when I tried to save as a mp3 in audacity it needed that file but it was named differently so I had to symlink to it. Look in /us/lib/ for files that have almost the same name and symlink to whatever you need.

---

### Post by ricardisimo on 2006-10-07
> **xander848 said:**
> Dont know if this is what your asking for but when I tried to save as a mp3 in audacity it needed that file but it was named differently so I had to symlink to it. Look in /us/lib/ for files that have almost the same name and symlink to whatever you need.

Nope. Nothing even close. Also, of course, I can't download the archive into /usr/lib, at least not GUI. How do I get access to that folder to download into it? Should I be doing this? Shouldn't I do exactly as I did already: download to desktop or some useful folder, then extract from there? Thanks.

---

### Post by ricardisimo on 2006-10-07
And one more thing: When I extract-in-place the download from sourceforge (lame-3.97.tar.gz) and look at the results, there is no .so file anywhere that I can see. I'm quite certain that I didn't select the Windows/Mac/etc version, so this just seems to be getting more and more complicated.

---

