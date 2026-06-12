---
title: "[SOLVED] Mini-cd Icewm ubuntu, won't find my USB hard drive?"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Jareth on 2008-04-11
Hi, I tried this yesterday:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

It all went well and I'm happy because at least I have my terminal and firefox.
But what I was wondering was when I plug in my USB hard drive it doesn't appear anywhere. I have thunar installed and its not there or in the /media folder.

Basicaly I haven't a clue so if anyone can teach me something I didn't know yesterday that'd be great.

Thanks

---

### Post by K.Mandla on 2008-04-11
If you started from a minimal installation, there's probably nothing running as an automounter for you. I don't recall if Thunar will show recognized-but-unmounted drives in its sidebar or not.

PCManFM is a very lightweight file manager that can do that. You also might want to look into automounting programs like ivman. Setting those up can be very time consuming though. 

If you're really interested, you can do these things manually, like [this]("http://kmandla.wordpress.com/2007/03/08/howto-mounting-without-sudo/").

---

### Post by Jareth on 2008-04-12
Yup thats great, all I did was install ivman from synaptic and now it can see USB drives in thunar and I can play from it in VLC.

Smashing, thanks very much!

(Another one solved)

---

