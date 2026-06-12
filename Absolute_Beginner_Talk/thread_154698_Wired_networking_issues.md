---
title: "Wired networking issues"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by cheftek on 2006-04-03
I am having internet access problems. I recently installed ubuntu on a 2800 sempron. This computer has wired internet access thru a dlink router (DI-614+).From what I am able to see it has internet access. I am able to ping sites such as dlink but when I try to use firefox browser every site I go to it does not access. It times out. The the router has assigned it a ip address but the mac address is showing FF-FF-FF-FF-FF-FF and has now host name listed. If there is anyone that can walk me thru how to get access please contact me.

---

### Post by dcstar on 2006-04-03
[QUOTE=cheftek]I am having internet access problems. I recently installed ubuntu on a 2800 sempron. This computer has wired internet access thru a dlink router (DI-614+).From what I am able to see it has internet access. I am able to ping sites such as dlink but when I try to use firefox browser every site I go to it does not access. It times out. The the router has assigned it a ip address but the mac address is showing FF-FF-FF-FF-FF-FF and has now host name listed. If there is anyone that can walk me thru how to get access please contact me.[/QUOTE]
Do a forum search for "disable IPv6" and see if those solutions help.

---

### Post by cheftek on 2006-04-06
Thanks dcstar but I still have no internet access I disabled the ipv6 thru firefox but nothing has change. It still times out and I am able to ping sites thru network. I still need suggestions

---

### Post by ubuntuuser on 2006-04-06
Post the output of the following commands.
```
ifconfig
route
tracepath www.google.com
```When you say you are able to ping dlink, do you ping your router or [www.dlink.com?](www.dlink.com?)
Are you able to log onto your router?

---

