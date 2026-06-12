---
title: "Help getting me online"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Gord0n on 2006-09-17
Ubuntu 32bit 6.06
Athlon64 3000+ s939
nvidia 7600gt
1.5gig pc3200
ASROCK Dual939-Sata2
Dualboot with winxp
Shaw Highspeed cablemodem
no router. Connect strait to the web.

I have installed fine. It recognized my Network Hardware, but failed the Auto DHCP, so i skipped it. 

After install, I do not have internet capabilities. I tried to setup with DHCP and activating my eth0, didnt work. Then i tried to setup with a static IP. (which i believe i have) and still nothing. 

Any help or suggestions would be appreciated.

---

### Post by mongooseman1128 on 2006-09-17
double check if you can ping at all (try google, it always works for me) if you can ping than it's probably mozilla. type in "about:config" in the URL bar, then in the filter field type in "ipv6" and double click the far right column so that it says true. That fixed my connecting problem when I first installed ubuntu

---

### Post by Gord0n on 2006-09-17
said the address "www.google.com" could not be found, so i guess we have no connection

---

### Post by Najand on 2006-09-17
Cable Modems keep your MAC Address and that is why they cannot make a new connection to the new OS. The easiest way is:
To Trun your IP Setting back to DHCP
Then shut it down....
Turn off your modem for 5 min or something
Then turn it on again and boot your computer afterwards.

---

### Post by Papa-san on 2006-09-17
open a terminal and type:
```
 ping google
```

---

### Post by mongooseman1128 on 2006-09-17
go to system> administration> network tools. in there is a tab for ping. if that works go ahead and do the "about:config" steps and let me know if it works

---

### Post by crokett on 2006-09-17
> **Gord0n said:**
> sorry, but how do i ping??

open a terminal session

type: ```


ping xxx.xxx.xxx.xxx


```

where xxx.xxx.xxx.xxx is an ip address.

---

### Post by Gord0n on 2006-09-17
> **Najand said:**
> Cable Modems keep your MAC Address and that is why they cannot make a new connection to the new OS. The easiest way is:
To Trun your IP Setting back to DHCP
Then shut it down....
Turn off your modem for 5 min or something
Then turn it on again and boot your computer afterwards.

Didnt seem to fix anything

> **Papa-san said:**
> open a terminal and type:
```
 ping google
```

Got an "unkown host" response

---

### Post by Gord0n on 2006-09-17
I have done the "about:config" steps, and still nothing.

---

### Post by Gord0n on 2006-09-17
I tried pinging my IP and it says "network unreachable"

---

### Post by comppsyco on 2006-09-17
Give this a try: shut down, cut the power for 30 seconds, and power back up. I know it sounds absurd, but aparently winxp likes to put some kind of gobbledigook in your network card that ubuntu can't read. It worked for me.
Worth a try.

---

### Post by Najand on 2006-09-17
That was the trick I told him and he said, not working.

---

### Post by Gord0n on 2006-09-17
Could there be an issue with my ASrock dual939-sata2 mobo onboard ethernet?

---

### Post by Najand on 2006-09-17
No, if it has been detected.

---

### Post by Gord0n on 2006-09-17
How do I know if it has been detected properly??

---

### Post by mongooseman1128 on 2006-09-17
did you check under system> administration> networking and make sure that etho0 is the default and is configured correctly

---

### Post by Gord0n on 2006-09-18
Yes it defaults to eth0, but how do i know if its configured correctly.

The DHCP autoconfig failed during install, I have tried to set it up in Ubuntu after install, and havetried static IP, typing in my ip address. Both havent worked

Thanks everyone for the help, Thier must be a way to get this working.

---

### Post by Gord0n on 2006-09-18
Anyone else have any Ideas. This has got to work.

---

### Post by spur on 2006-09-18
Do you have only the one eth card?

---

### Post by kdub432 on 2006-09-19
There IS a problem with the onboard ethernet card on the ASrock dual939-sata2 cards. I have this mobo and this problem is the only thing preventing me from switching to linux. However, I found a driver for this particular onboard ethernet card. Unfortunately for me though, its a .c file, which I would assume needs to be compiled into the kernel or something, and I havent the foggiest idea on how to do so. I would appreciate it if someone could help.....

---

