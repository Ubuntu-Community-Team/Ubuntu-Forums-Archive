---
title: "Firewall runs with eth0 and not with eth1"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-06-02
Hi,

I use Feisty on a laptop and often switch between eth0 (wired) and eth1 (wireless) connections. The problem is that the firewall is only active on one connection (here eth0) and is not running when I'm using eth1. I've seen this can be changed in Firestarter preferences but it only allow to make the firewall work with one network interface (if I make it work with eth1 then it stops working when I connect back with eth0...). So if I want to stay protected I have to restart Firestarter and change what is the active connection everytime which is a bit strange....

I'd like to configure the firewall so that it is always enabled, no matter what is the active connection. The firewall should work on all connections, including dial-ip if this is possible. How is it possible to achieve this?

Thanks

---

### Post by wormser on 2007-06-02
Do you have Firestarter installed?  Firestarter is a gui manager for your firewall.

```
sudo apt-get install firestarter
```

---

### Post by kilou on 2007-06-02
Yes it is installed but it only allow me to make the firewall active for one interface: in Firestarter's preferences under Network settings, only the selected interface in "Internet connected network device" and "Local network connected device" will be firewalled. Of course I can select eth1 or eth0 but for instance if eth0 is selected in these and I connect with eth1, the firewall is not active! The firewall is only active if the connected interface matches the interface selected in Firestarter, which is a problem!

I check the status of the firewall with **sudo /etc/init.d/firestarter status**

---

### Post by sammydee on 2007-11-28
I've also been having this problem.

Apparently this functionality will be enabled in firestarter 1.1. Not sure when that release is coming though...

Sam

---

