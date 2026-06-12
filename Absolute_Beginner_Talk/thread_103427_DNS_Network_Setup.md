---
title: "DNS Network Setup"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Phuayj on 2005-12-14
How do I setup DNS Network?

---

### Post by darth_vector on 2005-12-14
do you want to set up a dns server or just set up dns on your home machine? if you want to set up dns, just edit /etc/resolv.conf as root and add lines like

nameserver <ip of dns server to use>

---

### Post by Phuayj on 2005-12-14
I just want to set up dns network on my machine.

EDIT:But my TCP asks the server to assign the IP and assigns the server DNS/NBNS server addresses

---

### Post by darth_vector on 2005-12-14
if your server assigns dns then there is no need for you to do anything. note that this is done using DHCP, not TCP.

if your server is not seting up your dns servers, find out what dns servers you should be using and edit the /etc/resolv.conf file by adding

nameserver <dns server ip address>

for each dns server you wish to use.

---

### Post by Phuayj on 2005-12-14
I can't find the "resolv.conf" file. Do I have to use te console?

---

### Post by darth_vector on 2005-12-15
yep

---

