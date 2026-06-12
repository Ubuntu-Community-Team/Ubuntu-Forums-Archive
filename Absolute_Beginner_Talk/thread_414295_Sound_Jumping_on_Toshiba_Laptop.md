---
title: "Sound Jumping on Toshiba Laptop"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2007-04-19
I had Edgy before today, everything worked great. Did a fresh install today, and everything's working great, except the sound. It's usually almost mute, even with the volume all the way up, but for a couple seconds at a time every 7 seconds or so, it'll jump up. It's pretty much impossible to listen to anything. Ideas?

EDIT: Fixed, see below.

---

### Post by cam2009 on 2007-04-19
Got it fixed. involved adding something about alsa to a file...I can dig it up if anyone needs it, I can't seem to find it...

Also, could somebody tell me the default Amarok font? I never had trouble before, but there is something wrong with the font. I'm using kcontrol, and while it isn't ugly, I'd like what it was before. Thanks.

---

### Post by lazyrussian on 2007-04-19
ya plse help. I have a toshiba with the same problem

---

### Post by cam2009 on 2007-04-19
> **lazyrussian said:**
> ya plse help. I have a toshiba with the same problem
found it. in terminal:

> sudo gedit  /etc/modprobe.d/alsa-base

scroll down to the bottom and add this:
> 
options snd-hda-intel model=auto

I had to restart the computer completely for it to work, but it did.

---

### Post by lazyrussian on 2007-04-19
thanks. I'll try it in a sec and report my results

---

### Post by dangerpl on 2007-04-19
ah exactly what i was looking for! Lots of people were looking for this! :)

---

### Post by lazyrussian on 2007-04-19
Didn't work. I'm going to try this guide here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by lazyrussian on 2007-04-19
Still doesn't work :(

---

