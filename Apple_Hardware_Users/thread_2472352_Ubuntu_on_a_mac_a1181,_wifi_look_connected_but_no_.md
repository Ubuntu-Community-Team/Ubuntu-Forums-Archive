---
title: "Ubuntu on a mac a1181, wifi look connected but no internet or IP"
date: 2022-02-24
forum: Apple Hardware Users
---

### Post by malmago on 2022-02-24
Hi guys, I recently tried to bring an old mac a1181 back to life with linux, everything looks good, but I discovered that the wifi although it said to be connected had no internet.


The wifi board model is BCM4321, I tried several drivers and several methods that I saw on the internet but none of them solved my problem.

Can you guys help me fix my problem?


Thanks.

<iframe src="https://pastebin.com/embed_iframe/y33XAcdm" style="border:none;width:100%"></iframe>

---

### Post by gsahli on 2022-02-26
Have you checked/Can you show us the "Connection Information" and the Edit connections IPV4 settings?

---

### Post by malmago on 2022-02-27
Hi, i try with this commands with only the wifi connected: 

i tried ***ip r*** too but don't show any data.


> ***systemd-resolve --status | grep Current***
      Current Scopes: none
      Current Scopes: none

> ***ip a***
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens5: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 00:1f:f3:d5:76:92 brd ff:ff:ff:ff:ff:ff
    altname enp3s0
3: wls4: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:1f:5b:bf:c8:ee brd ff:ff:ff:ff:ff:ff
    altname wlp2s0
    inet6 fe80::52e:c73e:50ee:24f8/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


This is the actual state of the IPV4 setting for the wifi:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290103&stc=1[/IMG]



I hope this works.

---

