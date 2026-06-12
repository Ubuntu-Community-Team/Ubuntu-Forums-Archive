---
title: "Slowness on startup"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2008-04-03
generally from grub it take around 30-40 sec to load my login screen.  My last start up and once before it took at least 3 mins.  anyone ever have this happen?  anyone know what might cause this?

---

### Post by brian_p on 2008-04-03
> **RyanZec said:**
> generally from grub it take around 30-40 sec to load my login screen.  My last start up and once before it took at least 3 mins.  anyone ever have this happen?  anyone know what might cause this?

I have this intermittently with a wireless laptop and keep meaning to track down the  exact cause. I can see the messages as booting takes place and it halts for a while when internet services are being acquired. It could be DHCP on my router is acting up. Or the MTA is taking its doing lookups. Or my ISP's nameservers are not available. Or something I haven't thought of!

---

### Post by taavikko on 2008-04-03
The problem very well might be in usplash.

You can remove it using program called startup-manager (it's in the repos)
You can also check it using bootchart (in the repos also)
it makes pretty litlle picture of start process in /var/log/bootchart/ folder

---

