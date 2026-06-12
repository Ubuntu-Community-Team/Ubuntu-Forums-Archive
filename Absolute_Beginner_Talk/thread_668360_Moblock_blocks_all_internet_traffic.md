---
title: "Moblock blocks all internet traffic"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by rbrittner on 2008-01-15
Ok so I'm very new to linux and have been finding it a huge step up from windows but I've ran into a snag.  So I decided to install ktorrent last night and wanted to use peerguardian, instead (since it's no longer supported) I thought moblock could do the trick.  After following the install instructions on 
[https://help.ubuntu.com/community/MoBlock]("https://help.ubuntu.com/community/MoBlock")
I thought it installed good, but then my internet started to give me griefe.  I use my router as a DNS so my IP is staticly assigned.  Anyone have any ideas on why or what I could do to fix this issue.  Eventually I just uninstalled moblock and it started working again but I would really like to use this program.  Also one last question, I use Opera and since it has a built in torrent program I want to point it to use ktorrent.  Where do these programs install by default (windows user - sorry)

---

### Post by nem75 on 2008-01-15
> **rbrittner said:**
> Also one last question, I use Opera and since it has a built in torrent program I want to point it to use ktorrent.  Where do these programs install by default (windows user - sorry)

Since most program executables can be found in /usr/bin and this directory is always in the path environment variable, you don't need to tell Opera the complete path to the executable.

Just tell it to open torrents with "ktorrent" and you should be fine.

---

### Post by rbrittner on 2008-01-15
Ok thanks for the reply about ktorrent and opera, anyone else on the moblock blocking my internet?

---

### Post by Nameless_one on 2008-01-16
Actually, the Community Reference Document is a bit old. If you did the part about http, you'll have to change it. 

Re-install MoBlock. Open /etc/moblock/moblock.conf, and change the line : ```
WHITE_TCP_OUT=""
``` to read: ```
WHITE_TCP_OUT="80 443"
```. 

Port 80 is the http port, and 443 is the https port. Also, if you are using MSN and MoBlock is blocking it, try adding port 1863 to the list. Come back with the results :)

---

### Post by jre on 2008-01-17
You may also whitelist your complete LAN, see this section:
```
# This is an example to whitelist the range 192.168.178.1-192.168.178.255:
WHITE_IP_IN="192.168.178.0/24"
WHITE_IP_OUT="192.168.178.0/24"
```

Please also read the comments in that file (--> restart moblock after editing)

---

### Post by Jinx-Wolf on 2008-03-28
Stumbled upon this while trying to fix MSN.

For anybody else who's having this problem and uses Yahoo, add 5050.

---

### Post by Crash90 on 2008-04-04
Will setting HTTP and HTTPS incoming and outgoing open me up to anti P2P groups? It seems to be the only way that I can have the internet function.

---

### Post by Nameless_one on 2008-04-04
I believe you only need to open these ports outwards (in WHITE_TCP_OUT). That way, incoming connections to these ports are blocked. I am not sure wether this constitutes a gap in security.

---

### Post by jre on 2008-04-04
You only need the WHITE_TCP_OUT to be able to browse the internet.
WHITE_TCP_IN would be needed if your computer was a webserver running apache.

Now, if you set WHITE_TCP_OUT="http https" then another host may run a p2p app which is listening on port 80 or 443 and your computer might connect to it.
To prevent this you may tell your P2P application not to use port 20 and 443. Of course not all applications do have this functionality.

Alternatively you can whitelist IPs, not ports. With mobloquer this is quite easy. Or only use MoBlock if you think you need it.
Or don't rate the "risk" to high ;-)

---

