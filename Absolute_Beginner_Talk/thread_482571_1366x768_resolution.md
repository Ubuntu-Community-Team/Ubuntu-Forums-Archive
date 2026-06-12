---
title: "1366x768 resolution"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Phixion on 2007-06-23
Hey there, I have installed Ubuntu Server on a spare PC, I currently have it hooked up to my 26" HDTV and am trying to get the resolution correct.

I have edited xorg.conf and added the resolution, restarted X... but no luck, the max I'm getting is 1280x1024.

Anyone got any ideas?

---

### Post by Happy_Man on 2007-06-23
Try the command ```
sudo dpkg-reconfigure xserver-xorg
```

Just keep hitting enter until you get to the section with a list of screen resolutions. Choose all that you want with spacebar, keep hitting enter until it finishes. Restart X and see if it works!

---

### Post by Phixion on 2007-06-24
Tried that, problem is my res wasn't in the list of resolutions available, so i tried adding it manually but couldn't get it to work.

It's ok though, I decided to ditch a GUI :)

---

### Post by Bluecircle on 2007-06-24
Yes, 1366x768 is not listed. When I configured xorg and chose to use the intel driver, i just selected 1024x768, 800x600 and 640x480. After I finished it automatically listed 1280x1024 and 1366x768 too.

---

