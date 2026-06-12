---
title: "I can't ping any computer in my lan and computers can't ping my ubuntu\"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by chuchulo on 2007-09-27
I am using wireless connection. I can connect the router on 192.168.1.1 other computers also.But I can't ping mac on 192.168.1.3, nor mac  can't ping ubuntu 192.168.1.7. The mac on 198.168.1.2 can ping mac on 192.168.1.3 and vice versa.

Please help me...

---

### Post by llamakc on 2007-09-27
Are you using Gnome? Network-Manager? Have you chosen the correct Wireless network? Do you have any manually-added entries in /etc/hosts?

---

### Post by chuchulo on 2007-09-27
I am using kde and network manager too. I have added to /etc/hosts the ip adress of mac, that I can't ping. I added "192.168.1.3 juchachaa". "juchachaa" is the name of mac.

---

### Post by chuchulo on 2007-09-27
I am using the correct wireless network, because I can ping the router

---

### Post by llamakc on 2007-09-27
What is the output (from Konsole or Terminal) of:

route -n

---

### Post by chuchulo on 2007-09-27
> **llamakc said:**
> What is the output (from Konsole or Terminal) of:

route -n
Kernel IP routing table
Destination          Gateway         Genmask             Flags      Metric     Ref     Use   Iface
192.168.1.0         0.0.0.0            255.255.255.0      U            0            0          0        eth1
169.254.0.0         0.0.0.0            255.255.0.0          U            1000      0          0        eth1
0.0.0.0                 192.168.1.1    0.0.0.0                  UG          0           0          0        eth1

---

### Post by llamakc on 2007-09-28
Is there a typo in your /etc/hosts? Let's see that please.

---

### Post by chuchulo on 2007-09-28
> **llamakc said:**
> Is there a typo in your /etc/hosts? Let's see that please.
String "typo" isn't in /etc/hosts. I don't know what is "typo"

---

### Post by llamakc on 2007-09-28
> **chuchulo said:**
> String "typo" isn't in /etc/hosts. I don't know what is "typo"

An error or mistake. May we see the contents of your /etc/hosts file?

"typo" in my response refers to a typographical error.

---

### Post by chuchulo on 2007-09-28
/etc/hosts looks:

127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by llamakc on 2007-09-28
What sort of router are you using? Is pinging them required?

---

### Post by chuchulo on 2007-09-28
> **llamakc said:**
> What sort of router are you using? Is pinging them required?
108 Mbs Wireless Firewall Router WGT624 v3. I need share  files on lan, which consists of three macs and ubuntu. The macs are working on lan, but my Ubuntu isn't. Pinging from ubuntu to router is only working. The other computers I can't ping from Ubuntu

---

### Post by chuchulo on 2007-09-28
can anybody help me?

---

### Post by llamakc on 2007-09-28
You're certain that there is no intervening OTHER wireless network near you, correct? You're not in an apartment complex? You're not using the default name for your wireless network (that the router originally set)?

Does your wireless router offer any wired connections? If it does, and you plug directly INTO the router, are the results different? You'd need to release the wireless IP and secure a new dhcp lease for the wired ethernet device.

---

### Post by chuchulo on 2007-09-29
> **llamakc said:**
> You're certain that there is no intervening OTHER wireless network near you, correct? You're not in an apartment complex? You're not using the default name for your wireless network (that the router originally set)?
Yes, there are two other networks. Yes I am in apartment complex.Yes, I am using my own name for our wireless network.

> **llamakc said:**
> Does your wireless router offer any wired connections? If it does, and you plug directly INTO the router, are the results different? You'd need to release the wireless IP and secure a new dhcp lease for the wired ethernet device.
Thanks, I' ve tried to plug directly to the router, and the lan was working, sharing files was working, too.

Why the pinging is not working when i use the wireless connection?

---

### Post by chuchulo on 2007-09-29
sorry i've done mistake. this post is not here!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Het Irv on 2007-09-29
Is there a possibility that this could be a hardware Firewall on the router itself any that is stopping the ping from going thru?

Edit:  Wait..what...where am I there is not a thread here?  I thought there was...

---

### Post by chuchulo on 2007-10-01
> **Het Irv said:**
> Is there a possibility that this could be a hardware Firewall on the router itself any that is stopping the ping from going thru?

Edit:  Wait..what...where am I there is not a thread here?  I thought there was...

no, on the router is no Firewall.

---

### Post by chuchulo on 2007-10-03
Can anybody help me? I can't still help myself....

---

