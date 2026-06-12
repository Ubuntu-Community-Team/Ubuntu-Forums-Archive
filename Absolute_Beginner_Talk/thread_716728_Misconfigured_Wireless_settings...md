---
title: "Misconfigured Wireless settings.."
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by tompug on 2008-03-06
I was having problems with a long boot time, searched the logs and found something was waiting 60 seconds for a DNS connection/timeout. I seached the forum for 'DNS' and 'long boot time' and found this aparent fix. 


> sudo update-rc.d -f networking remove
sudo update-rc.d networking defaults 99

However I was wrong in diagnosing the problem. Now my wireless connection is down, can any tell me how to restore defualts?

---

### Post by wednesday allfather on 2008-03-06
Try reinstalling network-manager from your installation CD.  That should restore your defaults.

---

### Post by tompug on 2008-03-07
that didn't work its still down.

---

### Post by tompug on 2008-03-07
I'm totally stumped by this, I can reach my wireless router, which is also my modem/gateway. i just can't get  to an address outside my lan. 
I assume this is a DNS prolem.

can anyone troubleshoot this problem, It's driving me mad! I'll provide any info you need.

---

