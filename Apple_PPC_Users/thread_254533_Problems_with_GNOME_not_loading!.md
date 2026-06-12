---
title: "Problems with GNOME not loading!"
date: 2006-09-10
forum: Apple PPC Users
---

### Post by nits_555 on 2006-09-10
Hi All,

I installed ltsp from the [www.ltsp.org](www.ltsp.org) site (all packages). Then I went on to activate eth0 (ethernet port) on my laptop. ltsp could not configure my DHCP as the dhcpd package was absent. So I installed the dhcpd package. After this I tried using "ltspconfig" to reconfigure DHCP and it created a file dhcpd.conf

I rebooted ubuntu and since then, it only boots in "command prompt" mode (nitin@ubuntu). I even tried the recovery mode and it still boots in "command prompt" (root@ubuntu).

I am wondering if there is anyway to get ubuntu to start in GUI-mode. I have no clue what could have gone wrong. Any ideas on how to debug this problem will really be appreciated.

Thanking you in advance,
Nitin.

---

### Post by Torrance on 2006-09-10
As a first test, you could log in and try typing "startx" to see if Gnome loads manually. If it does, then it's simply a matter of fixing the startup script so that it loads Gnome automatically.

---

