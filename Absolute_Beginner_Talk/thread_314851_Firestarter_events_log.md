---
title: "Firestarter events log"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by jamere on 2006-12-08
Hi,
Absolute newb here. 
Noticed a "phone out" event that appears every few minutes going to "fiordland.ubuntu.com". It is being blocked by the firewall.
UDP protocol, NTP service. IP address is 82.211.81.145, port 123

anyone know what this is or am i just being paranoid?

Thanks for any info.

---

### Post by Sef on 2006-12-08
It's owned by Ubuntu, so I would not worry about it.

---

### Post by Wim Sturkenboom on 2006-12-08
Which version of Ubuntu? I know that Warty wanted to sync time with a timeserver at startup.
Haven't seen it in Dapper.

---

### Post by jamere on 2006-12-08
Thanks for the replies Sef and Wim!

Wim: using Dapper. You may have hit on it. I did have my clock set to sync with time servers, but specified two servers in Texas (Central Time). I guess there could be a default Ubuntu server that was being checked as well as the 2 Texas servers. If the system was checking all three periodically, that would account for the numerous phone outs being blocked in the firewall log. Hasn't happened since I removed synchronization. When I click on "sync now" button there's no event created on firewall log, so not sure about that, unless firewall knows to let time sync pass through.

Sef: You're probably right, just my paranoia about anything going out without my knowledge! Too many years with M$ I guess.

Thanks again folks!

---

