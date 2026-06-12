---
title: "Ubuntu doesn't load some websites"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Forty on 2006-10-29
Hi, I'm an inexperienced Ubuntu user. I have a problem since I switched to Ubuntu 6.10. The problem is that some websites, such as [www.nvidia.com](www.nvidia.com) and [www.sport.es](www.sport.es) don't load at all. I didn't experience this problem with other versions od Ubuntu, and on windows those websites load normally.
I didn't upgrade my prior version of Ubuntu: I formatted and then installed. After that the problem showed up.

I've tried to modify /etc/resolv.conf adding the DNS adresses that my ISP provided, but I haven't achieved anything. What else can I try?


Thanks in advance.

---

### Post by furiousV on 2006-10-29
> **Forty said:**
> Hi, I'm an inexperienced Ubuntu user. I have a problem since I switched to Ubuntu 6.10. The problem is that some websites, such as [www.nvidia.com](www.nvidia.com) and [www.sport.es](www.sport.es) don't load at all. I didn't experience this problem with other versions od Ubuntu, and on windows those websites load normally.
I didn't upgrade my prior version of Ubuntu: I formatted and then installed. After that the problem showed up.

I've tried to modify /etc/resolv.conf adding the DNS adresses that my ISP provided, but I haven't achieved anything. What else can I try?


Thanks in advance.


Start firefox, go to **about:config** by putting it in the address bar. Filter out **ipv6** and set **network.dns.disableIPv6** to **True**

Websites should now load

---

### Post by Forty on 2006-10-29
Hi! Thanks for the answer. I tried it but the sites still don't load. I've tried with firefox and 2 other web browsers as well, and the result is always the same :(

---

