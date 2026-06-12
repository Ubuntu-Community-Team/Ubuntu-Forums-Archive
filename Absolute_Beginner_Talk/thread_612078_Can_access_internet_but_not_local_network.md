---
title: "Can access internet but not local network"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by kaptengu on 2007-11-13
I have some issues with my networking.

It all started after connecting .local domain at work with my wifi connection. I got some message about avahi being disabled because of this .local domain. Except from this message, I was able to browse the web and everything seemed normal.

When I got home again, I couldn't connect at all. The nm-applet was crashing and didn't show up in the notification area. I reinstalled network-manager, and that seemed to fix the problem.

But now it sometimes stop working. The connection seems to work by looking at the nm-applet or running ifconfig. I can't access anything. The only way I know to fix this is to do ifdown eth1 and then ifup eth1, or restart the computer.

After doing this it works again, or at least access to internet. I can never access my local network, such as my router at 192.168.0.1. Also the bridged networking with vmnet seems to be broken.

Someone, please help me.

---

### Post by kaptengu on 2007-11-13
When trying to ping my router at 192.168.0.1 I get this strange reply:
```

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.4 icmp_seq=1 Destination Host Unreachable
From 192.168.0.4 icmp_seq=2 Destination Host Unreachable
From 192.168.0.4 icmp_seq=3 Destination Host Unreachable

```
192.168.0.4 is another laptop on my network. My computer's wifi has 192.168.0.7 (eth1).
When typing route -nv I get:
```

Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.102.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.0.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0       0.0.0.0         255.255.255.0   U     0      0        0 eth1
169.254.0.0       0.0.0.0         255.255.0.0       U  1000   0        0 eth1
0.0.0.0               192.168.0.1   0.0.0.0            UG    0      0        0 eth1
0.0.0.0               192.168.0.1   0.0.0.0            UG    0      0        0 eth0

```

---

### Post by dom on 2007-11-19
hi kaptengu

Basically, I would say, for a start, do not use ".local" as a tld.

As for not being able to ping the router, that looks like another issue. You appear to have a default route going to the same gateway via two different interfaces, which may be confusing things ??

i'm just writing [ another post]("http://ubuntuforums.org/showthread.php?t=617270") about avahi issues I had, and found this in my search for existing posts

---

### Post by steve.horsley on 2007-11-19
I wonder if you have the same IP address on both eht0 and eth1. Can you post the output from **ifconfig**?

---

### Post by kaptengu on 2007-11-19
Hi, thanks for replying.

The problem went away by itself. I guess it was a temporary routing conflict.

I will tell you if I see it again.

---

