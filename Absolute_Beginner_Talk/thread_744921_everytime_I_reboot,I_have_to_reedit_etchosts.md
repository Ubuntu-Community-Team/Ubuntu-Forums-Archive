---
title: "everytime I reboot,I have to reedit etc/hosts/"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by gverrilla on 2008-04-04
I had that
unable to resolve host Luther(me)
problem at the terminal
and I found out I could bypass it through the gksudo gedit  /etc/hosts command,by changing the Luther.WORKGROUP name to Luther only.
the first problem is everytime I reboot I have to go through the same process again : it seems as the saves were lost
the other problem is that when using gksudo gedit  /etc/hosts,sometimes it just wont work..then I close the terminal,and try again,and it works(asking my passworD)


any ideas?
cheers

---

### Post by gverrilla on 2008-04-04
some other stuff seem not to be working properly
and the problems comes with the Starting Administrative Application
what should that be ?
cheers

---

### Post by mikeyphi on 2008-04-04
Open System/Administration/Network
select the Hosts tab
1st line -aliases-should read localhost
2nd line -aliases- should read Luther

If not, highlight that line and select properties - then amend the name, check OK and close

---

### Post by gverrilla on 2008-04-04
this doesn't work with me
when I close the network settings and reopen it,the ".WORKGROUP" is still there

---

### Post by gverrilla on 2008-04-04
?

---

### Post by bubba_169 on 2008-04-04
Just checking, you have installed ubuntu and not just running the livecd?

---

### Post by gverrilla on 2008-04-04
for sure

---

### Post by Barton101 on 2008-04-06
I am having a similar issue; cannot set the work group.  

I have XP and Ubuntu computers at home (2 of each right now- - soon to 3/1).  

My home domain/workgroup is BARTONWEB.   I enter this the computer name into the "Host Name" field and the workgroup into the "Domain Name" field. 

 I re-boot and the comptuer name is updated, but the Domain Name field is blank.  The XP computers can see the name change, but they see the Ubuntu computer as being in the WORKGROUP domain.

Cheers Andrew

---

