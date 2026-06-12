---
title: "Trying to set ppp0 mtu , to optimize dial-up"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Silvain on 2007-12-21
I have been trying to adjust my dial-up mtu
One of the post I found said to use ifconfig command to check running configuration.
Does this paste show success ?
====================paste======================
ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:xxx.xx.xx.xxx  P-t-P:xxx.xx.xx.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:548  Metric:1
          RX packets:1047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:437083 (426.8 KB)  TX bytes:155343 (151.7 KB)
==============================================

I see one section it says MTU:548

---

### Post by kajillin on 2007-12-21
your MTU (Maximum Transmission Unit) cannot be changed, it is assigned by your isp and detected by your OS. To try and change it is like trying to use the force to grab your pen.

---

### Post by Silvain on 2007-12-21
Really your saying that a networking parameter is non adjustable ? Have always adjusted the packet sizes on other OS in past here. Maybe you can try executing the command I listed in my paste to see what kind of return messages you are getting ? Probably Ubuntu does work different from windows OS . But I have read several posting about adjusting MTU on this forum, so maybe we both have some things to learn still :)

My opinion here from past OS uses:
The whole point of adjusting the MTU , I have always done it in past on windows dial-ups set ups. We all know that the ISP will only accept so large of a packet size. The other factor is network routers or internal links used by my ISP. 

The Ubuntus dialer logs keep saying that it is using 1500 something, Im pretty sure that is, way large. Since in past set-ups my optimum returns on my ISP in past when doing a no fragment ping was around 548 to a site on the web.The whole point of adjusting it down is to avoid packet fragmentation. Also I do believe that on my phone lines out here , shorter packets, equal less chances of needing to do retransmissions due to errors from phone line noise.

---

### Post by plucky on 2007-12-21
Silvain,

Checkout **man ifconfig** for the command to change the value of MTU.It should be something like this.

```
sudo ifconfig ppp0 mtu 576
```

I think 576 is the optimum value for dial up modems,but I don't use dial up so cannot test this theory.
Any changes are at your own risk.

Good luck

---

### Post by Silvain on 2007-12-22
plucky,

Tried out the "man ifconfig" in the command terminal. Was wanting to copy and paste part of it. But again my knowledge fell short and when arriving at the end of the manual. All I could do was close out the terminal. 

So much to learn still here  :lolflag:

Will try out that command later on to see if my returns from the prior command change any  sometime tomorrow.

Thanks :)

---

### Post by Shazaam on 2007-12-22
On my pc that command only changes the mtu for the current connection. It resets back to 1500 when I re-dial. I will scrounge around in my config files to see where to make it permanent.

---

### Post by plucky on 2007-12-22
To exit from the manual terminal page just type **q**

to get the manual page as a text file, open a terminal and input

```
man ifconfig > config.txt
```

will create a text file in your current directory.

Cheers

---

### Post by Silvain on 2007-12-22
Thanks for the info again:) here is my output from playing at the CLI.
Before and then after:
Begins paste---------------------- IP blotted out--------------------------------------
$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:2XX.xx.xx.xxx  P-t-P:2xx.xx.xx.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:548  Metric:1
          RX packets:1883 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1728 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:768558 (750.5 KB)  TX bytes:252983 (247.0 KB)

silvain@silvain-desktop:~$ sudo ifconfig ppp0 mtu 549
[sudo] password for silvain:
silvain@silvain-desktop:~$ ifconfig ppp0
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:2xx.xx.xx.xxx  P-t-P:2xx.xx.xx.x  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:549  Metric:1
          RX packets:1884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:769043 (751.0 KB)  TX bytes:253496 (247.5 KB)

----------------------------------------------------------------------------------------------------------
Yeah! It definitely works.
This command code: sudo ifconfig ppp0 mut xxx 
Should be quite handy for testing different MTU settings.

Now I need to lookup how to send a ping with no fragment bit set so I can check results. Been a while since I have done that and the command is probably parsed differently in Ubuntu than in Windows. Time to search some.

---

