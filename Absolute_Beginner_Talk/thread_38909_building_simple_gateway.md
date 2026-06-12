---
title: "building simple gateway"
date: 2005-06-02
forum: Absolute Beginner Talk
---

### Post by yoseph2001 on 2005-06-02
hi, all..

i've just using Kubuntu, and well, this is very nice distro  O:) 

well, i've decided to change my gateway computer OS to Ubuntu. does anyone know how to install this gateway? i think it'll be text mode (low power pc), but i don't know very much about the linux command in the text mode.

so, i need some, manual :
- what packet should i install ?
- how to configure the network ? the other pc connect to internet through this gateway, but i don't know where to set the DNS etc etc in the text-mode.
- what simple text mode firewall to use & how to configure it ?

thank you very much for the help  ;-)

---

### Post by thrift on 2005-06-02
Well, what you probably want to do is setup iptables to configure NAT routing from the interior network to the internet.

To do that, your going to need to make sure ip forwarding is enabled on the box.

echo 1 > /proc/sys/net/ipv4/ip_forward (your going to want that to happen on startup)

Then you can simply use iptables to configure how packets should be routed.  Looking for iptables and masquerade in google should find you a bunch of information on exactly how to to do that.

If you want to run your own DNS forwarder rather than using your ISP provided DNS server, you can install bind and the set it up to forward to another DNS.

Does anyone know of any scripts/programs that can guide a user through this setup?  You should probably be able to figure out how to do it manually fine, and it'll certainly help you configure the routing exactly to your liking, but there are probably some scripts to aid you in the process.

---

