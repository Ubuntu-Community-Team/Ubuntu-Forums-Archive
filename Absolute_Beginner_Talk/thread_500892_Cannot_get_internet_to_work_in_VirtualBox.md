---
title: "Cannot get internet to work in VirtualBox"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by cwk on 2007-07-14
I set up an XP virtual machine using this guide: [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359), I can't for the life of me get any sort of connection.

This is what I have in rc.local

```
tunctl -t tap0 -u cene
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig ra1 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 ra1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 255.255.255.0 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 76.214.211.137 dev tap0
 arp -Ds 76.214.211.137 ra1 pub

exit 0
```

Any ideas?

---

### Post by starsky on 2007-07-14
hi there :)

as the howto says to use any ip for your virtual box "<vbox_ip>", try using different ip like 10.1.1.20 OR 192.168.1.122 (because 255.255.255.0 may be your broadcast address). Just make sure it isn't used by any computer in your network.


also make sure 76.214.211.137 is the IP that your ubuntu computer (host computer) is using.

HTH

post back :)

---

### Post by cwk on 2007-07-23
I tried 10.1.1.30 as my <vbox_ip> (pinged it, nothing came back). And 76.214.211.137 is just what I get from one of those web 'what's my ip?' sites. Rebooted, and still no connection. 

I've never really had to do much with IPs, so I may be missing something obvious here.

---

### Post by cwk on 2007-07-29
Bump. still looking for some help here.

---

### Post by AndEat on 2007-07-30
I'm trying to get that working, too

running a ubuntu server on k/ubuntu fiesty

 for some reason I thought that script went on the local machine and not the virtual


........also my bridge is dishing out ipv6 addresses which isn't really an issue but i wouldn't know the first thing about selecting a static ip there

---

### Post by asmoore82 on 2007-07-30
I just got VBox up and running on Friday without a howto ...
I'm using the default NAT option for networking with no add'l config needed.
will this help you or do you really need xp to fully join your local network?

P.S. VirtualBox OSE here.

---

