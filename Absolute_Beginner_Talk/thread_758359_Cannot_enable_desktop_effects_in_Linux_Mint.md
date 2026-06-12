---
title: "Cannot enable desktop effects in Linux Mint"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by tstack77 on 2008-04-17
I had been using Gutsy for a few months without problems but decided to give Linux Mint a go-around after I backed up everything in anticipation of Hardy. I have a fresh install with the suggested nVidia driver installed (latest for 7800 GT, and restarted), but I can't enable desktop effects... any ideas?

---

### Post by Hospadar on 2008-04-17
do you have video acceleration? try running "glxgears" from the terminal, if it gives you nice 3d gears, then 3d acceleration is working, if not then you've got issues

Also, could you post a copy your /etc/xorg.conf

---

### Post by tstack77 on 2008-04-17
Ok, I got the gears. I still cannot enable compiz desktop effects though. I tried to download the settings manager but that didn't help. 

What else can I do?

---

### Post by thefishki345 on 2008-04-17
Have you tried going into
system-administration-hardware drivers/restricted drivers/whatever and enabling the driver from there then try desktop effects. Thats what I had to do with my 8800gts

---

### Post by tstack77 on 2008-04-18
Yeah, I have the driver checked/enabled.

I forgot to mention that I have a dual-monitor setup and am able to use the 7800GT to configure them. Everything works besides compiz.

---

### Post by tstack77 on 2008-04-18
help :confused:

---

### Post by SunnyRabbiera on 2008-04-18
you might want to take this over to the linux mint forums.
did you use envy by the way?

---

