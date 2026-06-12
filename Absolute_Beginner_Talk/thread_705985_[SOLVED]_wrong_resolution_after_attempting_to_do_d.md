---
title: "[SOLVED] wrong resolution after attempting to do dual screen in gutsy"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by CostaRica on 2008-02-24
Hi.

I have a Sony VGN-TXT25N which was running perfectly until I decided to try the dual screen (Gutsy new feature).  

I could not, but when I came back to a single screen, the resolution is 640X480 and there is no way to put it back to 1366X768.

I tried the sudo dpkg-reconfigure xserver-xorg
 but when it comes to monitor (it suggests generic monitor) I do not know what to write, and if I leave the default I get the same 680x480 resolution.

I really appreciate your suggestions!

---

### Post by Rocket2DMn on 2008-02-24
You can choose whatever names you want, it doesn't really matter.  The most important part is selecting your video driver and resolutions.  At the resolution page use TAB to move and SPACEBAR to select your monitor's max resolution and everything less.
You can try having it autoconfigure as well:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by CostaRica on 2008-02-24
I did what you told me, but did not get the option of a 1366X768 resolution in xorg

---

### Post by CostaRica on 2008-02-24
Sorry, It DID work.  Thanks a lot!!!

---

