---
title: "I keep getting disconnected"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by unfun on 2006-08-13
for some reason, my internet completely disconnects after 10-15 minutes of being logged in and the only way to come back is typing sudo /etc/init.d/networking restart. firefox, etc. shows that its not connected but the connection properties window always shows the signal strength with at least 95% (im on a wireless connection). I've never had this problem with windows on this computer so the router and signal is fine so it must be linux

---

### Post by camRW on 2006-08-13
I had this same problem.  Disabling IPv6 worked for me:
[http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)

---

### Post by unfun on 2006-08-14
I'm a real noob I don't understand how to follow the guide, I want it step for step with EVERYTHING discribe :=)

Thanks though

---

### Post by dmizer on 2006-08-14
what part of the guide are you having problems with?

actually, i see your problem now.  try this instead: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by drtvasudevan on 2006-08-14
> **unfun said:**
> I'm a real noob I don't understand how to follow the guide, I want it step for step with EVERYTHING discribe :=)

Thanks though
in the firefox address bar type about:config 
and in the filter bar type ipv6 
and change from false to true= just double click it 
shutdown firefox
restart firefox.

---

