---
title: "Resolution and sound problem ."
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by nooblet on 2007-06-21
Hey guys I cannot get my resolution to be more than 1024x768 can any help ? I am using 8800GTS . 

 The other thing is about my sound problem I am using Intel 946GZIS mother board with sigmatel audio card onboard ... though on the desktop I can change the sound volume and its not showing that red cross which is there when sound is not available I can't hear songs etc .. please help ..

---

### Post by Kobalt on 2007-06-21
For your resolution thing : first, did you install the drivers for your nvidia card ? Second, you can try this : open up a Terminal and enter the following command line ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Select the driver for your card (leave default if you don't know) and then, in the resolution list, select the ones you want as available by hiting the spacebar. Validate with Enter. Restart X with Ctrl+Alt+Backspace so that the changes take effect, and now you should have a proper resolution.

About your sound problem, you might want to [check this first]("https://help.ubuntu.com/community/DebuggingSoundProblems").

---

### Post by nooblet on 2007-06-21
Well Ok the resolution problem is solved but the link you gave me for the sound problem is not helping :( ...

---

### Post by Kobalt on 2007-06-21
When you open the volume control, do you see the PCM level ? Is it muted, low or high ?

---

### Post by nooblet on 2007-06-21
Whats PCM :P ?

---

