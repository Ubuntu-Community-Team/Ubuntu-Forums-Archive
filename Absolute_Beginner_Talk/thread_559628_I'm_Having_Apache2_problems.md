---
title: "I'm Having Apache2 problems"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-09-25
My server was working and now only the local network has access.
I have done shields up tests and it shows port 80 as stealth under one test and open on another. people on the web get connecting to (site) and then nothing. I have three virtual sites again all work locally. what tools could I use to test the internet side of this connection, can I remove the local loopback port 127.0.0.0 from the config file, I need something that will allow me to go to the internet and back. Im using DMZ plus mode out of my dsl modem/router and have the server firewall running. I have firestarter running and cannot see anyone trying to hit port 80 or connecting to port 80.

now I did have music on one of my pages would some of the ISP's block my site because of this. I have taken the music off as of last night.

---

### Post by eggdeng on 2007-09-26
Make sure the router is forwarding port 80 to the server.
> something that will allow me to go to the internet and back 
As long as you are using a public IP or domain name to connect, you are doing this.

---

### Post by larry Gaminde on 2007-09-26
I have dmz open which allows all ports in to this machine.
and I can connect just fine from my network  just not outside connections  I  was thinking  that the router  would  forward it through without going to the internet.

---

### Post by eggdeng on 2007-09-26
Sorry if I'm misunderstanding you but I get the impression you're connecting to the server with your private IP. Just to exclude this, can you check your public IP with this command
```
zenity --info --text=" `wget http://checkip.dyndns.org/ -O - -o /dev/null | cut -d: -f 2 | cut -d\< -f 1 ; /sbin/ifconfig eth0 |grep inet\ adr | awk '{ print $2} ' |cut -d: -f 2 `"
```
and then type the output into the address bar of your browser.

---

### Post by larry Gaminde on 2007-09-26
the Ip address is correct.  Im using dyndns  on a dynamic address and the address that came up is correct. I will save that little command line didn't know you could do that.

---

### Post by larry Gaminde on 2007-09-26
I may be having trouble with lokkit and iptables I posted another post on this just now Im really not sure if port 80 is open on the firewall or not using sheilds up site it's showing as stealth or blocked most of the time.

---

