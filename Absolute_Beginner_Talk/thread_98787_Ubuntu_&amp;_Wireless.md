---
title: "Ubuntu &amp; Wireless"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Jennings on 2005-12-04
Hi, many thanks to the people who helped me on the last thred getting the internet to work through LAN. 

I am making this thred because i would like a certain tool for linux. In windows you get the search for wireless networks panel and it scans and comes up with the wireless networks found and i was wondering if there is a linux equivilent?

Many thanks, Jennings

N.B.
Whille googling i found "airfart" and it said i needed "linux-wlan-ng prism2_cs" any ideas?

---

### Post by kane77 on 2005-12-04
there is a tool named wifi-radar... I believe it is found in package manager if not let me know

Hope it helps

---

### Post by Lambert on 2005-12-04
In the repositories is

network manager
netapplet

At the top of the forums is a tab "projects". Click there and look at gtkwifi


And lastly, wifi-radar but it's not very highly regarded in posts I've seen.

I believe network manager is the preferred app and might make come with the next ubuntu release.

---

### Post by adduds on 2005-12-04
[QUOTE=Jennings]....it said i needed "linux-wlan-ng prism2_cs" any ideas?[/QUOTE] I have the same problem...

EDIT:

> adduds@ubuntu:~$ airsnort
/sbin/wlanctl-ng eth1 lnxreq_ifstate ifstate=enable > /dev/null
wlanctl-ng: Operation not supported
SIOCSIFFLAGS: Permission denied

that is what it says in term when i press scan in airsnort

or root
> 
root@ubuntu:/home/adduds# airsnort
/sbin/wlanctl-ng eth1 lnxreq_ifstate ifstate=enable > /dev/null
wlanctl-ng: Operation not supported
/sbin/wlanctl-ng eth1 lnxreq_wlansniff enable=true channel=10 keepwepflags=false prismheader=false > /dev/null
wlanctl-ng: Operation not supported
/sbin/wlanctl-ng eth1 lnxreq_wlansniff enable=true channel=11 keepwepflags=false prismheader=false > /dev/null


---

### Post by Mr. Electric Wizard on 2005-12-04
GTKwifi kicks so much ass!
I love that program!
As soon as WPA gets added to the feature set, it's going to be that much better.
Very killer app.

---

