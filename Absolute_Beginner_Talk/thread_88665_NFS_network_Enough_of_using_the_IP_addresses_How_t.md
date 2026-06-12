---
title: "NFS network: Enough of using the IP_addresses: How to replace IP by name of the PC ?"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-11-10
NFS network: Enough of using the IP_addresses: How to replace IP by name of the PC ? 

In the linux network, sometimes IP addresses are changing cos of DNS
how to make recognize linux boxes pc with only their intrinsic name (defined during the installation of the pc) ?
I mean a procedure that will work 
  
Thank you very much

Greetigns

Patrick

---

### Post by getglenn on 2005-11-10
have you looked at [www.ubuntuguide.com?](www.ubuntuguide.com?)

"How to mount network folder on boot-up, and allow all users to read/write?"

may help you, although it is for SAMBA

---

### Post by patrick295767 on 2005-11-10
[QUOTE=getglenn]have you looked at [www.ubuntuguide.com?](www.ubuntuguide.com?)

"How to mount network folder on boot-up, and allow all users to read/write?"

may help you, although it is for SAMBA[/QUOTE]
  
I tried once some stuffs from the guide but it didnt work...  :-(
I passed it... 
I'll look again, ok !

thank you very much !!

Patrick

---

### Post by getglenn on 2005-11-10
happy to try and help!

although i'm not very knowledgable...

in fact, am having trouble understanding networking linux [see recent post] so you may have some advice for me

---

### Post by Joe_lurker on 2005-11-10
You have two options:
1. run a DNS server on you network (pain in the @$$)
2. use the /etc/hosts file

Options 2 is the easiest option.  Edit the file '/etc/hosts' adding an entry for each machine on your network.
```
192.168.111.3 HPOfficeJet7300 hpoj7300 color
192.168.111.99 Computer1 comp1
192.168.111.2 HPLaserJet5MP hplj5mp laser

```
The format above is:
<IP Address> <Computer Name> <Alias> <Alias...>

You can read the man page for further options: 'man hosts'.

-Joe

---

### Post by patrick295767 on 2005-11-11
[QUOTE=Joe_lurker]You have two options:
1. run a DNS server on you network (pain in the @$$)
2. use the /etc/hosts file

Options 2 is the easiest option.  Edit the file '/etc/hosts' adding an entry for each machine on your network.
```
192.168.111.3 HPOfficeJet7300 hpoj7300 color
192.168.111.99 Computer1 comp1
192.168.111.2 HPLaserJet5MP hplj5mp laser

```
The format above is:
<IP Address> <Computer Name> <Alias> <Alias...>

You can read the man page for further options: 'man hosts'.

-Joe[/QUOTE]
  
Well, since I am in DHCP, the IP addresses can change ... so I guess I'll have only the option > 1. run a DNS server on you network (pain in the @$$)
  Anyhow, progressing is always with difficulties !!
  
(I go to bed and let u now 2morrow)
  
Pat' !

---

