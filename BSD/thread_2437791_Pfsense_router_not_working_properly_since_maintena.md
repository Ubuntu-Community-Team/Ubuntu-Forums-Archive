---
title: "Pfsense router not working properly since maintenance ISP."
date: 2020-02-29
forum: BSD
---

### Post by cheese66 on 2020-02-29
Dear readers,

I have a pfsense router, a Netgate SG3100, which has been working perfect for more than a year now.
Two weeks ago my ISP has done a maintenance here in the neighbourhood, and ever since I have a disfunctioning router every two days or so.

My internet then does not work, and my 192.168.1.1 web panel gives me a "bad gateway" error page.
I have to restart my router to fix it.

Anyone here who knows what I should check, or someone who I can share a log file with?
I you want a log file please ask here, so I can send one with a PM.

Thanks,
Martijn.

---

### Post by TheFu on 2020-03-01
I  would monitor the connection to the internet 24/7 and see whether the bad gateway happens at specific times.  With those logs, you can contact the ISP for help.  Concrete logs of failures on their side usually gets someone to pay attention.

But don't assume it is their fault.  I&#8217;ve been embarrassed by the ISP pointing out when my "been working 5 yrs" setup had failed.

i have no interest in seeing logs.  Could you just renew the DHCP lease?

---

### Post by cheese66 on 2020-03-17
Thanks TheFu!
And sorry for the late response!

Unfortunately my access-point broke, and I cannot try this because of that.
New switch and access-point first! Then we will see...

---

