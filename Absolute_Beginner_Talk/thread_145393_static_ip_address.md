---
title: "static ip address"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by awalesminfo on 2006-03-16
hi guys am facing problem with my broadband connection am having the static ip address and so i modified the /etc/networl/interfaces file but still i have to give dns from graphical mode so please tell me how i can give it from the /interfaces file and how i can down and up the eth

---

### Post by kmi on 2006-03-16
[QUOTE=awalesminfo]hi guys am facing problem with my broadband connection am having the static ip address and so i modified the /etc/networl/interfaces file but still i have to give dns from graphical mode so please tell me how i can give it from the /interfaces file and how i can down and up the eth[/QUOTE]

```
sudo ifconfig eth0 up
```
and
```
sudo ifconfig eth0 down
```

(replace eth0 if necessary)

Concerning DNS add this (if my memory is good... I'm on a &$$%^ç Win**** machine at the moment...) :
```
dns-nameservers aaa.bbb.ccc.ddd
```
at the end of /etc/network/interfaces (with the actual IP of your DNS...)

Should be OK ! :)

---

### Post by dvarsam on 2006-03-16
Hello !

I do NOT understand:

The _difference_ between setting up the DNS from the file "[color=blue]/etc/network/interfaces[/color]" & adding:

dns-nameservers aaa.bbb.ccc.ddd

...like you suggested above,

And setting up the DNS from the file "[color=blue]/etc/resolve.conf[/color]".
If the file does NOT exist, create one & adding in it two lines as follows:

nameserver xx1.yy1.zz1.kk1
nameserver xx2.yy2.zz2.kk2

Where xx1.yy1.zz1.kk1 & xx2.yy2.zz2.kk2 are the Server addresses (your Internet Service Provider should give them to you) &#8211; Article#: 138581

And why would somebody have 2 DNS Server addresses?

Is this a common method when there is a lot of traffic in an Internet Site (so some people are directed to one Server address & some other people are directed to a diff Server address, but BOTH Servers contain the SAME content)?

---

### Post by morpheus2485 on 2006-03-17
i am having the same problem just now - if i use dhclient, it configures everything quite happily, but I am trying to set up a static IP address, and whenever I type the command ifconfig ra0 X.X.X.X/X  i get  a numerical connection to the internet (i can connect to server's based on IP address), but the DNS is broken and i can't seem to find a way to fix it.

---

### Post by steve.horsley on 2006-03-17
The filename you need to create/edit is **/etc/resolv.conf** . Note the spelling.

You should list the nameservers in the file one per line, like this:
[B]nameserver 1.2.3.4
nameserver 5.6.7.8[/B]

That should do the trick.

---

### Post by Sanderfox on 2006-03-17
Doesn't /etc/resolv.conf get overwritten by resolvconf ?

---

### Post by kmi on 2006-03-17
I think it does... if you have the resolvconf installed... :)

steve.horsley :
Editing /etc/network/interfaces - or doing it with the GUI - should work, shouldn't it (well, I'm pretty sure I've never edited resolv.conf and static IP actually works...) ?

---

### Post by steve.horsley on 2006-03-17
Well, I have to admit I'm hazy on this myself. Where is BitTwister when you need him? Anyway, my Dapper install doesn't have a resolvconf, and in Breezy it's a directory. /etc/resolv.conf is where the nameservers addresses seem to go. It seems to get written automatically by the DHCP client because on my lappy, the contents change depending on where I plug it in. Totally different addresses at home and at work. Of course, logic says that if you turn the DHCP client off, the file won't get updated any more.

---

### Post by awalesminfo on 2006-03-18
hey guys :-|  the dns is still giving problem and every time i have to goto the gui and add it ,this also changes my interfaces file and deletes the gateway line and adds 2 more lines under ,
auto lo
iface lo inet loopback

guys please help me from this dns problem i tryed all ur sol's but they are not working on my pc

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address _._._._
netmask _._._._
gateway _._._._

---

### Post by kmi on 2006-03-18
:confused: Ok... You might be in a sitution described by other users and for which solutions are described [here]("http://doc.gwos.org/index.php/Router_DNS_Problems#HOWTO:_Router_and_DNS_problems").
Does it do the trick ?

---

