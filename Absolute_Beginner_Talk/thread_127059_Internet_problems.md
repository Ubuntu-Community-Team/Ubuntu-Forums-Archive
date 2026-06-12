---
title: "Internet problems"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by sod on 2006-02-08
I have just installed ubuntu but the internet aint working. have a dsl 604 router with dhcp, getting right ip adress to the pc(192.168.1.2) , can ping both router. external ip numbers and www adresses. but no internet. What to do?:-k

---

### Post by kaamos on 2006-02-08
You can ping www addresses? What happens when you open up firefox and try to go to [http://66.249.93.99/](http://66.249.93.99/) ?

If that works, you probably have the wrong dns servers listed in network settings. They are in System->Administration->Network settings

---

### Post by sod on 2006-02-08
i see google!

---

### Post by kaamos on 2006-02-08
Wait a sec, if you can ping websites with an address (and there is no big delay), your dns should be ok.

Open firefox, type about:config in the address bar. Type ipv6 in the filter. Change **network.dns.disableIPv6** to **true**

Hope this helps.

---

### Post by sod on 2006-02-08
ok ethO is configuration dhcp what do i have to set?

---

### Post by sod on 2006-02-08
it works! yr the best! thanks!

---

