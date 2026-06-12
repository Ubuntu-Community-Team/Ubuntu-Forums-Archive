---
title: "Backtrack etc/dhcp3/dhcpd.confg help !"
date: 2013-10-07
forum: Any Other OS
---

### Post by krishna6 on 2013-10-07
Hello respected members ,


                              I had been trying to set up a software accesspoint on Backtrack 5 with a usb wifi adapter , bringing it on Monitor mode and then specifying the dhcpd.confg file to run dhcp server . Problem I encounter is ,


Everything goes well to this point
> airmon-ng stop wlan0

airmon-ng start wlan0

// dhcpd.confg file content below
ddns-update-style ad-hoc;
default-lease-time 600;
max-lease-time 7200;
authoritative;
subnet 192.168.2.128 netmask 255.255.255.128 {
option subnet-mask 255.255.255.128;
option broadcast-address 192.168.2.255;
option routers 192.168.2.129;
option domain-name-servers 192.168.2.1;
range 192.168.2.130 192.168.2.140;
}
==============================================

airbase-ng -e Wifitest -c 11 -v wlan0 &

ifconfig at0 up
ifconfig at0 192.168.2.129 netmask 255.255.255.128
route add -net 192.168.2.128 netmask 255.255.255.128 gw 192.168.2.129


mkdir -p /var/run/dhcpd && chown dhcpd:dhcpd /var/run/dhcpd
echo > '/var/lib/dhcp3/dhcpd.leases'
dhcpd3 -d -f -cf /etc/dhcp3/dhcpd.conf -pf /var/run/dhcpd/dhcpd.pid at0  <---- [color=#000080]Problem line[/color]



dhcpd3 -d -f -cf /etc/root/dhcp3/dhcpd.conf -pf /var/run/dhcpd/dhcpd.pid at0   --> i get error that cant access /etc/dhcp3/dhcpd.conf  - permission denied , i looked up on google , google hinted it is something related to apparmor , but when i looked to see if apparmor is running , Apparmor isnt installed on the backtrack 5 i use , what could i try to resolve this ?


I am new to linux and backtrack , are there any ways to setup dhcp for my 
accespoint so that my clients would have an ip address .

---

### Post by howefield on 2013-10-07
Thread moved to a more appropriate forum, "*Other OS/Distro Support*"

---

