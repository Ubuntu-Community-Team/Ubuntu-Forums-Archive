---
title: "how can I connect to my ssh server?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-01-29
Ive set up an ssh server, but I dont know how to configure my zyxel router, or if that is even the problem..

so far, ive set static IPs for my 2 computers

windows putty client: 192.168.1.34
ubuntu ssh server: 192.168.1.33

and so if I putty to 192.168.1.33 from the windows machine on port 22, the connection "times out"

if I putty to 192.168.1.33 from teh windows machine on port 23, I get connection refused....

so I know something is sort of working right... but I cant even connect to the ssh server from within my network...

does anyone know what I need to do?

---

### Post by bodhi.zazen on 2008-01-29
See this link :

[uwiki]SSHHowto[/uwiki]

Start systematically testing ...

1. Firewall ??

2. Can you ping ??

---

### Post by joesmith1234 on 2008-01-29
> **bodhi.zazen said:**
> 

1. Firewall ??

2. Can you ping ??


1.  I dont know, that is why Im here.  But i am not leaving the subnet, so it should be ok... right?

2.  No, on windows cmd, ping 192.168.1.33 times out.
But note:  The ssh connections are different if I access an open port vs a closed port, so something is going on...

also, another note:  on the ubuntu machine I can ssh to "myself"... if i ssh 192.168.1.33, it works.

---

### Post by bodhi.zazen on 2008-01-29
From what you are describing you are fire walled.

for testing, turn off your firewall (your router will protect you) see if it works. Then bring your firewalls back up.

I can not help configure a windows firewall, I can help on the Ubuntu side, but you need to determine which firewall is problematic.

---

### Post by joesmith1234 on 2008-01-29
> **bodhi.zazen said:**
> From what you are describing you are fire walled.

for testing, turn off your firewall (your router will protect you) see if it works. Then bring your firewalls back up.

I can not help configure a windows firewall, I can help on the Ubuntu side, but you need to determine which firewall is problematic.

The firewall must be on the router, because I can connect to another ssh server on the internet just fine.

---

### Post by jcwmoore on 2008-01-29
192.168.1.xxx is a common ip address to PC's in you lan, i.e. behind your routers fire wall.  when I was setting up my SSH server I had to set request on port 22 (common SSH port) to be forwarded to my servers local ip address (that 192.168.1.xxx).  try googling for port forwarding and look how to set it up for you router.

I'm curious that you can not ping the other machine.  You should be able to, if they are on the same LAN.  you could try going to whatsmyipaddress.com to verify that you have the same public IP address on both machines

---

### Post by bodhi.zazen on 2008-01-29
did you configure you firewall on Ubuntu (iptables) or install firestarter ?

---

### Post by joesmith1234 on 2008-01-29
snip

---

### Post by joesmith1234 on 2008-01-29
by the way, I can connect on ssh from the windows machine to the ip
169.254.8.224


what does this mean??

---

### Post by bodhi.zazen on 2008-01-29
he he he ... 

It means :

You did not ssh into the correct IP address and it looks like the I address is being assigned to Ubuntu by DHCP and not static.

---

### Post by joesmith1234 on 2008-01-29
> **bodhi.zazen said:**
> he he he ... 

It means :

You did not ssh into the correct IP address and it looks like the I address is being assigned to Ubuntu by DHCP and not static.

ok, looks like i had jacked up the nat addressing somehow, so now I can go from windows to ubuntu across the network, but sshing into my global ip from an outside ssh tunnel doesnt work. 

at least i am getting somewhere...

---

### Post by bodhi.zazen on 2008-01-29
OK now you are talking about configuring you router.

See your router documentation, be sure and change the password on your router !!!

ALSO you NEED TO SECURE that ssh connection :

[uwiki]AdvancedOpenSSH[/uwiki]

---

