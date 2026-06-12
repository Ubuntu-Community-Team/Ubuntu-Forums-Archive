---
title: "help reading dmesg ouput (any pointer is enough)"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by towsonu2003 on 2005-12-11
Hi,
After setting guarddog (firewall), I started getting these weird (firewall-related) messages that I dont kow how to read... When i had firestarter, I would just look at its log thing... With guarddog, I cant :)

 would appreciate any pointers to a guide or something on how to read dmesg output that looks like this:```
[4300874.823000] DROPPED IN=ppp0 OUT= MAC= SRC=216.109.127.60 DST=10.21.93.168 LEN=1420 TOS=0x00 PREC=0x00 TTL=50 ID=15249 DF PROTO=TCP SPT=80 DPT=5063 SEQ=2559095911 ACK=1955605696 WINDOW=33120 RES=0x00 ACK PSH FIN URGP=0 
[4300884.834000] ABORTED IN=ppp0 OUT= MAC= SRC=66.230.239.174 DST=10.21.93.168 LEN=40 TOS=0x00 PREC=0x00 TTL=251 ID=46799 PROTO=TCP SPT=80 DPT=3337 SEQ=2356729624 ACK=1967490276 WINDOW=1996 RES=0x00 ACK RST URGP=0 
[4300885.575000] DROPPED IN=ppp0 OUT= MAC= SRC=66.230.239.174 DST=10.21.93.168 LEN=52 TOS=0x00 PREC=0x00 TTL=49 ID=11150 DF PROTO=TCP SPT=80 DPT=3338 SEQ=4169970372 ACK=1964023448 WINDOW=7504 RES=0x00 ACK URGP=0 OPT (0101050A829DED5D829DED5E) 
[4300885.930000] ABORTED IN=ppp0 OUT= MAC= SRC=66.230.239.174 DST=10.21.93.168 LEN=40 TOS=0x00 PREC=0x00 TTL=251 ID=46808 PROTO=TCP SPT=80 DPT=3326 SEQ=1728043466 ACK=1935708738 WINDOW=16019 RES=0x00 ACK RST URGP=0 
[4300887.190000] ABORTED IN=ppp0 OUT= MAC= SRC=66.230.239.174 DST=10.21.93.168 LEN=40 TOS=0x00 PREC=0x00 TTL=251 ID=46834 PROTO=TCP SPT=80 DPT=3337 SEQ=2356729623 ACK=1967490276 WINDOW=1996 RES=0x00 ACK RST URGP=0 
[4300887.190000] ABORTED IN=ppp0 OUT= MAC= SRC=66.230.239.174 DST=10.21.93.168 LEN=40 TOS=0x00 PREC=0x00 TTL=251 ID=46857 PROTO=TCP SPT=80 DPT=3338 SEQ=4169970372 ACK=1964023448 WINDOW=1996 RES=0x00 ACK RST URGP=0
```

Well, I am guessing what "aborted/dropped", "in=ppp0", "src", and "dst" are, but the rest is very postmodern (read: stuff I can't understand)... I would like to understand what my firewall is doing in its spare time :)

any help appreciated

thanks :)

---

### Post by janrinok on 2005-12-11
This might help -

[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)


Jan

---

### Post by towsonu2003 on 2005-12-11
[QUOTE=janrinok]This might help -
[http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)
[/QUOTE]
Hey thanks. Although it's a good tutorial, I could not find enough reference to iptables logging in there. I also tried man syslogd and cat /etc/syslog.conf but could not find any relevant info... 

It seems, from the logging example given in that tutorial, I need what the meaning of these abbreviations are for iptables:
```

[xxxxxxx.xxxxxx]=? LEN=? TOS=? PREC=? TTL=? ID=? DF=? SPT=? DPT=? SEQ=? ACK=? WINDOW=? RES=? ACK=? PSH=? FIN=? URGP=0=?
```again, any pointers or someone with enough english to decipher them: very appreciated :)

---

### Post by towsonu2003 on 2005-12-21
bump |^

:confused:

---

### Post by Lambert on 2005-12-21
See if this link helps you.

[http://search.cpan.org/~paulv/POE-Filter-Log-IPTables-0.02/IPTables.pm](http://search.cpan.org/~paulv/POE-Filter-Log-IPTables-0.02/IPTables.pm)

---

### Post by towsonu2003 on 2005-12-21
hey thanks Lambert. I think that is perfect and have answers for the ones I really wanted to know :) for anyone interested:

[xxxxxxx.xxxxxx]=some kind of timestamp that my dmesg / iptables log dont parse correctly for some reason (why??)
LEN= The length of the IP packet
PROTO= protocol (self explanatory, not in that page)
TOS= The Type of Service of the IP packet
PREC= The Precedence of the IP packet (need more research on what that is)
TTL= The time to live of the IP packet (need more research)
ID= The id of the IP packet 
DF= (Don't know, not in that page)
SPT= (not in that page) 
DPT= (not in that page) 
SEQ=The sequence number of the <type of packet here> packet 
ACK= (not in that page)
WINDOW= (not in that page) 
RES= (not in that page)
PSH= (not in that page) 
FIN= (not in that page) 
URGP=0= (naturally, not in that page :) )

I guess having a log analysis tool or logging deamon designed specifically for the firewall is more useful, for those who need such advanced info (I am assuming a desktop user who basically just browse web dont really need one). Repos have a couple of those tools.

---

### Post by Lambert on 2005-12-21
If any of the other ones interest you.


DF= (Don't know, not in that page)

[COLOR=Blue]fragment_flags[/COLOR] [COLOR=Blue]An arrayref. Can have "CE" (congestion), "DF" (don't fragment), or "MF" (more fragments are coming).[/COLOR]
  
SPT= (not in that page) 

[COLOR=Blue]Look into shortest path tree

[/COLOR] DPT= (not in that page) 

[COLOR=Blue]Look into dynamic packet transport[/COLOR]

SEQ=The sequence number of the <type of packet here> packet 

[COLOR=Blue]seq[/COLOR] [COLOR=Blue]The sequence number of the ICMP echo packet.[/COLOR]
 


ACK= (not in that page)
PSH= (not in that page) 
FIN= (not in that page) 

[COLOR=Blue]flags[/COLOR] [COLOR=Blue]An arrayref. Can be any combination of "CWR" (Congestion Window Reduced), "ECE" (Explicit Congestion Notification Echo), "URG" (Urgent), "**ACK**" (Acknowledgement), "**PSH**" (Push), "RST" (Reset), "SYN" (Synchronize), or "**FIN**" (Finished)[/COLOR]
  
WINDOW= (not in that page) 

[COLOR=Blue]window[/COLOR] [COLOR=Blue]The length of the TCP window.[/COLOR]
  
RES= (not in that page)

[COLOR=Blue]res[/COLOR] [COLOR=Blue]The reserved bits.[/COLOR]
  

URGP=0= (naturally, not in that page :) )

[COLOR=Blue]urgp[/COLOR] [COLOR=Blue]The urgent pointer.[/COLOR]

---

### Post by towsonu2003 on 2005-12-21
great help. thanks so much.

---

