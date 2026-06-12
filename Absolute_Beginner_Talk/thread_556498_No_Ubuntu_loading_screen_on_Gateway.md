---
title: "No Ubuntu loading screen on Gateway"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-09-21
I recently installed 6.10 and 7.04 on a Gateway 500S. At boot-up, I don't get the Ubuntu loading window with the bar that shows loading progress. The screen just stays black until the log-in window appears.
Is there a way to make the Ubuntu loading window come-up as it does on my IBM NetVista?
Thanks

---

### Post by Pumalite on 2007-09-21
Do you have a long booting time?

---

### Post by Toet on 2007-09-21
I had the same problem with my gf8500gt. What kind of card is in your box?

---

### Post by LowSky on 2007-09-21
I'm having this issue with 7.10 but there isn't a fix yet.

its ubuntu and its your video card.. search for a program called envy, it will help fix your issues

---

### Post by alienexplorers on 2007-09-21
For the ENVY script follow the link in my sig line.

---

### Post by Pumalite on 2007-09-21
If you have what you describe, the kernel is trying to load modules for hardware that doesn't seem to find in your machine.

---

### Post by Stunt Double on 2007-09-21
Boot-up time to the log-in window on the Gateway (2.0Ghz + 512 MB PC 2100) is 2 mins. 45 secs. On the IBM NetVista (700 Mhz + 512 MB PC133) it's 1 min. 50 secs.
     The video is built into the Motherboard which is an Intel (Essex) Pentium 4 R2. 
   I'll try Envy and report back.
 A side note: When I tried to run 7.04 and 6.10 via live CD on my HP 522n (1.8 Ghz + 768 MB), I never got past the black screen with a flashing white cursor line at the top left. In all cases, I used the same Ubuntu CDs which worked perfectly the first time on the NetVista.
Thanks

---

### Post by Pumalite on 2007-09-21
Try this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by Stunt Double on 2007-09-21
Thanks.
I'll be away from my main machines until Tuesday. I'll post my results when I return.

---

