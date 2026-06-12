---
title: "First time Linux user (I NEED HELP)"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by clinty on 2007-06-05
I'm having problems with my screen resolution. I know there is a page that covers almost every possibility for what the problem is and how to fix it but i thought it may be faster to ask for some help. I just installed linux on my old computer because i thought it might help prolong it's life time. It has an oldd video card: 3dfx Voodoo Banshee(16mb) but it's capable of more than 800x600 resolution.

It's weird because when I was using Ubuntu on the live cd, I had a nice 1024x768 resolution.
When I start up Ubuntu and log-in, I still have 1024x768.
However when the loading screen pops up, my pointer becomes huge and my resolution is scaled down to 800x600.

thanks in advance.

---

### Post by jonward0690 on 2007-06-05
Well you can't adjust your scree resolution at all.

---

### Post by jonward0690 on 2007-06-05
Or try this type this in the terminal "sudo dpkg-reconfigure xserver-xorg"

---

### Post by rich.bradshaw on 2007-06-05
Can you change it in System/Preferences/Screen Resolution?

---

### Post by clinty on 2007-06-05
uhh what?
If you're asking me if I personally can then the answer is yes, i can change between 800x600 or 640x480

i tried running the configuration again. Do i need to restart before it takes effect or should it be fixed now? If it should be fixed now, it didn't work.

---

### Post by jonward0690 on 2007-06-05
Well try typing "sudo dpkg-reconfigure xserver-xorg"

---

### Post by Jussi Kukkonen on 2007-06-05
*Please* use descriptive post titles: You will get more (expert) help, and others will not have to load something they have no expertise on. example: *"no 1024x768 reso with 3dfx Voodoo (works in liveCD)"*

---

