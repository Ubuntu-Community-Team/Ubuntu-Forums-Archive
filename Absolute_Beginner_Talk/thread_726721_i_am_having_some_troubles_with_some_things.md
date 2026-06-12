---
title: "i am having some troubles with some things"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by pankirk on 2008-03-17
Ok so my wireless pci adaptor (wmp54g linksys) works great. But every once and a while it will just disconnect from the internet and stop working, I know its not my router because when i shut my pc off and turn it back on the internet works again.So it must have something to do with ubuntu/the drivers I have for my card. Also I have this mic, it came with my motherboard and its called "soundMAX SUPERBEAM" is there a way that I can get this mic setup to work with ubuntu? When I hax windows, it needed some sort of control panel (i think) to work. SO yeah... How can I fix my internets and how can I get my mic working again. Thanks in advance this forum really helps me out a lot!

EDIT: and one last problem i'm having (sorry...) I have AWN dock and I have a launcher on it and the launcher is photoshop cs2.... which means It uses wine to run. And im just wondering how I can change it from the default blue triangle to the actual photoshop icon. i tried to right click it but theres no Icon thing to click.

---

### Post by daengbo on 2008-03-17
Your driver may be buggy and causing you to lose the connection. If that happens again, you probably don't need to reboot, just to re-establish the connection using the applet in System -> Administration -> Network. Untick the wireless card's box, wait about ten seconds, then turn it back on. That should work for you.

How does the mic connect to the motherboard? Try going to the volume control applet near the clock, right-clicking, and choosing "Open Volume Control." You can set the mic volume from there. In the preferences, you may also find another mic listed in there that isn't in the main voume control panel by default. Best of luck.

---

### Post by pankirk on 2008-03-17
The mich just connects to the green (or whatever the color is for mic) hole in the back? Thats all it had to be plugged into for windwos to work.

---

### Post by daengbo on 2008-03-17
If that's the case, then it should be working. The mic jack is on the same USB audio device, right? Run "alsamixer" in a terminal and see if the mic is muted or turned all the way down.

---

