---
title: "Internet Connection"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by DDM1 on 2006-02-09
Hi,

I just recieved Ubuntu today and am so excited. I used the Live CD and cannot seem to connect to the internet. It installed great. Sound and video work. My ISP is Sympatico. I read the help files but seem to be stuck. If I did th "ifconfig eth0" right it is picking it up. Thanks for your help.

DDM1

EDIT...forgot to add that I am using a Slipstream modem provided by Bell/Sympatico

---

### Post by jasmuz on 2006-02-09
Try this to autoconfigure it (hope this works...depending if Sympatico uses DHCP):

$ sudo dhclient eth0

---

### Post by SigMtnDawg on 2006-02-09
jazmuz, i am trying your suggestion, but it's been going on for a couple of hours.  how long does this take?

thanks

---

### Post by aragorn2909 on 2006-02-10
SigMtnDawg:  Seeing as Sympatico is your ISP, I'm guessing you have a *Speedstream* 5200 or 4200 modem.  Just log into your modem's web interface (192.168.2.1 or something) and plug in your b1 user id and your password, and let the modem take care of the pppoe, instead of the OS.  Much simpler that way.

A

---

### Post by DDM1 on 2006-02-10
Thank-You for your responses. I will try them out tonight when I have more time. And yes, Sympatico site told me to use 192.168.2.1.

DDM1

---

### Post by SigMtnDawg on 2006-02-10
actually, my ISP is Comcast.  i was following the instructions above to try to get my network connection going, because i do have DHCP.  perhaps this is the wrong route.  anyway, it has been about 10 hours and the program is still running.  should i try to stop it and try your solution, aragorn?  if so, how do i stop the autoconfigure?

thanks

---

### Post by dle on 2006-03-17
[QUOTE=aragorn2909]SigMtnDawg:  Seeing as Sympatico is your ISP, I'm guessing you have a *Speedstream* 5200 or 4200 modem.  Just log into your modem's web interface (192.168.2.1 or something) and plug in your b1 user id and your password, and let the modem take care of the pppoe, instead of the OS.  Much simpler that way.

A[/QUOTE]

Log into it with telnet, is that right?

---

