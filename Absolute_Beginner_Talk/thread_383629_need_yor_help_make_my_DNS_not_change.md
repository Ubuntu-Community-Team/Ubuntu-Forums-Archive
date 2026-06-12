---
title: "need yor help make my DNS not change"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by fanny on 2007-03-13
i had many problem connect to the internet but now i find that if i put on the DNS tab my iSP DNS (212.143.212.143) im connected and everything works fine , just every 30 minutes (eprox...) i cant surf and i go to the dns tab and find another DNS (10.0.....)
im trying to solve this problem for a while . i have this link tell me if it will help me [http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html](http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html)
thanks !

---

### Post by fanny on 2007-03-13
..?

---

### Post by fanny on 2007-03-13
please

---

### Post by Rui Pais on 2007-03-13
hi, do not bump your threads every half an hour, is not considered polite ;)

[check here]("http://opendns.com/start/ubuntu.php") how to do it (last part of point 2).

---

### Post by fanny on 2007-03-13
i did step by step . still the same problem.

---

### Post by Rui Pais on 2007-03-13
do you add
```
prepend domain-name-servers ... , ...;
```
to /etc/dhcp3/dhclient.conf and it still be replaced by 10.0.0.x?

Do you tried to reboot with that option on dhclient.conf and checked if that still happen even after reinicialize your hardware with that options?

---

### Post by fanny on 2007-03-14
i did everything but still every 30 minutes it disconnect and the DNS back to 10.0.0.138 . theres most be a solution for this problem....

---

### Post by Rui Pais on 2007-03-14
Usually resolv.conf (where DNS IPs are) is overwritten by dhcp. 
Since yours are overwitten you must be using dynamic IP.
Try to use a Static one. At network-admin  -> Interface settings -> Configuration set your IP, subnet mask and gateway address according to your net specification 
(check those with ifconfig, should be something like 10.0.0.3 subenet: 255.255.255.0, gateway: router ip)

good luck

---

### Post by dannyboy79 on 2007-03-14
is that ip your router's ip? than that's fine, as long as you did the prepend with the isp dns servers than these dns servers' will always be viewed before your router so it doesn't matter if that 10. ip addresss keeps showing up in your dns tab. if you folowed the links instreuctions than that is the solution.

---

### Post by fanny on 2007-03-14
still nothing changed .
* i dont understand rui instruction (where is network admin -interface settings).

---

### Post by Rui Pais on 2007-03-14
> **fanny said:**
> still nothing changed .
* i dont understand rui instruction (where is network admin -interface settings).

sorry.

on a terminal type:
```
gksudo network-admin
```

---

### Post by fanny on 2007-03-14
sorry for me being stupid... but i see only 4 tabs : dns -generel-connections-hosts.
if you can direct where i write what?

---

### Post by fanny on 2007-03-14
sorry for me being stupid... but i see only 4 tabs : dns -generel-connections-hosts.
if you can direct where i write what?

---

### Post by undertakingyou on 2007-03-14
Is your IP address set to static or dynamic?  If it is dynamic it will update the DNS entry.  Change it to a static IP address and the problem should go away.

---

### Post by fanny on 2007-03-14
how do i know which ip to use in the static ip option? and subnet mas and gateway?

---

### Post by undertakingyou on 2007-03-14
in terminal type ```
ifconfig
``` it will give you a bunch of output, we are looking for one particular line.

example::  inet addr:192.168.10.187  Bcast:192.168.10.255  Mask:255.255.255.0

So, for your static ip enter the "inet addr".  For subnet mask put in "Mask" and for gateway put in the "Bcast" except change the last number to 1. (i.e.  Instead of 192.168.10.255 I would put in 192.168.10.1)

See if that does it.

---

### Post by fanny on 2007-03-14
thank you guys so much. i think you solve my problem ,

---

### Post by dannyboy79 on 2007-03-14
wait, how is that. for he benefit of all users, please explain how you solved it. other users will then not have to read 2 pages of posts only to find that there is no answer documented. thank you.

---

### Post by fanny on 2007-03-15
i will explain now. 
first i find my ISP provider DNS and i put it on the DNS tab.(actually i dont know what the DNS means...)
 
second i follow  this instruction :

in terminal type 
Code:
ifconfigit will give you a bunch of output, we are looking for one particular line.

example:: inet addr:192.168.10.187 Bcast:192.168.10.255 Mask:255.255.255.0

So, for your static ip enter the "inet addr". For subnet mask put in "Mask" and for gateway put in the "Bcast" except change the last number to 1. (i.e. Instead of 192.168.10.255 I would put in 192.168.10.1)

and thats it.

---

### Post by dannyboy79 on 2007-03-15
> **fanny said:**
> i will explain now. 
first i find my ISP provider DNS and i put it on the DNS tab.(actually i dont know what the DNS means...)
 
second i follow  this instruction :

in terminal type 
Code:
ifconfigit will give you a bunch of output, we are looking for one particular line.

example:: inet addr:192.168.10.187 Bcast:192.168.10.255 Mask:255.255.255.0

So, for your static ip enter the "inet addr". For subnet mask put in "Mask" and for gateway put in the "Bcast" except change the last number to 1. (i.e. Instead of 192.168.10.255 I would put in 192.168.10.1)

and thats it.

DNS stands for Domain Name Service. There are tons of "DNS" servers all around the world. these servers will convert domain names (gogle.com) into the ip address (64.233.167.104)  so that everyone doesn't have to remember the ip address of the website but can simply type in the name of it, so if you don't have your dns servers set up correctly for your computer, than it'll seem like you're not connected to the internet but you are. you could just type in 64.233.167.104 in the browser and it should go there.

also, you want to use ```
ifconfig
``` NOT ifconfigit, at least I didn't think ifconfigit was a command but I guess I can't say for sure since i am not at my linux box. this information is the information for interfaces. hence "if" config. so it will give you the ip address of your interface, what the gateway is that it's connected to, the mac address of your interrface and lots of info that's important.

well the above worked but didn't you also do the prepend option within your dhclient.conf? your dns server will be overwritten because whenever you receive a new dhcp lease (can be every 30 mins, it depends how it setup). just so you know, your explaination of the "bcast" thing and simply changing the end number to a 1 is not entirely correct and could screw other newbies. the gateway (which is what the Bcast is referring to) is merely the ip address of the router or modem between you and the internet, think of it as the "gateway" ip to the internet. glad you got it working.

---

### Post by haelters on 2007-03-15
I find it a very bad idea to change to a static ip configuration just because of the dns setup. If you do not want that dhcp is changing your favorite dns servers (in /etc/resolv.conf), simply edit /etc/dhcp3/dhclient.conf. In that file you will see the requests your dhcp client will ask the dhcp server. e.g:
```

request subnet-mask, broadcast-address, time-offset, routers,
       domain-name, domain-name-servers, host-name,
       netbios-name-servers, netbios-scope;

```
Simply remove domain-name-servers from that list and the nameservers in /etc/resolv.conf won't be updated anymore by your dhcp client.

The difference here (compared to the solution with the 
```
prepend domain-name-servers ... , ...;
```
) is that in my solution we completely ignore the domain nameservers the dhcp servers sends.

---

### Post by dannyboy79 on 2007-03-15
does this work for you????? no one said that you needed to change to a static ip to solve this, that is merely 1 solution. the solution mostly documented her is if you still want to use dhcp, than simply uncomment the prepend line in your dhclient.conf so that the "real" dns servers are used first before the router itself, as some routers don't properly forward dns server requests properly and then what happens is that the router trys to resolve the names and can't, then that's when you get all these people saying their internet doesn't work. we tell them to add their dns servers into the dns server tab, but then when the dhcp lease is up, it rights in the router's ip i think. so basically I am saying that I think your solution of NOT requesting that the dhcp server send dns servers this may also work but either solution is NOT better than the other.

---

### Post by fanny on 2007-03-15
first im a male nice to meet you. my nick is fanny. my name is daniel.

  how do i get to "etc/dhcp3/dhclient.conf" im dont know yet many commands. and why its not recomnded using static ip?

---

### Post by Rui Pais on 2007-03-15
> **fanny said:**
> how do i get to "etc/dhcp3/dhclient.conf" im dont know yet many commands. 
configs are at files inside /etc/. You can edit them with a text editor and admin powers... like:
```
gksudo gedit /etc/dhcp3/dhclient.conf
``` 

> and why its not recomnded using static ip?
none should be recommended over the other. 
If you have a small net, 2, 3, 4 computers, static is usually faster and simpler. each computer has its ip always set.
If you have a large network it's more secure to use dhcp to set they ips. Easier to administrate and one avoid errors like repeating an ip.

---

### Post by haelters on 2007-03-15
> **dannyboy79 said:**
> does this work for you?????
Yes, I've even tried it before I posted...

> **dannyboy79 said:**
> 
no one said that you needed to change to a static ip to solve this, that is merely 1 solution. 
My English probably isn't good enough, but I understood that he changed his IP Address:
> **fanny said:**
> i will explain now. 
So, for your static ip enter the "inet addr". For subnet mask put in "Mask" and for gateway put in the "Bcast" except change the last number to 1. (i.e. Instead of 192.168.10.255 I would put in 192.168.10.1)
and thats it.

> **dannyboy79 said:**
> 
as some routers don't properly forward dns server requests properly
I don't see the use of having the nameservers of a malfunctioning router inside /etc/resolv.conf.

> **dannyboy79 said:**
> basically I am saying that I think your solution of NOT requesting that the dhcp server send dns servers this may also work but either solution is NOT better than the other.
Indeed, but I never said your solution was not good (although I should have mentioned that to be very clear). Both solutions are good, but as said before, a malfunctioning router is of no use. I feel you find yourself attacked. This was in no way my intention. I only wanted to show the users that they have other solutions that to use the fixed ip in case of dns problems (especially as explained here: he takes an ip from the range used by the DHCP server, which is asking for trouble, because the DHCP server is going to reuse that address).

---

### Post by haelters on 2007-03-15
Let me make my self clear. DCHP and static IP is good. I ONLY wanted to say that changing simply because of dns problems should not be done. 

And also, If you use static IP DON'T take an IP that is in the range given to the DHCP server (or simply stop the DHCP server if you are going for static ip's)

---

### Post by dannyboy79 on 2007-03-15
> **haelters said:**
>  My English probably isn't good enough, but I understood that he changed his IP Address:
Yes, you are correct, he did change it to a static ip. I didn't read it closely enough and thought that he used the prepend solution so that his perferred dns servers would always be at the top and used first.
> **haelters said:**
> 
I don't see the use of having the nameservers of a malfunctioning router inside /etc/resolv.conf. 
For one thing, its not a malfunctioning router, some routers are designed this way.
D-Link routers, My netgear router (and probably some others) AREN'T actually DNS servers, they are merely DNS forwarders, Ubuntu (and some other linux OSes) don't realise this. Unfortunately, the router gives Linux the impression that it is a DNS Server, so until router manufacturers start learning the difference between DNS servers and DNS forwarders, OS's like Ubuntu might be plagued with this problem for a while. I completely agree though, there is no reason to have your router within your resolv.conf if the router isn't a true dns server so your solution is a better solution
> **haelters said:**
> 
Indeed, but I never said your solution was not good (although I should have mentioned that to be very clear). Both solutions are good, but as said before, a malfunctioning router is of no use. Well you stated that it was a bad idea to make an ip address static (at least that's what I originally thought). I thought that was a bold  statement but now I see that you only meant to say that making it static only to solve the issue if you had a bad router was a bad idea. Now I get it. :-)
> **haelters said:**
> 
I feel you find yourself attacked. This was in no way my intention. I only wanted to show the users that they have other solutions that to use the fixed ip in case of dns problems (especially as explained here: he takes an ip from the range used by the DHCP server, which is asking for trouble, because the DHCP server is going to reuse that address). 
No, I don't feel attacked at all. I agree again, it's not a good idea to chose an ip that the dhcp server is handing out as he'll get duplicate ip's if he ever introduces a new computer into his network than he'll be wondering what happened.

---

