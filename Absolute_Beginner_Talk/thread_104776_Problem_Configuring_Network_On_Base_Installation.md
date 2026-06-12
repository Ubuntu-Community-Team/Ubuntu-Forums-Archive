---
title: "Problem Configuring Network On Base Installation"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by WhizCas on 2005-12-16
Hi,

I for a while now have run an apache server on my pc and it worked fine. Now im trying to put it on a small server I've got running at home. But I cant get internet to work... I have the following setup:

- a router @ ip adress 192.168.100.1 netmask 255.255.255.0
- layout /etc/network/interfaces:
> auto lo
iface lo inet loopback

mapping hotplug
  script grep
  map eth0

iface eth0 inet static
  addres 192.168.100.67
  netmask 255.255.255.0
  broadcast 192.168.100.255
  network 192.168.100.0
  gateway 192.168.100.1
 - i can ping my router and i can ping other pcs on my home network
- i cant ping ips outside my home network

I would really appreciate your help cause ive already tried a lot of guides and howtos but untill now nothing worked

---

### Post by Dr. Nick on 2005-12-16
Did you copy and paste your interfaces file or type it? I realized address is mispelled, wanst sure if that might be a problem or not. Can you login to your routers web interface from your browser? Also if you have gnome go to System-Administration-Networking and make sure your ethernet card is detected and activated

---

### Post by WhizCas on 2005-12-16
I didnt copy and pasted indeed, but the ip numbers etc are correct. I can login to my router interface, got it set up already for other pcs in the network and on those pcs internet works fine.

The server im trying to setup is base installation, so i dont have graphic interface and so i cant got to System-Administration-Networking and make sure your ethernet card is detected and activated... But i can ping other pcs so i think it shouldnt be a problem should it?

---

### Post by d1337 on 2005-12-16
and try again...here is my /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address         192.168.0.137
        netmask         255.255.255.0
        network         192.168.0.0
        broadcast       192.168.0.255
        gateway         192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 151.164.1.8 151.164.64.201
```
Add nameservers (according to your isp) and then restart by /etc/init.d./networking restart and see if that hooks you up.

d1337

---

### Post by WhizCas on 2005-12-16
I dont need to add data of isp because thats setup in my router... Further you got exactly the same settings as me, didnt type it in the first post but i also added auto eth0 but that didnt help.

---

### Post by d1337 on 2005-12-16
Most of my machines, whether Ubuntu or vanilla Debian, have _always_ needed me to add in the dns nameservers, even though it is set up in my router.  Simple edit, then we can rule it out and move on.

d1337

---

### Post by WhizCas on 2005-12-16
Ive got one windows xp pc and this pc is a ubuntu pc. And internet works perfect on both. I have cable in Holland and besides the ip adress i dont have any info on my inter provider, its a little different then dsl connections.

---

### Post by d1337 on 2005-12-16
Sorry I've not been much help.  If you can ping inside your network but not out, I can only think that you may check your router to insure that it isn't holding things up.  It sounds as if your card is working fine, so I'm at a loss...sorry.

d1337

---

### Post by WhizCas on 2005-12-16
[quote=d1337]Sorry I've not been much help. If you can ping inside your network but not out, I can only think that you may check your router to insure that it isn't holding things up. It sounds as if your card is working fine, so I'm at a loss...sorry.

d1337[/quote]

No Probs :D Thanks for your concern. If its inside my router I dont have a clue what to change, especially cause it already got internet shared... Anyone else has a clue?

---

### Post by d1337 on 2005-12-16
For grins, who is your internet provider?

d1337

---

### Post by Dr. Nick on 2005-12-17
[quote=WhizCas]I didnt copy and pasted indeed, but the ip numbers etc are correct. I can login to my router interface, got it set up already for other pcs in the network and on those pcs internet works fine.

The server im trying to setup is base installation, so i dont have graphic interface and so i cant got to System-Administration-Networking and make sure your ethernet card is detected and activated... But i can ping other pcs so i think it shouldnt be a problem should it?[/quote]

oh no gui,are you using a text based browser to test or just pings?  I have never had this problem but saw this thread [http://ubuntuforums.org/showthread.php?t=95350&page=3&highlight=ip](http://ubuntuforums.org/showthread.php?t=95350&page=3&highlight=ip) which may be of some help. I would look  into the ipv6 and nameserver parts. When they say gedit though use nano since its text based

Sorry I cant be of more specific help

---

### Post by WhizCas on 2005-12-17
[quote=d1337]For grins, who is your internet provider?

d1337[/quote]

@Home: [http://www.home.nl/](http://www.home.nl/) , Im really not proud of it, but as a student u must live cheap...

---

### Post by WhizCas on 2005-12-17
[quote=Dr. Nick]oh no gui,are you using a text based browser to test or just pings? I have never had this problem but saw this thread [http://ubuntuforums.org/showthread.php?t=95350&page=3&highlight=ip]("http://ubuntuforums.org/showthread.php?t=95350&page=3&highlight=ip") which may be of some help. I would look into the ipv6 and nameserver parts. When they say gedit though use nano since its text based

Sorry I cant be of more specific help[/quote]

Maybe a n00bish question, but when you only use command line its called gui?

I already used vim to edit my files, is almost a like only u got line numbers etc.

Changed nameserver to 127.0.0.1 and turned ipv6 off, still didnt work out :(

---

### Post by bscbrit on 2005-12-17
I'm not sure that I have followed this thread but I must agree with d1337 that I cannot see how name resolution is taking place.  I accept that it is done by your router, but where have you told your server to look at the router when it wants a name resolving?  From the command line, can you ping, say, [www.symantec.com?](www.symantec.com?)

---

### Post by bscbrit on 2005-12-17
If your gateway is also your DNS, then edit /etc/resolv.conf to contain the following:

nameserver 192.168.100.1

You can have multiple nameservers (and they all have the same name - 'nameserver').  Just list them one after another in /etc/resolv.conf.

---

### Post by WhizCas on 2005-12-17
[quote=bscbrit]If your gateway is also your DNS, then edit /etc/resolv.conf to contain the following:
 
nameserver 192.168.100.1
 
You can have multiple nameservers (and they all have the same name - 'nameserver'). Just list them one after another in /etc/resolv.conf.[/quote]
 
Ok, at the moment I am not at home so I can't try it, but tomorrow I will show the results of the ping and Ill try adding nameservers...
 
Thanks for your help =D>

---

### Post by Dr. Nick on 2005-12-17
[quote=WhizCas]Maybe a n00bish question, but when you only use command line its called gui?

I already used vim to edit my files, is almost a like only u got line numbers etc.

Changed nameserver to 127.0.0.1 and turned ipv6 off, still didnt work out :([/quote]

vim is fine aswell , I suggested nano sine I use it. That thread  used gedit since they had gnome, but gedit wont work in command line.

Have tou tried using dhcp at all?

---

### Post by d1337 on 2005-12-17
Whois shows nameservers for home.nl as follows:

```
 Domain nameservers:
      ns1.home.nl          213.51.129.75
      ns2.home.nl          213.51.145.75
      ns3.home.nl          213.51.128.75

```
Try adding

```
dns-nameservers 213.51.129.75 213.51.145.75 213.51.128.75
```

to the bottom of your /etc/network/interfaces to see if resolv.conf may work itself out.

d1337

---

### Post by WhizCas on 2005-12-22
--- Problem Solved ---

I solved the problem the following way: I turned dhcp on, linux automattically changed my nameservers:

 /etc/resolv.conf

search @Home
nameserver 213.51.129.37
nameserver 213.51.144.37

----------------------------------

Thanks for your help d1337, Dr Nick and bscbrit

---

