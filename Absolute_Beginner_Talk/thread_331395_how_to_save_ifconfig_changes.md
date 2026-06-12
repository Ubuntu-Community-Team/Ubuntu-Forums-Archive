---
title: "how to save ifconfig changes"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by lucman on 2007-01-04
Hi,

does anybody know how to save changes made by the ifconfig command? by entering ifconfig eth0 192.168.0.1 i've managed to share internet connection between my linux computer and my win xp computer... the problem is that everytime i restart my linux i have to enter the command again... i would like to know how to save that command so it runs everytime y boot linux...

Thanx

---

### Post by dannyboy79 on 2007-01-04
i believe ifconfig only reads what is inside the interfaces file within /etc/network/. it sounds to me like your network setting is dhcp but then after you log in you change it to static so you can share the internet connection. this is what my /etc/network/interfaces file looks like and I have a static ip

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers xx.xx.xx.xx

I believe you can do this with a gui though, go to system, admin, then networking, and just setup your eth0 to be static and fill in your ip you want and the dns servers it should use. some people can simply put their router and that will forward your isp's dns server info to your computer but for me I added my router as a dns server as well as my isp's dns servers. the gateway is my router. if you don't have a router than I am not sure what you would put got your gateway. good luck.

edit:
i also forgot 2 mention that you also may want to make sure that your /etc/resolv.conf file contains your dns servers also. example:
nameserver 81.26.228.3
nameserver 81.26.227.3

---

