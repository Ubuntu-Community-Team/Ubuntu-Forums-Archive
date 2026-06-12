---
title: "Baffled About Non-Working Internet"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by flowingfire on 2007-05-15
Hi Everybody,

I was hoping an easy fix might make my Internet work again.  It has been working without difficulty for several weeks now, but not anymore.

What happens is that I boot up, and the Network Manager shows that I'm connected to my network, even showing bars of signal.  It definately is connecting.  I go into the system settings, and it even shows an IP address.  

BUT- nothing works.  Konqueror, Firefox, and Opera can't connect.  Apt-get and the package managers can't connect.  Nothing is connecting to the Internet.  I find this strange, given that the wireless card is receiving signal and registers an IP address.

Why is this not working?  How can I get it working again?  

Thanks,
-David

---

### Post by swisscow on 2007-05-16
Hi, I don't know if this will help but you never know....

If I have exactly the same situation you have (network says it's connected wirelessly but can't get anything). I use my browser to connect to the wireless router, find the bit which says DHCP. It usually says *connected*, but if I'm having a problem it says *disconnected*. Clicking** DHCP connect** then solves all my problems (well with the Internet anyway!)

I'm by no means clear on what all these things do, I just know I need DHCP working.

Hope it helps

---

### Post by Whiffle on 2007-05-16
What happens if you open a terminal and try to ping your router, and how about a website?  Network manager is being most screwy as of late.

---

### Post by flowingfire on 2007-05-16
Hi.  I just checked my wireless router, but it appears the DHCP is working fine.  In fact, it even shows my Ubuntu computer connected to IP Address 192.168.0.102 bound to a specific mac address.  Notably, 192.168.0.102 is the same IP address that the Ubuntu computer says it's connected to....

So my real problem is that I see absolutely no indication that this isn't working from a technical standpoint, but it's -just- not working for some strange reason.

I took the advice, and opened the terminal to type: ping 192.168.0.1.  (That's the address of my router.)  The results were many repeated lines showing a DIFFERENT IP address (192.168.0.125) and saying "destination unreachable."  I think that's fairly revelatory.

Thanks for the help... Give the ping results, I might be able to deduce the problem on my own now... But input is still welcome.

---

### Post by medad on 2007-05-16
What are your router and wireless types?  When my system wasn't working correctly, I used to turn off and on my router to see if the wireless connection would re-connect.

---

### Post by flowingfire on 2007-05-16
Thanks. Internet is working now.... hmm...

---

### Post by decdi02 on 2007-05-16
I'm experiencing the same problem.  How did you fix this?
thanks,
didier

---

