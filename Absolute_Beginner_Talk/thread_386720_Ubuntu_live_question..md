---
title: "Ubuntu live question."
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Radiotracker on 2007-03-17
Im using a free bootmanager called OSL2000. I tried to boot ubuntu once but i got a message saying that is should set it up to boot my HDD first then my CDROM.
 
I need help, Please :(

---

### Post by Zuuswa on 2007-03-17
The option to boot from cd or first hard drive should be set within your BIOS.  When your computer first powers up, you should see a screen telling you to hit a key (usually F12 or F10 or something similar) before it starts loading the boot manager. For me it says F10 for boot options, F12 for network boot or DEL for setup.

---

### Post by Radiotracker on 2007-03-17
ok. my keys are F2(bios) and F12(boot options). I'll have to try that.
I hope there are no compatibility issues with my dell.
 
Dell 2350
Windows XP pro
Intel P4 2.2GHz
60 GB HDD
256 MB RAM
EVGA Nvidia geforce fx5500
soundmax onboard sound

---

### Post by zvacet on 2007-03-17
Go to the bios and pick advanced bios features>boot sequences(or something symilar)and  choose your firs boot device to be cdrom.Save and exit.Now you can boot from your CD.

---

### Post by Radiotracker on 2007-03-17
ok. thanks for the help. :guitar:

---

### Post by Radiotracker on 2007-03-18
:(  It helped me get past the OSL2000 message, but im still having problems.
 
it acts like everything going smooth but after the Ubuntu load screen goes away.
a dos cursor will blink for about 30 seconds then i get this screenfull of messages.
it wont go further than that. :(

---

### Post by h0ax on 2007-03-18
You may want to try it in "Safe Mode" on the boot - 
or elaborate on what the "screenful of messages" is so we can try to help that way

---

### Post by Radiotracker on 2007-03-18
[17179620.012000] times A Fraggin million or more.
 
 
I just noticed that its probably about 2-5 screenfuls of info. it's too much to write down.
it's mainly numbers and other stuff. i can give you 2 of the lines though.
 
 
[17179620.012000]   <0> kernel panic - not syncing fatal exception in interrupt address or something like that.
 
 
and   <1>   BUG: unable to handel kernel paging request at virtual address.

---

### Post by Radiotracker on 2007-03-18
I just tried booting in safe mode and that didn't work.  :mad:

---

