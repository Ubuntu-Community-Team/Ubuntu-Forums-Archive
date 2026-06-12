---
title: "Volume Controls only affect front speakers"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by tprzepiorka on 2008-02-10
Hello,
The default volume controls (Master) only affects the volume of the front speakers. My rear speakers to do not mute if I choose to mute from the drop down audio control. Any ideas? (I am using Alsa)

---

### Post by randy78 on 2008-02-10
In a terminal, type:
alsamixer

If it's not installed:
sudo apt-get install alsamixer

Hope that helps ;)

---

### Post by tprzepiorka on 2008-02-11
Ok, So I got into the alsamixer. I found that I could adjust all the speakers at the same time by using the "PCM" control. The only thing is that I usually use my keyboard's volume control keys to adjust the volume. These keys affect the "Master" volume. Is there anyway to change it so that these keys affect the "PCM" rather than the "Master" volume?
Thanks for the reply :)

---

### Post by randy78 on 2008-02-11
> **tprzepiorka said:**
> Ok, So I got into the alsamixer. I found that I could adjust all the speakers at the same time by using the "PCM" control. The only thing is that I usually use my keyboard's volume control keys to adjust the volume. These keys affect the "Master" volume. Is there anyway to change it so that these keys affect the "PCM" rather than the "Master" volume?
Thanks for the reply :)

If you have a volume icon on your panel, right click it and go to Preferences, then select PCM

If you do not have a volume icon on your panel, right click on an empty space on the panel, select Add To Panel, when the dialog box opens, scroll down and click once on the volume control, then click add and then follow the instructions above ;)

After you select PCM, right click on the volume control again, select Open Volume Control and from there you can adjust levels, unmute speakers and whatnot.

Take Care :popcorn:

EDIT: Nevermind, I thought you were asking how to access the PCM control panel... I'm not sure how to bind the keyboard to affect only the PCM... I'll see what I can find ;)

---

