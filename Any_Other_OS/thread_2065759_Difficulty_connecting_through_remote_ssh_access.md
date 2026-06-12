---
title: "Difficulty connecting through remote ssh access"
date: 2012-10-02
forum: Any Other OS
---

### Post by AJbloomie on 2012-10-02
I am a new linux user and I currently have Linux Mint installed (Maya). I haven't gotten any responses on this issue at their forums, and I think it's generic enough to try here.

I have successfully installed open-ssh. I am having difficulty connecting remotely to the server. I am currently running stock sshd_config. Here are the steps I've tried with their results:

1) Port forwarding through my 2 chained routers: I have two services running that require forwarding. One is a torrent client running on a Windows box, the other is ssh on my Linux Mint laptop. I can see the open torrent client port, but not ssh (port 22) with a remote port scan. Just to eliminate possible router issues, I set both routers to DMZ mode, and still could not see the ssh port or connect from remote location. Torrent client port on the Windows box still registers as open.

2) ssh connections from behind my routers, both from the Windows box using PuTTY, terminal in a Mac laptop, and a third linux machine are all successful.

3) I've checked my iptables, and every policy seems to be set to ACCEPT. See below. I've also posted my route -n results if that's heplful.

Given that DMZ enabled still prevents remote connections to ssh, it suggests to me that there is a problem on the ssh service side. Any help would be greatly appreciated!

iptables -L:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
```

---

### Post by Perfect Storm on 2012-10-03
Moved to Other OS/Distro.

---

