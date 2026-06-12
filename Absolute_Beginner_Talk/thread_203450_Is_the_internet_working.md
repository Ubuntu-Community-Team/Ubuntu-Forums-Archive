---
title: "Is the internet working??"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-25
I am connected to the net. But how do i know that i am connected or not.:confused: 

usually i open the firefox browser and open google.com. If a page comes then i am connected or else i am not.

Is there a sure way by which i can know that i connected or not cuz i have a limited time of internet.:rolleyes:

---

### Post by Maggot on 2006-06-25
I'll assume you are on dialup. Add the Modem Monitor applet. Right mouse click on Panel, Add to Panel

---

### Post by hardfire_avk on 2006-06-25
No!!

I have a cable internet which get's connected through a LAN. But however I have the hourly pakage rathar than the unlimited package.

---

### Post by T700 on 2006-06-25
Open Firefox, clear the browser cache (method varies by the version), and go to a website.  If it loads, you are connected to the internet.

Or...

Click on a link to somewhere you have not gone before.  If it loads, you are connected.

Or...

Go to a website and press Ctrl-R and if it loads, you are connected.

Good luck,
Paul

---

### Post by vibhu on 2006-06-25
I am not too sure if I got the question right, so here are 2 ways of looking at it :

**Way 1**:
1. Open a Terminal ( Applications -> Accessories -> Terminal ).
2. Type : ping [www.google.com](www.google.com). You should get something like : 
```

vibhu@ubuntu:~$ ping www.google.com
PING www.l.google.com (66.102.7.147) 56(84) bytes of data.
64 bytes from 66.102.7.147: icmp_seq=1 ttl=240 time=270 ms
64 bytes from 66.102.7.147: icmp_seq=2 ttl=239 time=286 ms
64 bytes from 66.102.7.147: icmp_seq=3 ttl=240 time=337 ms
64 bytes from 66.102.7.147: icmp_seq=4 ttl=240 time=286 ms
64 bytes from 66.102.7.147: icmp_seq=5 ttl=240 time=295 ms
64 bytes from 66.102.7.147: icmp_seq=6 ttl=240 time=283 ms
64 bytes from 66.102.7.147: icmp_seq=7 ttl=240 time=334 ms

--- www.l.google.com ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7011ms
rtt min/avg/max/mdev = 270.365/299.183/337.076/24.108 ms

```
(You will need to do a ctrl+c to quit out of ping).

**Way 2**:
1. Right click on the taskbar at the top. 
2. Click on "Add to Panel"
3. Scroll down to "System and Hardware" and click on "Network Monitor". Click "Add".
4. You should get something like the double monitor icon in top right as in the pic : 
[http://bladra.is-a-geek.org/extra/Screenshot.png](http://bladra.is-a-geek.org/extra/Screenshot.png) (2nd icon to left of 57F). This will show whether you are connected (no icons on it) or not ( will have ! or x if the network is not connected - you can try by removing the cable and seeing if it works).

Hope that answers your question !

---

### Post by Maggot on 2006-06-25
[QUOTE=hardfire_avk]No!!

I have a cable internet which get's connected through a LAN. But however I have the hourly pakage rathar than the unlimited package.[/QUOTE]
Ok, do the same thing but instead of adding Modem Monitor add network monitor ;)

edit: Oopss....vibhu already mentioned that :-D

---

### Post by hardfire_avk on 2006-06-25
Thank you. The network monitor did work..

---

