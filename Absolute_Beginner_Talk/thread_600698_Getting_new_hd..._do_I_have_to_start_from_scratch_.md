---
title: "Getting new hd... do I have to start from scratch?/ other noob questions"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-02
I'm running Gutsy Gibbon on a 4GB harddrive right now and sooner or later will be upgrading to a larger one. Is it possible to just copy over to a new harddrive or am I going to have to reinstall and start from scratch?

also completely off topic, 

I have Ktorrent installed and was wondering how to make it my default .torrent program for Firefox, right now I have to manually drag the torrent files into the program to download. Also how do I check to see if the ipfilter.dat loaded correctly? I remember in Utorrent there was a logger tab that showed this. 

and one more, 

how do I view system specs ex. video card. Thanks for your help!

---

### Post by Dr Small on 2007-11-02
For the system specs:
```
sudo apt-get install sysinfo
```

---

### Post by SOULRiDER on 2007-11-02
To make kTorrent open .torrent files from Firefox go to (in firefox)

edit > preferences > content > manage (near the bottom)

---

### Post by 449 on 2007-11-02
> **SOULRiDER said:**
> To make kTorrent open .torrent files from Firefox go to (in firefox)

edit > preferences > content > manage (near the bottom)

Hm, ok I'm there but all there is, is default video files.

---

### Post by shearn89 on 2007-11-02
normally you get a "what should i do with this" type box, and if you check "open with application", it should do what you want. Check the default download settings for the filetype (should be near where you just were).

---

### Post by 449 on 2007-11-02
Wow, I feel stupid I still don't see it. Maybe I just don't have it. Here's a screenshot.

---

### Post by philinux on 2007-11-02
If you have a torrent  file on your desktop right click selct properties and change the app it opens with. All torrents will now open with that app.

---

### Post by shearn89 on 2007-11-02
That looks right. Just make sure that in that box at the bottom, nothing is set for torrent files. (Or that its set to open with ktorrent).

---

### Post by 449 on 2007-11-02
> **philinux said:**
> If you have a torrent  file on your desktop right click selct properties and change the app it opens with. All torrents will now open with that app.

That fixed it. Thanks for all your guys help this far!

---

### Post by 449 on 2007-11-02
I have **one** more question to add. Is there any video converter software available? Say to convert .avi to .wmv? Thanks Again!

---

### Post by shearn89 on 2007-11-02
yes, but i can't remember off the top of my head. Try searching. There's probably at least a shell script for it.

---

### Post by 449 on 2007-11-04
If anyone can answer my harddrive question that be great.

---

### Post by shearn89 on 2007-11-04
Oh sorry. You could install the disc as a second drive, but then you'd have to reinstall GRUB once you removed the smaller disc. Easiest probably to backup your entire /home directory, then make a list of all essential software, and reinstall. Won't take you long to get back where you were, as long as you have your home directory.

---

