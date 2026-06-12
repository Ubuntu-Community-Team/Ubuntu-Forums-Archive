---
title: "networking problems.  Maybe a dhclient prob?"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by gomezj00 on 2006-06-10
Hi,

I'm using Drake and I connect wirelessly to my router by doing the following:

>iwconfig eth1 essid myessid (no key)
>dhclient

I can then connect most of the time but after a while, perhaps when my ip address lease expires, I lose my network connection.  Anyone have any ideas as to why dhclient inconsistently obtains an address and then drops my connection.  The network manager I'm using never works.  It always says "Activating interface" but it never works despite being able to see all the woreless networks around me.  Anyway any help anyone can provide will be greatly appreciated.  This forum and the people on it are awesome.

---

### Post by deja2004 on 2006-06-10
Just a suggestion (since I saw you haven't had a reply yet). Try installing wifi-radar. I use it on my laptop and it connects to AP w/ ease. Type this:
```
sudo apt-get install wifi-radar
```
Best of luck.

---

### Post by jvictor on 2006-06-10
Conxn droppage for me (WIRED) to an adsl router was because of IPV6 enabled and not using the ISPs DNS in my /etc/resolve.conf file

edit
/etc/resolv.conf file

---

### Post by gomezj00 on 2006-06-19
Thanks for the help you guys.  The wifiradar worked like a charm!=D>

---

