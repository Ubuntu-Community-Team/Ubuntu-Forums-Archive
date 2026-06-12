---
title: "ISP ip address in DNS always reset back to 192.169.1.1"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by liangtp on 2006-07-30
Hi,

i had to set the DNS to my ISP ip address 202.188.0.133.

however after about 10 minutes of surfing, the DNS revert back to 192.168.1.1. As a result, i get very very slow connection.

how to make the change in DSN to my ISP ip address permanent?

Thanks

---

### Post by ProjectGod on 2006-07-30
i'm assuming you have DHCP enabled on your router and your ubuntu computer is acting as the DHCP client. on your router you need to make sure that the leases it gives out has the ISP's DNS server IP **in addition** to allocating its IP own as DNS server.

you can try that or set the DHCP leases to be given out for a longer period. say 8 hours or even a day.

---

### Post by MaximB on 2006-07-30
I have answered this question several times
search the forum
make the file .conf read only **AFTER** you have changed the networking properties.

---

