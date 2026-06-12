---
title: "[SOLVED] Mute audio from virtual console?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by 42Wired on 2008-04-07
In class, it's very embarrassing when I start up my laptop and the Ubuntu login sound comes blasting out of my speakers. I don't want to disable it the login sound altogether.

Is there a way to mute the audio before I log in using a virtual console?

---

### Post by Slushdoot on 2008-04-07
You could turn the master audio down with alsamixer before loggin on.

Also, you could also turn the volume down with the GUI volume applet before you log off the prevous session.

These ways are how I do it.

---

### Post by 42Wired on 2008-04-07
My point is that I forget to do that before I shut down sometimes. If I'm already in class, I can't access the GUI without first logging in, which triggers the sound.

---

### Post by ladwinster on 2008-04-07
You can always connect some headphones before log in :P

---

### Post by 42Wired on 2008-04-07
That wouldn't be a bad idea.

But I still want to know how to do it.

---

### Post by Slushdoot on 2008-04-07
At the GDM login screen press ctrl alt F2.  This will take your to a CLI login prompt.  Enter your username and password then you'll be presented with a command prompt.  Type alsamixer and use the arrow keys to turn the master volume all the way down.  When you're ready exit that and run startx to enter your X session.

You may have to install alsamixer before using it.  I can't remember if it comes with the base system or not.

---

### Post by 42Wired on 2008-04-07
Sweet. I was looking for something like that. Thanks.

---

### Post by Slushdoot on 2008-04-07
You're welcome. :)

---

