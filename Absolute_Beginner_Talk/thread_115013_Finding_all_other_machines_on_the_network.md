---
title: "Finding all other machines on the network"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by TheAnonymousx on 2006-01-09
So, I'm trying to find out how to use the command line (or any method for that matter) to determine the IP addresses for every machine on the network connected to the router. 
Anyone got suggetions?

---

### Post by souki on 2006-01-09
if the hosts respond to ping, you can try
ping -b 192.168.0.255  (where 192.168.0.255 is the broadcast adress of your local network)

---

### Post by deNoobius on 2006-01-09
A CLI program called nmap can do it also, as well as return information about the other machines.  it is available from the repos.

---

### Post by jimrz on 2006-01-09
you should be able to go to your router using your browser, type http://<router ip> (probably 192.168.0.1) in the address bar, where you will likely find a list of all attached devices giving the name / ip address / mac address for each.

---

### Post by TheAnonymousx on 2006-01-10
Yeah, although I can go to the router, my roommate purchased the actual item and knows the password. I suppose I could ask him though (or try to guess the default one)

---

### Post by paulmilliken on 2006-01-10
[QUOTE=TheAnonymousx]So, I'm trying to find out how to use the command line (or any method for that matter) to determine the IP addresses for every machine on the network connected to the router. 
Anyone got suggetions?[/QUOTE]

If your subnet mask is, say, 255.0.0.0 and your gateway is 10.0.0.2 then you would type
"ping -b 10.255.255.255"
ie. in your ping command, replace the zeros in your subnet mask with 255 and the non-zero values with the corresponding values from your gateway address.

Paul

---

### Post by patrick295767 on 2006-01-11
Sthg very very very easy :
try the login manager, 
click on the remote X-connection, U'll have the list of all pc that are running Linux and XDMCP on the network.
  
I'll look for sthg with xterm ... 

Greetz

---

