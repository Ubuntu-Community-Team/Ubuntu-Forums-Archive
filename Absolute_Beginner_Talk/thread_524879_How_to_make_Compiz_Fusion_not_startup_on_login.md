---
title: "How to make Compiz Fusion not startup on login??"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Cannon9559 on 2007-08-13
Ok, i know this sounds wierd at first.....but i don't want compiz fusion to start up at login. I installed the systray icon for it and it works perfect, it even recognizes emerald. The problem is that i want the systray icon to start up at login, but if i do that then it tries to start compiz again, which is already running and then the system freezes. Right now i have to do everything manually, i have to stop compiz, startup the systray icon, and then it starts compiz again(which i want). Also i can't find out how to have the default theme manager as emerald for the systray icon. If anyone has suggestions, or has any links to other sites about this then that would be most helpful......thnx.

---

### Post by Hobo Joe on 2007-08-13
Check the sessions, under System>Preferences, make sure compiz fusion isn't there.

---

### Post by BitTorrentBuddha on 2007-08-13
I've not seen the systray for compiz fusion, if you don't mind me momentarily hijacking your thread, could you point me to the systray applet? From there perhaps I can have a look at it and try and help you out in return.

---

### Post by Paul133 on 2007-08-13
I have fusion-icon set to start up at login and I've had no problems. Bit, here's the video tutorial I followedhow to set up the fusion icon: [http://www.youtube.com/watch?v=4uNQcD82mhk](http://www.youtube.com/watch?v=4uNQcD82mhk)

And here's how to do it: 
```
 sudo apt-get instal git-core
git clone git:/anongit.opencompositing.org/users/crdlb/fusion-icon
cd fusion-icon
sudo make install
```

Obviously, put those in one line at a time. You can launch the icon through Applications -> System Tools -> Compiz Fusion Icon

---

### Post by Cannon9559 on 2007-08-13
Sry I don't remember where i found the how to for the Fusion-icon, but it was something similar to what paul did there. I did already check the sessions, and compiz fusion isn't there, so i don't really know how, or where it starts up. Lol, it's a big mystery.

---

### Post by Cannon9559 on 2007-08-13
Hey, i found the how to for installing Fusion-icon in ubuntu(it's actually on these forums):
[http://ubuntuforums.org/showthread.php?t=497186]("http://ubuntuforums.org/showthread.php?t=497186")

---

