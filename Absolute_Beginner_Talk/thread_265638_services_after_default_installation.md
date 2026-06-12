---
title: "services after default installation"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Cruz on 2006-09-26
Yo,

so after a default isntallation all services in System -> Administration -> Services are enabled. 

Do I really need 3 types of cron (anacron, atd, cron)? Or can I disable the first two and use good ol' cron only?

Do I really need both syslog facilities? Or can I disable klogd and use sysklog only?

Is the printer service cupsys needed if I have cupy running elsewhere on the network and I want to send the print jobs there?


After disabling all "suspicious" services that I mentioned above my netstat -l output is:

Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:49706         *:*                     LISTEN
tcp        0      0 *:5900                  *:*                     LISTEN
tcp        0      0 localhost:43248         *:*                     LISTEN
udp        0      0 *:bootpc                *:*

What are these two high ports 43... and 49... for? Or how can I find out? What's the 5900 port for and what is this bootpc udp thing?

In the Local Address column, does localhost:port mean that only a socket from localhost could connect to this listening port? And *:port a socket from any host accordingly?

So many questions....

Cruz

---

### Post by Gotterdammerung on 2006-09-26
You may disable anacron and atd. atd however is not like cron, it schedules tasks differently. read man at for more info.

You should choose only one system logger. sysklog is enough.

I guess cupsys is only needed on the printer server. Don't know for sure.

Try *netstat -atnp | grep -i listen* to check who's listening in each port.

If your localhost has a valid IP, i.e., a IP different from 192.*.*.* and from 10.*.*.*, it means that anybody over the www can reach these ports.

---

### Post by Gotterdammerung on 2006-09-27
> **Gotterdammerung said:**
> You may disable anacron and atd. atd however is not like cron, it schedules tasks differently. read man at for more info.

You should choose only one system logger. sysklog is enough.

I guess cupsys is only needed on the printer server. Don't know for sure.

Try *netstat -atnp | grep -i listen* to check who's listening in each port.

If your localhost has a valid IP, i.e., a IP different from 192.*.*.* and from 10.*.*.*, it means that anybody over the www can reach these ports.

I've studied a little bit more about your problem. [COLOR="Blue"]sysklog [/COLOR]is the system logger, and [COLOR="Blue"]klog[/COLOR] is the kernel logger. So, I think it would be wise to load them both.

---

