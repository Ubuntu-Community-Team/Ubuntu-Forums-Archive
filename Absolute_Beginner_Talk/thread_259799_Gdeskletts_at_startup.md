---
title: "Gdeskletts at startup"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-17
Hi, I was wondering how I get my gdesklets to load at startup.  I currently have them running, so I looked at the system monitor to get the name of the process that was currently running, it was listed as :

python /usr/lib/gdesklets/gdesklets-daemon

So, I went into the sessions manager, and added that to the start up. I rebooted and I saw that indeed gdkeslets was loaded on startup, however my desklets themselves didn't appear.  I had to right click the icon in the tray, and choose "configuration" for them to appear.  Is there any command I am missing to get them to auto load.  I even tried my shortcut key to see if they would appear, but they did not.  Any idea is very much appreciated, thank you.

---

### Post by raldz on 2006-09-17
what I did was just add "gdesklets" to the Session Start Up list.. it works fine.. the desklets (I have 3) loads perfectly..

---

### Post by orb9220 on 2006-09-17
Yep that is all you should have in startup is gdesklets

---

### Post by 3rr0r on 2006-09-18
I'll try that when I get home, thanks for the responses.

---

### Post by 3rr0r on 2006-09-19
sucess!

---

### Post by dannyboy79 on 2006-09-22
yeah, that works but then you also get the bash shell that opens as well and you have to click on the "x" in the upper right hand corner to close it or go into the file menu and click quit. Are you guys not getting the shell showing up as well as your gdesklets by adding gdesklets to your startup within sessions? Maybe I need to double check what I added into startup?

---

### Post by Brunellus on 2006-09-22
> **3rr0r said:**
> sucess!
w00t.  I love it when a plan comes together.

---

### Post by raldz on 2006-09-22
> **dannyboy79 said:**
> yeah, that works but then you also get the bash shell that opens as well and you have to click on the "x" in the upper right hand corner to close it or go into the file menu and click quit. Are you guys not getting the shell showing up as well as your gdesklets by adding gdesklets to your startup within sessions? Maybe I need to double check what I added into startup?

Yup, I can see the shell showing up.. but only for about 2 seconds, then it closes automatically..

---

