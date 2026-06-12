---
title: "Is this a problem - chkrootkit Result"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Healey on 2006-01-04
Hi

I ran chkrootkit and noticed this :

Checking `lkm'... You have     1 process hidden for readdir command
You have     1 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
Checking `rexedcs'... not found

I did not know what to do so I ran chkrootkit again and it now says nothing detected - I got this:

Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[7192])

I use Breezy 5.10 if it makes any difference

Am I ok ????

Regards

Healey

---

### Post by bluefrog on 2006-01-04
download and run rkhunter from rootkit.nl and make a check.

i had what i consider (so far, think there were processes a bit slow to disappear - if it's possible) as a false positive on lkm but in your case it's talking about a packet sniffer.
so double check with rkhunter.

james

further googling says that packet sniffer  could be "normal" as well..

---

### Post by Healey on 2006-01-04
Hi

Thanks for the reply

Yes - I have run rkhunter and all is ok - In fact I did that first

I have also tried chkrootkit again and no problems reported !!

I just want to be safe rather than sorry !!

Thanks for your help

Healey

---

