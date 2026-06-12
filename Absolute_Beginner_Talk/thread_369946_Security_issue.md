---
title: "Security issue"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by skiddly on 2007-02-25
[SIZE="5"][/SIZE]Well im a bit concerned now after been assured i do not need anti virus or firewalls on linux, i installed firestarter for peace of mind and have had quite a few messages saying computer been hit latest from 82.23.142.191 does this mean someone has accessed my pc or have tried and failed and how many people have hit me before i put firestarter in real worried now.

---

### Post by Tomosaur on 2007-02-25
It would normally just mean they tried to access, but firestarter turned them away. There can be lots of reasons for this. Yes, it could be someone scanning you for an easy way in to your machine, but this is such a regular occurence, it's not worth worrying about. The chances of them being able to get into your machine are very, very small. Firestarter is also not a firewall - it is a frontend to Linux's excellent, built-in firewall, which is called IPTables. Unless you yourself have opened up any holes into your machine, then you should be perfectly fine - Ubuntu is very tight regarding internet security.

---

### Post by skiddly on 2007-02-25
So do i need to set IPTables up or is it automatic when installing ubuntu and where would i look to check iptables or do i not

---

### Post by Tomosaur on 2007-02-25
> **skiddly said:**
> So do i need to set IPTables up or is it automatic when installing ubuntu and where would i look to check iptables or do i not

IPTables is already working away in the background. Firestarter allows you to configure iptables, but you don't need to do anything else unless you know you need to - for example, if you want to run your own web server from your computer - you will need to configure IPTables to allow people to connect to your machine. However, if you're just using your desktop as normal, you shouldn't have any need to mess around with it. Some people just feel better with Firestarter or some other firewall app running, but it's more of a security blanket than anything. The chances of your machine being compromised are very, very small.

---

### Post by klein de usa on 2007-02-25
hi 
i looked up the ip. interesting note:
OrgName:    RIPE Network Coordination Centre 
OrgID:      RIPE
Address:    P.O. Box 10096
City:       Amsterdam
StateProv:  
PostalCode: 1001EB
Country:    NL

ReferralServer: whois://whois.ripe.net:43

NetRange:   82.0.0.0 - 82.255.255.255 
CIDR:       82.0.0.0/8 
NetName:    82-RIPE
NetHandle:  NET-82-0-0-0-1
Parent:    
NetType:    Allocated to RIPE NCC
NameServer: NS-PRI.RIPE.NET
NameServer: NS3.NIC.FR
NameServer: SEC1.APNIC.NET
NameServer: SEC3.APNIC.NET
NameServer: SUNIC.SUNET.SE
NameServer: TINNIE.ARIN.NET
Comment:    These addresses have been further assigned to users in
Comment:    the RIPE NCC region. Contact information can be found in
Comment:    the RIPE database at [http://www.ripe.net/whois](http://www.ripe.net/whois)
RegDate:    2002-11-23
Updated:    2004-03-16

# ARIN WHOIS database, last updated 2007-02-24 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.


[http://www.arin.net/whois/]("http://www.arin.net/whois/")

---

### Post by skiddly on 2007-02-25
[COLOR="Blue"][SIZE="5"][/SIZE][/COLOR]Sorry for lack of knowledge but what does that mean exactly

---

### Post by klein de usa on 2007-02-25
hi 
i took the ip address you posted and searched with the link at the bottom of my last post and it gave me the internet service that has that address it was one of there users i would suspect, the internet access is in Amsterdam, realy just interesting information in less you realy get p_ssed about it and want to complain to there service provider because they can track it right back to the computer it came from sitting in an office or someones house in most cases

---

