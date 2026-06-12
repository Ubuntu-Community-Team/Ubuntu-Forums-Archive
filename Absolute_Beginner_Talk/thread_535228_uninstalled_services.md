---
title: "uninstalled services"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by kornface13 on 2007-08-26
Since I installed Ubuntu a week ago, I've done ALOT of expiramenting with different programs.  here's a problem i just noticed.


In the services manager, I see a few services that shouldn't be there.  For instance:

mysql
mysql-ndb
mysql-ndb-mgm
nfs-kernel-server (not sure if this is always here or not)
samba
RPC mapper (not sure what this is)
apache2


If these are uninstalled, how do I get them completely gone?


And lastly....

I have ALOT of listening ports, and am wondering if someone can help me figure out what the heck they all are...

Nothing should be listening except Kapote (it it listens) and other defaults.....  Someone please help.  Thanks in advance.


kornface13@DeezNuts:~$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:47550                 *:*                     LISTEN     
tcp        0      0 localhost:2207          *:*                     LISTEN     
udp        0      0 *:32768                 *:*                                
udp        0      0 *:32771                 *:*                                
udp        0      0 *:670                   *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:mdns                  *:*                                
udp        0      0 *:sunrpc                *:*

---

### Post by jamvegan on 2007-08-26
Are you familiar with lsof?  I can't remember if it's installed by default, but it's in Ubuntu's repositories.  It can provide more information on exactly which process is listening on a port.  For instance:
```
sudo lsof -i
```
on my machine shows the following:
```
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
avahi-dae 4934  avahi   13u  IPv4  17190       UDP *:mdns 
avahi-dae 4934  avahi   14u  IPv4  17191       UDP *:1024 
dhclient  5050   dhcp    6u  IPv4  17551       UDP *:bootpc 
hpiod     5109   root    0u  IPv4  17626       TCP localhost.localdomain:2208 (LISTEN)
python    5112  hplip    4u  IPv4  17637       TCP localhost.localdomain:2207 (LISTEN)
ntpd      5330    ntp   16u  IPv4  18015       UDP *:ntp 
ntpd      5330    ntp   17u  IPv6  18016       UDP *:ntp 
ntpd      5330    ntp   18u  IPv6  18017       UDP ubuntu-desktop.local:ntp 
ntpd      5330    ntp   19u  IPv6  18018       UDP ip6-localhost:ntp 
ntpd      5330    ntp   20u  IPv4  18019       UDP localhost.localdomain:ntp 
ntpd      5330    ntp   21u  IPv4  18020       UDP ubuntu-desktop.local:ntp 
cupsd     5949 cupsys    1u  IPv4  20053       TCP localhost.localdomain:ipp (LISTEN)
```

ipp is Internet Printing Protocol.  CUPS uses it, and it is something that you would normally expect to see.

hpiod is another printing thing (from HP).  I'm not sure exactly what it does, but it's also part of a normal install.

bootpc is what gets your IP address and so on from the network if it's not statically configured.  It's also a normal thing to see.

I think that mdns has to do with resolving machine names on the local network.

sunrpc listens for and forwards calls to other protocols.  I think that the actual process goes by the name of portmap.  This is not part of a standard install, and probably got installed to manage connections for some sort of server you tried out (NFS  or NIS?).

---

### Post by kornface13 on 2007-08-27
AWESOME!  thanks for the reply.  that does answer some questions, and yes, that utility does come pre-installed.

Now on to my next question....

Here's what I see when I look at the services page.

[http://i28.photobucket.com/albums/c202/kornface13/forum/Screenshot-Servicessettings.png]("http://i28.photobucket.com/albums/c202/kornface13/forum/Screenshot-Servicessettings.png")

I uninstalled mysql completely (autoremove/ remove --purge) and there is nothing left relating to mysql.  Is it normal for it to still show up in the services page?

---

