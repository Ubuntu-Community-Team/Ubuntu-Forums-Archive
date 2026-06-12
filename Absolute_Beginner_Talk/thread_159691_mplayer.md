---
title: "mplayer?"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2006-04-13
I am using Ubuntu 5.10. I would like to play movies with mplayer. But I don't have it installed. Where can I find it?

---

### Post by Ubuntuud on 2006-04-13
sudo apt-get install mplayer

---

### Post by nalmeth on 2006-04-13
You can search synaptic for it, or if you would like to use the terminal, type this to find mplayer related packages:
apt-cache search mplayer
If you have the regular i386 kernel, then I believe the mplayer package is called mplayer-386
sudo apt-get install mplayer-386
xine is very good too, you might want to look at that, if you like mplayers interface.

---

### Post by mandrakethepenguin on 2006-04-13
You should use [Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405")
Its a script that will install encoders and media players, including mplayer, to your machine.

---

