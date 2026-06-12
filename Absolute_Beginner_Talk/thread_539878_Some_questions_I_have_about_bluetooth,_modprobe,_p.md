---
title: "Some questions I have about: bluetooth, modprobe, pand, networks, etc."
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Siph0n on 2007-08-31
1) Do I have to do modprobe every time I reboot? Like sudo modprobe bnep .

2) Is /etc/modules the file where I would put anything I normally load with modprobe?, so it loads every time I reboot?

3) My /etc/network/interfaces file is blank, yet to get online I type these commands:
sudo iwconfig ath0 mode managed key XXXXXXXXXXXXXXXXXXXXXXXXX
sudo iwconfig ath0 essid "MYESSID"
sudo dhclient ath0

If I were to put the following in my /etc/network/interfaces file, should it auto start my network connection when I reboot?:

auto ath0
iface ath0 inet dhcp
wireless-essid   MYESSID
wireless-key     XXXXXXXXXXXXXXXXXXXXXXXXX
wireless-channel auto
wireless-mode    managed


4) Where do I find out what drivers I have and am using? How can I stop using certain drivers so I can use others?

5) What is the difference between hcitool and hidd ?hcitool scan finds my bluetooth devices, but hidd --search doesn't, why? :)

6) I read somewhere that pand --ethernet <name of interace> is used to create the bnep interface in /etc/network/interfaces , but i just get the list of options when i type that command. Should I just add bnep0 to the file manually?

---

