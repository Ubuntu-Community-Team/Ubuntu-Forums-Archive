---
title: "[SOLVED] Thunderbird Keeps Trying to Open an IP Address in Fire/Swiftfox"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-10-23
The other day, i noticed that 2 tabs kept opening in FF. They were both trying to reach 64.40.157.85. I closed them, and a few hours later, they came back. After a lot of messing around to figure this out, I found out that opening Thunderbird is causing this. If I open Thunderbird without Firefox open, it opens swiftfox - two tabs, both going to that IP. I have been going through my emails to see if there could be some malicious spam in there, but can't find any. I did a who is through my Ubuntu Network Tools, and got this:

OrgName:    Speedfox, Inc 
OrgID:      SPEED-5
Address:    107 RR 620 South
Address:    STE 102 #E14
City:       Austin
StateProv:  TX
PostalCode: 78734
Country:    US

NetRange:   64.40.144.0 - 64.40.159.255 
CIDR:       64.40.144.0/20 
NetName:    SPEEDFOX-1
NetHandle:  NET-64-40-144-0-1
Parent:     NET-64-0-0-0-0
NetType:    Direct Assignment
NameServer: NS1.SPEEDFOX.COM
NameServer: NS2.SPEEDFOX.COM
Comment:    Fast Intelligent Web Hosting
RegDate:    2004-01-13
Updated:    2004-01-13

OrgTechHandle: TCA27-ARIN
OrgTechName:   Cansler, Trey 
OrgTechPhone:  +1-512-608-9990
OrgTechEmail:  [email]admin@websitesource.com[/email]

# ARIN WHOIS database, last updated 2007-10-22 19:10
# Enter ? for additional hints on searching ARIN's WHOIS database.





??? What gives? Speed fox is cheap webhosting, but I realize it is probably trying to send me to a site that is signed up through them. Probably some scam, but how do I get rid of it?

Thanks for any help.

---

### Post by Shazaam on 2007-10-23
Who is your ISP?

---

### Post by coldstatue on 2007-10-23
Comcast, but I've been using them for over a year, 3 weeks at this apartment, and it never happened before.

If they're doing it, can i block it?

---

### Post by coldstatue on 2007-10-23
BTW, if I boot into openSuSE on the same machine, which shares the same Thunderbird profile, it doesn't happen.

---

### Post by coldstatue on 2007-10-29
Well, i figured it out. I installed openSUSE on another partition, setting it up to share my Thunderbird profile from Ubuntu. Somehow, that installation prompted a check of updates, and the lightning plug that I had disabled in Ubuntu was reactivated. It still had some old IP for accessing my own ics files - problem is, I canceled the website over a year ago. So, there you go. Not sure why it didn't happen in SUSE, or why it was trying to hit the IP with a browser, but deleting them in lightning solved it. I didn't recognize this as my own site because I apparently purchased through a reseller. Guess I should've known the IP though.

---

