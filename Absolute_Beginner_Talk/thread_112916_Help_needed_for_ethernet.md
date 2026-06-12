---
title: "Help needed for ethernet"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by mikyor on 2006-01-05
I recently installed Ubuntu 5.10 and everything seems to work fine except the internet.  I am able to ping my router and other websites.  In my  internet browser (firefox) I can log into my router but I cannot reach any websites.  

I have a linksys router and it is set to DHCP, and my ethernet connection is plugged in and working properly(the lights blink).

Could anyone help me out on this issue?

---

### Post by jonathanm on 2006-01-05
try restarting your router, taking power out and put it back in, that usually works

---

### Post by darckhart on 2006-01-05
i think you may have a DNS problem, and just need to add some DNS servers to your list. 

check your router settings to make sure you have the DNS servers' ip addresses plugged in. (on my linksys router there;s a section for it on the setup page.)

if they are, then check your network card. there's probly a gui way to do this, but i can't remember at the moment...

so, just sudo gedit /etc/network/interfaces

look for the lines something like 'iface eth0'. look near the bottom of that list for that device and there should be some spots to type in your DNS server's ip addresses. i use sbc up in northern california, so their servers are 206.13.31.12, 206.13.28.12, and 206.13.29.12.

---

### Post by mikyor on 2006-01-05
jonathanm thank you for that tip, I tried so many things but forgot to try that =(

---

