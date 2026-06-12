---
title: "PCI network card not working"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Squizz on 2008-02-26
I've been running Gutsy as a headless server for about a week or so now, but for some reason I can no longer ssh or vnc into the machine.

I'm using a PCI ethernet networking card (as I found it impossible to set up my USR wireless usb) and the light is now on red, instead of green(!).  I've checked the ethernet cable and if I plug it into a laptop then it works just fine.

Is it likely that the card has fried?  Is there a way to check without having to attach a monitor (as that would be a pain).

I didn't get permission from my ISP to use it as a server, and the computer is permanently assigned to 192.168.1.100 so is there a chance my isp has simply blocked that computer without telling me?

Any suggestions?

---

### Post by notwen on 2008-02-26
First let's see if Ubuntu even recognizes your card.  Open up a terminal and type in the following command and paste back your results:

```
lspci
```

---

### Post by Squizz on 2008-02-26
I just plugged in a monitor and it's not even booting in Ubuntu.  Just my luck!

I guess I'll have to try and fix it before I do anything else, btu thanks for your help anyway :D

---

