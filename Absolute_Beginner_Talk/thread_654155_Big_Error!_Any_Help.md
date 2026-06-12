---
title: "Big Error! Any Help??"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by sunami900 on 2007-12-30
It's my headline when opening firefox.. IT"S HUGE!
i let my sis on my pc for like 5m and pow it's wrecked.. any solutions will be appreciated!

<br><br>
[[IMG]http://img168.imageshack.us/img168/4292/problemtg2.th.png[/IMG]](http://img168.imageshack.us/my.php?image=problemtg2.png)

---

### Post by taurus on 2007-12-30
Check your network connection?  It could be down from the look at your applets.

---

### Post by overdrank on 2007-12-30
> **taurus said:**
> Check your network connection?  It could be down from the look at your applets.
Edit that is the force quit

---

### Post by HereInOz on 2007-12-30
First up, reboot your router/modem and any other networking devices - wireless APs or routers, ethernet switches, all those devices.  Also after rebooting all these, reboot the computer.

If that doesn't work, open a terminal and type in:

less /etc/resolv.conf

This will tell you the IP address of your nameserver (which may also be your router/modem.

Now see if you can ping the nameserver ip address by typing in:

ping     followed by a space and then the nameserver address.  e.g. ping 192.168.5.254 or whatever the address is.

If you do not get a response from this, then your network connectivity has failed.  If you do get a response from this, it probably means that your local area network is OK, and the problem lies either with the DNS relay properties of your router/modem, or your ISP is having an issue at the moment.

By the look of the network manager icon, your local area network is non-functional at the time the screen dump was taken.

See how you go.

---

