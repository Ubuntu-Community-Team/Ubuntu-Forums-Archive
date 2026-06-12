---
title: "no sound at all"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by simplekin on 2007-05-07
Ok, i have just installed Ubuntu, and have no sound at all. I believe this is because of my video card, but who knows. I was wondering if somone can help me with this. First i need to find out my sound card and the only way I can do that is to go and take it out and look at it, is there a program that tells you what hardware you have?

---

### Post by vigleik on 2007-05-07
To find out what kind of hardware you have, use "lspci -v" (v for verbose, or more detail) or, for a slightly different list, "lshw". (You might have to install lshw first, "sudo apt-get install lshw".)

---

### Post by kensou on 2007-05-08
write  "alsamixer" and check for sound

---

### Post by simplekin on 2007-05-08
> **kensou said:**
> write  "alsamixer" and check for sound ok i did, i dont know what to do with it, and is it supposed to start making sounds right away?

---

### Post by chemtut on 2007-05-08
right click sound icon
click volume control and unmute everything 
This happened to me and I sorted it out this way

good luck

---

