---
title: "Wired and Wireless cards not working (PCMCIA)"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Voodoo Child on 2007-06-09
a beginner. Duhr. 

I've tried everything in my power to get these things to work, including reinstalling the ubuntu FF program several times.  

I have a MN-520 wireless card. It's reading it, and recognizing my wireless signal, but it still isn't working. I've even gone to the terminal.

We've also tried some other wireless cards, and they still won't work. 

I have plugged in the numbers for the IP address and everything. I need help

Frustration.  Grr.

---

### Post by matthewboh on 2007-06-09
FF program?

I've found NetworkManager to be pretty good, however you need to comment out everything in your /etc/network/interfaces file EXCEPT for lo, reboot the machine and use NetworkManager to connect

---

