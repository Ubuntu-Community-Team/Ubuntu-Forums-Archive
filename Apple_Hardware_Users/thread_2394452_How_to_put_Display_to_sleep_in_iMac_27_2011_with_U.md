---
title: "How to put Display to sleep in iMac 27 2011 with Ubuntu Server 18.04 LTS WITHOUT X"
date: 2018-06-16
forum: Apple Hardware Users
---

### Post by aibix on 2018-06-16
Hi there,

problem as stated in the topic. 

I repurposed an old iMac as an ubuntu server, since the hardware is still quite powerful, but I don't like the display resolution any more.

Now everything is working just fine, except the display stays on forever, showing nothing but the login prompt (console).

All searches on the internet turn up people with the opposite problem - blank screen. I wonder how I can have a blank screen?

dpms and other suggestions involving xset and stuff don't work, since the machine complains about not being able to "open" the display or failing "real mode calls" (vbetool).

So, what's the trick?

/w best regards
aibix

---

### Post by mörgæs on 2018-06-17
HI, welcome to the fora.

We need to know the hardware details. While running a live boot please copy and paste ```
sudo lshw -sanitize > lshw.txt
``` to the command line, execute it and post lshw.txt in CODE tags.

---

