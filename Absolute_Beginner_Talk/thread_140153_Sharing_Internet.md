---
title: "Sharing Internet"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by komyg on 2006-03-05
I was trying to share my internet connection using a computer with Ubuntu 5.10 as a server and another computer with Windows XP as a client. And then I ran into an article in the Ubuntu WIKI that told me the use this commands:

$iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
$echo 1 > /proc/sys/net/ipv4/ip_forward

But I couldn't get the internet connection working, perhaps is because the Ubunutu computer cannot connect with the Windows computer via LAN (The other way around works just fine with Samba).
So I gave up, but when I went back to the original configuration (Windows is server and Linux is client), I couldn't get the internet on the Linux computer working.

Thanks,
Komyg

---

