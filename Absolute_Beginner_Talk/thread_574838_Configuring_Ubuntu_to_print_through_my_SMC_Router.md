---
title: "Configuring Ubuntu to print through my SMC Router"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by duckblind123 on 2007-10-13
I have an SMC Barricade-g Router (SMC2804WBRP-G) and am trying to configure the printer on Ubuntu to work.
The printer is the same one I use for my Windows partitionand it works fine there.  I have tried to install the printer
using the System - Administration - Printers method, but have not had any luck with that.  I have tried all four of the different types of set-ups for the printer (CUPS, Windows, Unix, etc..) and nother had worked.  I can ping the router ip okay.  I am farily new to Ubuntu, but am willing to learn at a fast pace.  Any assistance that can be provided to resolve this would be great.
Thanks, duckblind123

---

### Post by NavmaN on 2007-10-13
Are you connected to the internet through the router?

How is the printer connected to your Ubuntu box?

Van

---

### Post by duckblind123 on 2007-10-13
I am connected to the Internet through the SMC router.  The printer is connected directly to the SMC router (as the router also has a print server).  I have a Desktop PC that is loaded with both Windows XP and Ubuntu and that PC is hard wired to the router.  When I boot into Windows, the printer works fine, but when I boot into Ubuntu, I am having difficulty in configring the printer to work.  FYI:  I also use this same printer to share with a laptop running wireless to the same router.
Thanks, duckblind123

---

### Post by duckblind123 on 2007-10-14
RESOLVED - I was able to figure out by setting the printer as a Unix printer and loading in 192.168.2.1 as the Host and LPT1 as the Queue, it works.
Thanks,  duckblind123

---

### Post by Muki on 2007-10-17
Hey!

I am having the same problem. Could you please give more detail on how and where you defined the host and the queue settings? With a special entry in the /etc/printcap maybe? What was the entry?

Thanks in advance.

---

