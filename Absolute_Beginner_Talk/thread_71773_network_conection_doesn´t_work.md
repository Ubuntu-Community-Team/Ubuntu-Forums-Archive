---
title: "network conection doesn´t work"
date: 2005-10-04
forum: Absolute Beginner Talk
---

### Post by Marw on 2005-10-04
I have breezer. at first everything worked normaly but now the network don`t work (under windows works normaly). It seems to be connected but internet doesn't work neither ping. I thought this can be because of IP adress setting but it is ok (IP adress get from dhcp) where else can be a problem?

---

### Post by KingBahamut on 2005-10-04
Did you change any of your network settings? What are your DNS Settings? What are your Hosts settings?

---

### Post by Marw on 2005-10-04
it is possible that i changed something :( but don't know what.
dns is ok (and even ping doesn't work)  host settings? what have to be there?

---

### Post by KingBahamut on 2005-10-04
can you out put the contents of /etc/resolv.conf and /etc/hosts, also output the results of an ifconfig......

---

### Post by Marw on 2005-10-04
sorry i have to reboot twice :)

resolve.conf:
 nameserver 217.11.224.1
 nameserver 217.11.224.2
 domain praha5.net
 search praha5.net

hosts:
 127.0.0.1 localhost.localdomain localhost Marwubuntu

 # The following lines are desirable for IPv6 capable hosts
 ::1 ip6-localhost ip6-loopback
 fe00::0 ip6-localnet
 ff00::0 ip6-mcastprefix
 ff02::1 ip6-allnodes
 ff02::2 ip6-allrouters
 ff02::3 ip6-allhosts

---

### Post by KingBahamut on 2005-10-04
Doesnt look like your getting a valid IP address. 

Nor does it look like you have a proper host for yourself in hosts.

---

