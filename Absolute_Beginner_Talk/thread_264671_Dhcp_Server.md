---
title: "Dhcp Server"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by patz on 2006-09-25
this is my first time to use ubuntu 6.06.. I had 3 computers at home and i want to setup DHCP on my machine  and share the connection on my 2 spare computer. please help how to do it.. thanks in advance:D

---

### Post by dmizer on 2006-09-25
you'll need more than just a dhcp server.  you'll need to set up nat (network address translation) as well.

this is not the most easy thing to do in windows or in linux, so expect to spend some time on it to figure everything out.  i suggest starting here: [http://easylinux.info/wiki/Ubuntu_dapper#DHCP_Server](http://easylinux.info/wiki/Ubuntu_dapper#DHCP_Server)

---

### Post by Marsolin on 2006-09-25
Howtoforge just posted a [How To Set Up A DHCP Server For Your LAN]("http://www.howtoforge.com/dhcp_server_linux_debian_sarge") article. It might help you.

---

### Post by patz on 2006-09-25
> **dmizer said:**
> you'll need more than just a dhcp server.  you'll need to set up nat (network address translation) as well.

this is not the most easy thing to do in windows or in linux, so expect to spend some time on it to figure everything out.  i suggest starting here: [http://easylinux.info/wiki/Ubuntu_dapper#DHCP_Server](http://easylinux.info/wiki/Ubuntu_dapper#DHCP_Server)


sir i had knowledge in windows server and i experience configuring windows 2000 Family and 2003 servers.. is it the same  as windows  when you configuring DHCP?  i dont how to set the IP forwarding... thank you!

---

### Post by dmizer on 2006-09-25
sorry, in the absolute beginner forum, i assume zero knowledge.  i meant no slight to your experience level.  i simply address the problems at the level the forum requires.

for configuring ip forwarding, you'll need to configure your ip tables somehow.  ip tables is linux version of a firewall.  usually people configure iptables with a gui of some sort because ip tables is a nightmare to configure manually (in my opinion).

if you have a graphical desktop already installed, i suggest installing firestarter to configure ip tables.  it can to nat and ip forwarding.

the howto i linked to gives directions for internet connection sharing only.

terminology you learned in windows will be the same, but how you go about configuring the settings is significantly different.

---

### Post by patz on 2006-09-25
> **dmizer said:**
> sorry, in the absolute beginner forum, i assume zero knowledge.  i meant no slight to your experience level.  i simply address the problems at the level the forum requires.

for configuring ip forwarding, you'll need to configure your ip tables somehow.  ip tables is linux version of a firewall.  usually people configure iptables with a gui of some sort because ip tables is a nightmare to configure manually (in my opinion).

if you have a graphical desktop already installed, i suggest installing firestarter to configure ip tables.  it can to nat and ip forwarding.

the howto i linked to gives directions for internet connection sharing only.

terminology you learned in windows will be the same, but how you go about configuring the settings is significantly different.

sir i already configure the gui and ip tables as well as DHCP. but it doesn't work, i dont know how to set the ip forwarding in order to share the connectoin of the internet.. thank you.

---

### Post by dmizer on 2006-09-25
what are you using to configure iptables?  firestarter?  webmin?  if you've configured them manually, i doubt i'll be able to help you much.

here's a quick guide that you should be able to use to share your internet connection.

you'll need to figure out which network adapter will be your local (lan) adapter and which will be your internet (wan) adapter:
```
ifconfig
```
providing your dhcp server is currently connected to your internet, the wan adapter should contain your internet ip address.  make a note of what ubuntu calls this (eth0, eth1 etc).

i highly recommend using firestarter to configure your dhcp server and internet connection sharing.  if you don't already have it installed, do so by:
```
sudo aptitude install firestarter
```

if you've already done that, determine which ethernet adapter has wan and which has lan.
type:
```
ifconfig
```
your wan adapter should have your wide area network ip address. if you have more than two lan adapters attached, this might be difficult, but you will need to determine which adapter will be used for your local network.

once you have that all figured out, do the following:

1) open firestarter by typing:
```
sudo firestarter
```
2) in firestarter, go to:
preferences >> network settings:
3) choose your internet connection device (usually eth0, but check ifconfig to see which device is getting an ip from your isp).
4) choose your local connected device (usually eth1, but this too can vary ... again, check ifconfig to insure that you choose the correct device).
5) check "enable network connection sharing"
6) if you want dhcp for your local network, select "enable dhcp ..."
7) under dhcp server details, select your desired ip range (usually starting 192.168.0.100 and ending where ever you'd like).

now you need to configure your local area network interface.

1) open network interfaces:
```
sudo nano /etc/network/interfaces
```
2) add (or edit if it's already there) the secondary (local area) interface to the end of this file:
```
iface eth1 inet static
        address 192.168.0.1 *<< replace 192.168.0.1 with your desired router ip* 
        netmask 255.255.255.0
```
3) save by hitting ctrl+x > select yes > hit enter to confirm the save.

restart your network:
```
sudo /etc/init.d/networking restart
```

now see if you can pull a local ip address.

let me know how you fare.  the above was quickly written, but i believe it to be complete.

alternatively, either the guide i posted earlier or the guide Marsolin posted will also produce the same results.

---

