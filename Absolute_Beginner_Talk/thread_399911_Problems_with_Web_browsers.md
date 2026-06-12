---
title: "Problems with Web browsers"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by linux_crazy on 2007-04-02
I have a problem with web browsing. I have installed many Linux distros (last Kubuntu 6.10). They all have one thing in common. The only web browser which 
 works for me is konqueror. I have intalled mozilla and opra but both of them 
 freeze on 'connecting to ...' then 'connection timeout' .My computer is connected to internet through Actiontec Wireless DSL Modem--->Ethernet cable. 

 I dug around and a source of problem is DNS.
 When I change /etc/resolve.conf to 'nameserver 205.171.2.65 nameserver 205.171.3.65'
 
 everything seems to work fine exept when I restart my system the resolve.conf
 overwrites itself to original 'nameserver 192.168.0.1
 nameserver 205.171.3.65'
 and back to begining only konqueror works. Any ideas how to fix this problem???
 
 P.S. getting tired changing resolv.conf
Edit/Delete Message

---

### Post by metalkr on 2007-04-02
[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by linux_crazy on 2007-04-03
Thanks it works now

---

