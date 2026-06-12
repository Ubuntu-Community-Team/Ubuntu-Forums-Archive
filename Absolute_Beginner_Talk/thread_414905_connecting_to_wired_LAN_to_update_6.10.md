---
title: "connecting to wired LAN to update 6.10"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-04-20
Hello,

I have ubuntu 6.10 and I want to update it to 7.04. For that I need broadband internet connection. I received from my office a internet permission to connect to the internet cable. There are cetaing configuration parameters, like IP, gateway, subnet mask. I already entered them in System>Administration>network settings>wired connections. But there are two other parameters which I don't know where to enter: dns1 and dns2. it seems that there's no option for dns1&2 in Ubuntu 6.10. ?? :( what can I do now?

---

### Post by Pobega on 2007-04-20
Try either using network-manager-gnome or editing /etc/network/interfaces by hand (The latter is generally the better way to do it).

If you edit /etc/network/interfaces you can restart networking with a quick 

```
/etc/init.d/networking restart
```

That is, so long as it's already running. If networking isn't running replace "restart" with "start"

---

### Post by O-pos on 2007-04-20
Thank you for your help. can you explain in more primitive language how these procedures can be done? I mean editing /etc/network/interfaces by hand and "restarting networking wit ha quick"?

---

