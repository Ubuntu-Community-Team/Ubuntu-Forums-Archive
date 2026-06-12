---
title: "gtk install mistake, no gnome, need internet please help"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by silicon_chipper on 2008-01-01
Hi posted about this before not sure, if this is ok, but I tried to install gtk manually. I installed the glib dependency, when I ran configure for the atk dependency i got an error saying the version of glib in pkg_config was one version, but a different version was found, it advised me to remove the old version. Anyways so I just decided to try apt-get install libgtk2.0-common libgtk2.0-dev. I can't boot into gnome now, ctrl-alt-f1 or ctrl-alt-f4 still get me in.
I saw this in a post about a similar problem:
```

apt-get update
apt-get install -f
apt-get install ubuntu-desktop

```
I need internet access to do this, but can someone tell me how to get online from the command line, ifconfig returns the below
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22992 (22.4 KB)  TX bytes:22992 (22.4 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.111.128  Bcast:192.168.111.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.4.1  Bcast:172.16.4.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

So I tried dhclient vmnet1, it seemed to work it and printed some stuff to the terminal the last line said I was bound to an ip address. I ran apt-get update, it tries to connect to archive.canonical.com but eventually just prints:

error could not resolve archive.unbuntu.com

It tries to connect to a bunch of other stuff but just prints similar errors. 
Ok so I rebooted and tried dhclient vmnet8 and the exact same stuff happened.

I know this is bad, but just wonder if it can be fixed without a reinstall. Thanks you guys are great by the way.

silicon

---

### Post by silicon_chipper on 2008-01-01
hello?

---

