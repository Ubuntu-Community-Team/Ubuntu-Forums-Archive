---
title: "java, seamonkey and runescape"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by jimclarke on 2008-04-18
I'm trying to play Runescape on my Linux box using SeaMonkey. It doesn't seem to load the java plugin. I've tried reloading the java jre and the java plugin to no avail. Runescape runs fine with firefox. Can I fix this or is it a mystery. Runescape runs fine using SeaMonkey on my XP machine, so is just my Linux machines (Gusy and Hardy) that have issues.

---

### Post by kerry_s on 2008-04-18
make sure you have> edit> preference> advanced, java checked.
click help> about plugins and see if java is there.

---

### Post by jimclarke on 2008-04-18
edit> preference> advanced, java is checked.

help> about plugins>java is** not** there. that guides me to download jre-6-linux-i586.bin. I downloaded to my desktop but not sure how to proceed. lol, my ignorance of linux is shining here.:confused: I did try uninstalling and reinstalling jre plugin through synaptic package manger, but that didn't help.

---

### Post by kerry_s on 2008-04-18
look in synaptic if you have sun-java6-jre and sun-java6-plugin, then check where they were installed, sometimes the links are not in the right place.

---

### Post by jimclarke on 2008-04-18
Have to do this on hardy computer, I seem to have broken Gutsy :eek: . Both sun-java6-jre and sun-java6-plugin are installed plugin went
/home/jim/Desktop/Screenshot-sun-java6-jre Properties.png
/home/jim/Desktop/Screenshot1.png

Hope the screen shots are ok

---

### Post by Sinkingships7 on 2008-04-18
run this in the terminal and restart firefox:
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by jimclarke on 2008-04-18
ran that, the response was /home/jim/Desktop/Screenshot-jim@lout: ~.png.. Firefox still runs ok but SeaMonkey still shows no java plugin

---

