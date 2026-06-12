---
title: "Monitor problem"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by andrew222 on 2006-11-14
I just bought a new LG L194WT Flatron monitor and after I hook it up and start my computer, I then see the Ubuntu startup splash screen and then the monitor goes blank with a message in a box ( from the monitor ) saying 'Analog out of range  60 Hz'.

I then restart and go to my Windows partition and everything works fine.

I bought an Envision monitor and it gave me the same thing, once Ubuntu loads up, blank screen.

Should I buy a digital connector? Is it a driver issue?

I hope to hear from one of you soon. 

Andrew

---

### Post by schrombot on 2006-11-14
It sounds like the X server is still trying to use the settings from the old monitor. When the screen goes blank press CTRL+ALT+F2, login at the command prompt, and run ```
sudo dpkg-reconfigure xserver-xorg
```Put in all the information it asks for, some of the stuff will probably be in the monitor documentation, and see if that helps.

---

### Post by andrew222 on 2006-11-14
Thank you very much, I'm going to try it out right now. I'll let you know how it works out.

Andrew

---

### Post by andrew222 on 2006-11-14
It worked like a charm, I'm writing this from my Linux partition. schrombot, you're a star.

Thanks again,

Andrew

---

### Post by schrombot on 2006-11-14
Glad I could help.

---

