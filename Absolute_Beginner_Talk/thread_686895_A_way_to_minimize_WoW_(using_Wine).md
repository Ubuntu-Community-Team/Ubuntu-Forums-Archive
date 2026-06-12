---
title: "A way to minimize WoW (using Wine)?"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by papuccino1 on 2008-02-03
I can't minimize it nor can I alt+tab. Any help?

---

### Post by diaa on 2008-02-03
try this thread [Starting a second X server]("http://ubuntuforums.org/showthread.php?t=510182")
and this howto [Extra XServer]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+extra+XServer")

---

### Post by papuccino1 on 2008-02-03
What the beep!?

Hahaha sorry I'm so confused right now. I don't want to start a server or anything like that. All I want to do is minize the window. That's it. Does it have to so complicated?

---

### Post by Kilz on 2008-02-03
> **papuccino1 said:**
> What the beep!?

Hahaha sorry I'm so confused right now. I don't want to start a server or anything like that. All I want to do is minize the window. That's it. Does it have to so complicated?

You could tell wine to simulate a desktop. Type winecfg in a terminal. The wine config will open. On the Graphics tab check the Emulate a virtual desktop box. Adjust the size of the desktop, at least 800x600 and click ok. Then when Wow starts it will be in a window. If it cant be shrunk, at least you can open another application over it.

---

### Post by papuccino1 on 2008-02-03
I'd rather not mess up my configuration. So there's absolutely NO way for me to just minimize it? :S

---

### Post by Majorix on 2008-02-03
You can create a new application entry so you don't mess up with the default entry. There you should edit it to "Allow the window manager to control the windows" or whatever that was. You won't need a virtual desktop as suggested above, I believe. Though I may be wrong, I don't use WINE any often :)

---

### Post by papuccino1 on 2008-02-03
Oh my god. 

Note to Wine devolopers. Make a frikin' minize key! I can't make any sense of all the help you guys gave me. :(

---

