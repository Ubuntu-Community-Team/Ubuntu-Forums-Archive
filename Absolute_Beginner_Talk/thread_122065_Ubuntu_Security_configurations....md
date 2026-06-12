---
title: "Ubuntu Security configurations..."
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by confused57 on 2006-01-26
Been using Ubuntu about a month and really enjoying the experience.  You guys are the best, patient & helpful to us rookies.  I've been only taking small steps in my learning process, installing programs using synaptic and terminal and Automatix really works(Firefox 1.5 was a snap & is significantly faster).  I like OpenOffice so much, I've installed it on my XP boxes.
  My concern is with internet security using my Ubuntu box, I'm fairly savvy with security in my 2 XP pc's.  I bought a Linksys router a couple of weeks ago and have the 2 XP's and the Ubuntu box sharing an internet connection.  I installed Samba, swat, smb.conf, but chickened out trying to set up a home network due to security concerns.  I was able to access Samba using Swat via FF browser with my user "root privileges" password, but the Samba GUI would not allow any configuration changes to samba logged in this way.  I changed my actual root password, but haven't tried logging onto swat using it(security reasons).  I've since deactivated Samba in System Services.
   I was wondering what system configurations I may need to make to ensure my  Ubuntu box is secure from outside "attacks".  I make sure Firestarter is running anytime I'm logged on and I get very few hits(probes) from outside sources.  Will a home network be secure using my router with the 2 XP's and the Ubuntu box?  I mainly want to be able to share a printer within my home network.

---

### Post by Perfect Storm on 2006-01-26
Well, the ports are closed in ubuntu by default and you can configure iptables with firestarter frontend. So yes it's save. You might install anti-virus scanner on your ubuntu to scan your windows machines.

---

