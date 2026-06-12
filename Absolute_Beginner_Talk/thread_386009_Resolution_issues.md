---
title: "Resolution issues"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Lupurus on 2007-03-16
Hello! This is the first time I've installed Ubuntu (or any Linux distro for that matter) and so far I have one problem. My resolution is currently at 800X600, and the only options available to me in the screen resolution preferences window are that and 640X480. I usually run my display at 1280×1024. My video card is an ATI all-in-wonder XT. (regrettably, I don't know the number associated with my video card's name, and, having no idea how to use Ubuntu, am not sure how to find out).
Any help would be appreciated,
Lupurus

---

### Post by Kobalt on 2007-03-16
Hello,

Open up a Terminal and enter the following command line :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as avaliable with the spacebar then press Enter. Finally, press Ctrl+Alt+Backspace to restart X and ... voilà ! :)

---

### Post by Lupurus on 2007-03-16
Worked like a charm, thanks!

---

