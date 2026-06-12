---
title: "I Need Proper Ubuntu for TOR Server.."
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by gecko_90410 on 2007-07-28
Hi Experienced Ubuntu People!
I am planning on using Ubuntu as a platform for a TOR server,,Do I use Ubuntu Server or Desktop Ubuntu? This is my first experiment with a server of any kind and Linux. I have Intel P3 800 MHZ processor on Compaq board with 256 MB ECC RAM and a broadband internet connection. Is that hardware adequte for dedicated TOR server machine or will I need hardware upgrade?
Comments, hints or just plain good advice gold here ,,Thanks in advance,
                                                                                                                      Gecko

---

### Post by Golyadkin on 2007-07-28
Both would work equally well, but if you really do nothing else on the machine than having it run a dedicated Tor server, I would go for a completely nailed shut server version. Close every port and every service you don't need. Don't install any programs you don't need, and let it run in textmode (init 3, runlevel 3) for maximum performance. Just tunnel into it with SSH, or if you really have to, VNC. 
Tor is not that heavy on the computer, unless you expect it to work with thousands of connections all the time.

---

### Post by gecko_90410 on 2007-07-30
Thank you so much for helping me understand the basics of using Ubuntu with TOR,, Will post results of my experience on this board..
                                                  Gekco

---

