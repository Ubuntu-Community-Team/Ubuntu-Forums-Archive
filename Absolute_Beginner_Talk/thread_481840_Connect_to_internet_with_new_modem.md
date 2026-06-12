---
title: "Connect to internet with new modem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by heather_s on 2007-06-22
Hi; I've installed Feisty and the net connection used to work fine. Now I have replaced my Netgear DG834G with a Billion 7404-VGPM and the internet connection no longer works. I went to ifconfig and both eth0 and eth1 are set to DHCP and there is nothing in DNS, Hosts etc. I can't ping the router either. Can anyone help this poor n00b? Thanks!

---

### Post by octoberdan on 2007-06-23
Open a console and try
```

sudo dhclient

```

also confirm that NetworkManager is running
```

pidof NetworkManager

```
If you get its proccessor ID back, it's running

Also try restarting, of course

---

### Post by heather_s on 2007-06-23
Thanks, I tried sudo and it said no working leases in persistent database - sleeping
and the pidof came back with a number 4572.
Should I maybe just reinstall Feisty?

---

