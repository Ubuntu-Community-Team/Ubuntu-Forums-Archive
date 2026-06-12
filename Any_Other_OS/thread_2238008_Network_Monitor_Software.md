---
title: "Network Monitor Software"
date: 2014-08-05
forum: Any Other OS
---

### Post by ramakanta on 2014-08-05
In office , 10PC ,with broadband connection (share one BB  business plan ) . I want to known from Master PC ( or any one PC from 10) , which user usages how many data(download +upload ). is it possible  . then which software I will used for that ?? . thank you.

---

### Post by TheFu on 2014-08-05
Only if all the traffic goes through a device can it report what traffic is happening.  A leaf PC cannot know about traffic from others on the network.

Well, that isn't completely true.  If you have a router that is making the connection to the ISP, then that device, with some firmware, can report traffic using SMNP, to another system for analysis.  I hope that makes sense.  Often, it is easier to just use firmware on a router to see the traffic - tomato [http://www.howtogeek.com/74881/how-to-monitor-and-log-your-bandwidth-usage-with-tomato/](http://www.howtogeek.com/74881/how-to-monitor-and-log-your-bandwidth-usage-with-tomato/) is one of the easier, more capably firmwares that has bandwidth tools built-in.  pfSense [https://doc.pfsense.org/index.php/Traffic_Shaping_Guide](https://doc.pfsense.org/index.php/Traffic_Shaping_Guide) is another.

So - do you have a router and what brand/model is it?
If not, which OS does the computer that connects to the internet run?  Would be good to see the routing table to ensure you have the correct machine (i.e. so we don't waste time on the wrong machine).

---

### Post by ramakanta on 2014-08-29
> **TheFu said:**
> Only if all the traffic goes through a device can it report what traffic is happening.  A leaf PC cannot know about traffic from others on the network.

Well, that isn't completely true.  If you have a router that is making the connection to the ISP, then that device, with some firmware, can report traffic using SMNP, to another system for analysis.  I hope that makes sense.  Often, it is easier to just use firmware on a router to see the traffic - tomato [http://www.howtogeek.com/74881/how-to-monitor-and-log-your-bandwidth-usage-with-tomato/](http://www.howtogeek.com/74881/how-to-monitor-and-log-your-bandwidth-usage-with-tomato/) is one of the easier, more capably firmwares that has bandwidth tools built-in.  pfSense [https://doc.pfsense.org/index.php/Traffic_Shaping_Guide](https://doc.pfsense.org/index.php/Traffic_Shaping_Guide) is another.

So - do you have a router and what brand/model is it?
If not, which OS does the computer that connects to the internet run?  Would be good to see the routing table to ensure you have the correct machine (i.e. so we don't waste time on the wrong machine).


please find attached file for whole systems 

[[img]http://s28.postimg.org/jjfusbtbt/Untitled.jpg[/img]](http://postimg.org/image/jjfusbtbt/)

---

### Post by TheFu on 2014-08-29
Well - the only part of the system that sees all the traffic is the modem. That is the only device which can possibly know what bandwidth all the machines are using. Is it just a modem or also a router? Can you replace the firmware with something useful that can report the data you seek?

---

### Post by ramakanta on 2014-08-30
It is **Siemens SL2_141 **

---

