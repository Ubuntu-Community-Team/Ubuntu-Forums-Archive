---
title: "Not able to connect to the internet"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by sujithnambath on 2007-05-14
I just reinstalled ubuntu in my laptop, previously i was able to connect to the internet wireless(intel pro 2200 wireless card) and wired network.
now after reinstalling i am not able to access anyway to the internet .
i am sure my hardware is supported by ubuntu since it worked previously perfectly..
what can i do? i have no clue how to fix this.

thanxs
Sujith

---

### Post by Pulka on 2007-05-14
try turning off ipv6

---

### Post by sujithnambath on 2007-05-14
i am sorry i am new to this OS 
i tried rmmod ipv6 and got error:module ipv6 is in use

ps: i got my ethernet card and wireless card listed.... but it is not getting connected and wireless is not listed in network settings....so no option to connect with that too..

help please
sujith

---

### Post by annda on 2007-05-14
which version of ubuntu do you have?

have you installed the restricted kernel modules?

also, it's strange that your wired connection is not working...

what is the output of ifconfig? and the contents of /etc/network/interfaces ?

are you using the gnome network manager (via panel applet) or system tools to manage the connections?

---

### Post by MoxJet on 2007-05-14
Can you post output of the following commands?
```
cat /etc/network/interfaces
```
```
sudo ifconfig
```
```
sudo mii-tool
```

---

### Post by sujithnambath on 2007-05-15
itz really a strange problem..ubuntu seems to detectthe network once in every 5-6 restarts..otherwise nothing shows in the network manager..neither my wireless card shows or wired network works.
i use the 7.04 fiesty ubuntu
output of interfaces

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



sudo mii-tool
eth0: no link

thanxs

---

