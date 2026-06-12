---
title: "DSL router problems SOLVED"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by gudy1024 on 2007-02-22
:)

---

### Post by ubunutgoz on 2007-02-22
how do I know which kernel version i use?

thanx
Alan

---

### Post by gmutt on 2007-02-22
"Finally after so many tries, OS changes (ubuntu 6.1 -> kubuntu 6.1, 7.1, 6.06..and 1 milion gray hairs more, this is it ! For all of you who are at home and using a (A)DSL router with NAT and DHCP"

Apreiate all your efforts Gudy from Thialand and for your response, I will give it a try and see what blows up hehe......Thanks

---

### Post by gudy1024 on 2007-02-22
> **ubunutgoz said:**
> how do I know which kernel version i use?

thanx
Alan

okay I have added a few more lines to explain the details

greetings Gudy

---

### Post by Rui Pais on 2007-02-23
Hi, got to this thread following indications from other threads...

Sorry but what you stand is not correct. 

The config files on /boot are just backups from kernel builded options. 
It's irrelevant to change it or not (unless you then copied the changed file to a kernel source tree named as .config and recompile the kernel).

The simple ways to disable ipv6 is just backlist them. [Here an how-to]("http://ubuntuforums.org/showthread.php?t=87798").

The file that you mention and don't remember the name it's /etc/resolv.conf.
If it's overwritten (meaning that you probabilly use dhcp and not static IPs) you should do:
```
$ sudo gedit /etc/dhcp3/dhclient.conf
```
and add to the end of file:
> prepend domain-name-servers <your_primary_DNS_IP>,<your_secondary_DNS_IP>;

if you don't know the DNS IPs, just check your router setting with a browser
or use some general DNS servers:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
and after that restart network.

Hope that clarifies the question.

Edit: [Here is an excellent thread on the subject]("http://www.ubuntuforums.org/showthread.php?t=282034").

---

### Post by gudy1024 on 2007-02-23
the point is I was trying this before.... and its not working because I have to use dchp, no option for a static IP
When you start "drapper" you see on the screen that the config file is read, this is something you don't see anymore in 6.10 and 7.01 (h3) of course its not nice to see all those messages running over the screen...but it was usefull :)
,by commenting out those parts in the config file. all troubles gone....:)

its okay you have put the other link too ,the more info we can give the better

to test if it was really ipv6 giving the troubles with the router, I've done a clean install of xp and by internet connection protocols, only activated tc/ipv6 and not tc/ipv4.... same troubles as in linux,

I hope in the next release version 7.04 we will have ipv6 standard DISABLED, and with a simple option enabled...the point is where must we report this to get it done for the next release :))))

---

### Post by Rui Pais on 2007-02-23
> **gudy1024 said:**
> the point is I was trying this before.... and its not working because I have to use dchp, no option for a static IP
When you start "drapper" you see on the screen that the config file is read, this is something you don't see anymore in 6.10 and 7.01 (h3) of course its not nice to see all those messages running over the screen...but it was usefull :)
Which one not worked? the ipv6 turned off or the dns config? 
In edgy (and probabilly on festy) you just need to do:
```
sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist
```
and to use dhcp you need to change the dhclient.conf file, not resolv.conf one.

> by commenting out those parts in the config file. all troubles gone....:)

Sorry to insist on this, but the config files are just text backup files. You can delete them, replace by shakespeare sonets, what ever. They aren't use as configurations files... (they would be in /etc if that was the case)
What probably happened was that you managed to turn ipv6 off, with the usual blacklist or aliases, and only checked after you changed config file. 
> to test if it was really ipv6 giving the troubles with the router, I've done a clean install of xp and by internet connection protocols, only activated tc/ipv6 and not tc/ipv4.... same troubles as in linux,
Yes thats an internet issue, not OS specific. The DNS problem seems to be an issue of some routers/modems.

> 
I hope in the next release version 7.04 we will have ipv6 standard DISABLED, and with a simple option enabled...the point is where must we report this to get it done for the next release :))))
That has been discussed to death. Wouldn't happen, 'cause ipv6 is to be the future of Internet, so sooner or later will be the standard used. The silly part is in the "sooner or later", what happening in reality is later, very later... (Not in next decade probabily :lol:) 
It's a bit ridiculous to Ubuntu to start use that as default, specially with a lot of people having problems... is like selling cars with parachutes with the argument that in the future cars maybe will fly like in Blade runner movie ;)

---

