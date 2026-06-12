---
title: "Wireless sucks on 6,2 10.10"
date: 2011-05-02
forum: Apple Hardware Users
---

### Post by disappearedng on 2011-05-02
Hi everyone

I checked into my new hotel. So currently I am using 6,2 on 10.10. I know wireless is kind of spotty on macbookpros so I have followed the guide pretty closely. I have done the following:
[LIST=1]
[*]compiled and installed the latest wireless driver from broadcom on 64bit 
[*]placed a script called wireless with chmod +x that does iwconfig eth1 power off
[*]manually use iwconfig eth1 power off
[*]change back to the original wl.ko with depmod and modprobe 
[/LIST]

It turns out that I am seeing massive packet loss pinging to Google. My first intution told me to check if power management is off and indeed it was. then I decided that maybe my wireless driver is crap so I rolled back to the original driver. I pinged again and massive packet loss as well. I manually make sure that iwconfig power management is always off for optimal performance. 

So I guess it might be that my network is ***** so I booted from mac and did a ping to google for 30 mins. Not a single packet dropped. On my ubuntu, packet drop occurs every 3-5 mins and total packet loss is 72%. 

So my question is, why is ubuntu macbookpro's wireless so sh!tty? I am pretty forced to drop back to Mac everytime something wrong with wireless occurs. Has anyone had any luck working around this (like installing 32 bit drivers rather than 64 bit?). Why does Broadcom's linux driver suck so bad? (Should we blame broadcom or the kernel?)

Please enlighten me.

---

### Post by kozhy on 2011-05-07
i was trying a several options but without found the solution for this issue, and 
this answer i found it in a another forum but it work for me, i hope that it helps you 


> editing /etc/laptop-mode/conf.d/wireless-power.conf

changing WIRELESS_BATT_POWER_SAVING=1 to WIRELESS_BATT_POWER_SAVING=0 

and then restart laptop-mode (or reboot).

---

