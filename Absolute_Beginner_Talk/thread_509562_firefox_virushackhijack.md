---
title: "firefox virus/hack/hijack"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by enduser on 2007-07-25
[https://fivestar.izap.com/cgi-bin/status.py](https://fivestar.izap.com/cgi-bin/status.py)                       keeps hijacking my google.

I do have admin passwords on so i'm guessing this is just a browser hack.

I use firefox.

totally new to ubuntu so i dont know how to toubleshoot in the slightest.

---

### Post by asmoore82 on 2007-07-25
create a new, clean profile to use in firefox:

close all browser windows, open a terminal and...

```
~ $ killall firefox
~ $ firefox -ProfileManager
```

-OR-
_NUKE_ your entire firefox config, (you will permanently lose settings/bookmarks)
```
~ $ /bin/rm -r ~/.firefox
```

---

### Post by Daveth on 2007-07-25
since neither I or anyone will risk visiting this website then, what exactly does it do to google?

---

### Post by sad_iq on 2007-07-25
Hmm...the page seems to be down...so...can't test...also I don't use firefox, but I do have it installed...the only advice i have ...make sure you run an updated system...and in firefox make sure you use noscript and other security addons there are (**Firefox->Tools->Add-ons** and look for ->Noscript)

---

### Post by st33med on 2007-07-25
I think I have heard of this. It maybe a Java exploit in Firefox that takes all the passwords stored in Firefox.

[SIZE="5"]Advice to all that read this: DON'T GO ON THE LINK PROVIDED.[/SIZE]

Also noted is that the link involves a python script (notice the .py at the end of the link). It also maybe something I have no idea about.

---

### Post by rickycodie on 2007-07-25
try using opera

sudo apt-get install opera

---

### Post by st33med on 2007-07-25
Actually, the link is supposed to end in .pay.

---

### Post by Seisen on 2007-07-25
> **st33med said:**
> Actually, the link is supposed to end in .pay.

Then it wouldn't be a python script.

---

### Post by Seisen on 2007-07-25
> **enduser said:**
> [https://fivestar.izap.com/cgi-bin/status.py](https://fivestar.izap.com/cgi-bin/status.py)                       keeps hijacking my google.

I do have admin passwords on so i'm guessing this is just a browser hack.

I use firefox.

totally new to ubuntu so i dont know how to toubleshoot in the slightest.

If it has anything to do with javascript exploits install noscript extension

---

### Post by ted9k on 2007-07-25
fivestar.izap.com resolves to 192.168.107.1 ?

i believe that means it's something on an internal network

---

### Post by r4ik on 2007-07-25
Here's a whois if anybody can use it be my guest.

OrgName:    Internet Assigned Numbers Authority
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   192.168.0.0 - 192.168.255.255
CIDR:       192.168.0.0/16
NetName:    IANA-CBLK1
NetHandle:  NET-192-168-0-0-1
Parent:     NET-192-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    This block is reserved for special purposes.
Comment:    Please see RFC 1918 for additional information.
Comment:
RegDate:    1994-03-15
Updated:    2002-09-16

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

---

