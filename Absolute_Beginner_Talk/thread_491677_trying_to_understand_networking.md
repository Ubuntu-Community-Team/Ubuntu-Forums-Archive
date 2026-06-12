---
title: "trying to understand networking"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Matthyis on 2007-07-03
thank you

---

### Post by Computer-Slave on 2007-07-04
Please post a question and then demand an answers. Dont post posts without questions becoz they take place on server.

---

### Post by Matthyis on 2007-07-05
> **Computer-Slave said:**
> Please post a question and then demand an answers. Dont post posts without questions becoz they take place on server.

EXT_IP=24.x.x.x/32
INT_IP=192.168.0.1/32
EXT_NET=24.x.x.0/24
INT_NET=192.168.0.0/24
MASQ_NETS="192.168.0.0/24"
LOCAL_ADDRS="127.0.0.0/8 192.168.0.1/32 24.x.x.x/32"
MAIL_RELAY=24.x.x.x/32
SMB_ACCESS="192.168.0.2/32"
SMB_BCAST="192.168.0.255/32"

I dont understand soory if I sound dum as dirt but as this guy told me to repost to demond a answer becoz it goes on the server I just dident want to look stupied thank you but if someone can still help me out that would be cool because I'm just a grunt that dont like M$
so I'm trying to learn linux

---

### Post by Sober_Drunks/Wh/AK47 on 2007-07-05
I dont know becaz! I out thier far out

---

### Post by Computer-Slave on 2007-07-07
> **Matthyis said:**
> EXT_IP=24.x.x.x/32
INT_IP=192.168.0.1/32
EXT_NET=24.x.x.0/24
INT_NET=192.168.0.0/24
MASQ_NETS="192.168.0.0/24"
LOCAL_ADDRS="127.0.0.0/8 192.168.0.1/32 24.x.x.x/32"
MAIL_RELAY=24.x.x.x/32
SMB_ACCESS="192.168.0.2/32"
SMB_BCAST="192.168.0.255/32"

I dont understand soory if I sound dum as dirt but as this guy told me to repost to demond a answer becoz it goes on the server I just dident want to look stupied thank you but if someone can still help me out that would be cool because I'm just a grunt that dont like M$
so I'm trying to learn linux
Try visiting [http://computerzone.wetpaint.com/page/LAN+Networking+%28Linux-Windows%29](http://computerzone.wetpaint.com/page/LAN+Networking+%28Linux-Windows%29) and plz become a registered user with ur same username (Sober_Drunks/Wh/AK47) so that i can recognize u. I hope that helps if doesn't tell me on these forums.

Thanks!

---

### Post by jrusso2 on 2007-07-07
> **Matthyis said:**
> EXT_IP=24.x.x.x/32
INT_IP=192.168.0.1/32
EXT_NET=24.x.x.0/24
INT_NET=192.168.0.0/24
MASQ_NETS="192.168.0.0/24"
LOCAL_ADDRS="127.0.0.0/8 192.168.0.1/32 24.x.x.x/32"
MAIL_RELAY=24.x.x.x/32
SMB_ACCESS="192.168.0.2/32"
SMB_BCAST="192.168.0.255/32"

I dont understand soory if I sound dum as dirt but as this guy told me to repost to demond a answer becoz it goes on the server I just dident want to look stupied thank you but if someone can still help me out that would be cool because I'm just a grunt that dont like M$
so I'm trying to learn linux

Is there a question in there somewhere?

---

### Post by Sunforge on 2007-07-07
To keep this post as short as humanly possible, without boring you to death, here is a very, very quick run through what you have posted.
 
**EXT_IP=24.x.x.x/32**
This is your external web address. This IP address is what you use when you surf the web, send your mail and perform other tasks that are not destined for your local (internal) network.
 
**INT_IP=192.168.0.1/32**
This is your internal network address. You use this IP when you're performing tasks on your local network
 
**EXT_NET=24.x.x.0/24**
This is the subnet (network) that your external ip address belongs to.
 
**INT_NET=192.168.0.0/24**
This is the subnet (network) that your internal ip belongs to.
In a nutshell a /24 subnet has a mask of 255.255.255.0 with
useable address .1 through .254
broadcast address .255 (which is what other computers would use to find your computer if they were on the same subnet)
 
**MASQ_NETS="192.168.0.0/24"**
This is a Unix term that I can never place. Someone I'm sure will enlighten you on this one.
 
**LOCAL_ADDRS="127.0.0.0/8 192.168.0.1/32 24.x.x.x/32"**
This defines local subets:
127.0.0.1 is normally your loop back address, which is used for some internal processes
192.168.0.0/24 is your internal address
24.x.x.x/32 is your external address.
 
**MAIL_RELAY=24.x.x.x/32**
This is where you'd send you mail.
 
**SMB_ACCESS="192.168.0.2/32"**
This is all about server message block (generally used by Microsoft machines)
 
**SMB_BCAST="192.168.0.255/32"**
Ditto this one

Quick run through summary before I post some links:
Your network card has a mac (hardware address) that is tied to an IP (network address): you need both to function.
 
The words subnet and network are generically interchangeable and mean the same thing: a collection of IP addresses that all belong in the same place. They define what you can see and what you can't on a local network. To see other things on different networks you need a router (your modem, DSL router, satellite dish, tin on a string).
 
Why all the IP addresses? Well that's because we all have to live on different networks due to the limit of the TCP/IP version 4 protocol, which is probably a bit much for now.
Anyway that was your starter for ten. Follow the links, give them a read and hopefully you'll be on your way.

If you want to know more about IP and IP addresses in general, this is a good starting place:
[http://www.tokyopc.org/newsletter/1998/05/Ipintro_1.html](http://www.tokyopc.org/newsletter/1998/05/Ipintro_1.html)
 
The other thing that might be worth knowing about is "what is a mac address"
[http://compnetworking.about.com/od/networkprotocolsip/l/aa062202a.htm](http://compnetworking.about.com/od/networkprotocolsip/l/aa062202a.htm)

---

