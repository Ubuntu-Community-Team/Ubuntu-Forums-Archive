---
title: "Java and OpenOffice on a PowerPC G4"
date: 2009-03-18
forum: Apple Hardware Users
---

### Post by icorbyn on 2009-03-18
I'm new to the forum and Ubuntu, so I apologise if this question has been asked before (I did look).

I installed 8.04 desktop on a PowerPC G4, and everything is dandy, except OpenOffice can't find a Java JRE, so the wizards don't work.  I did find this bug report

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/250825](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/250825)

which I think says Java on the PowerPC distribution was broken, but is now (2009-03-10) fixed, at least for the Jaunty version.  How can I incorporate this fix into 8.04?  Please don't say 'wait for Jaunty', as I have persuaded a local non-profit to try Ubuntu  for their office workstations, and one attraction was the LTS status of 8.04.

Thanks.

---

### Post by cyberdork33 on 2009-03-18
> **icorbyn said:**
> I'm new to the forum and Ubuntu, so I apologise if this question has been asked before (I did look).

I installed 8.04 desktop on a PowerPC G4, and everything is dandy, except OpenOffice can't find a Java JRE, so the wizards don't work.  I did find this bug report

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/250825](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/250825)

which I think says Java on the PowerPC distribution was broken, but is now (2009-03-10) fixed, at least for the Jaunty version.  How can I incorporate this fix into 8.04?  Please don't say 'wait for Jaunty', as I have persuaded a local non-profit to try Ubuntu  for their office workstations, and one attraction was the LTS status of 8.04.

Thanks.
From reading the bug, the problem appears to be the fact that OpenOffice was built without the Java stuff for PowerPC. It has not been built with it until the version that is now in Jaunty... therefore, really the only way to get the fixed version would be to get the jaunty version (for now). I would also request a backport to 8.04 for PowerPC in that bug report.

---

### Post by icorbyn on 2009-03-19
Thanks for confirming my take on the bug report.  
I want to keep to a standard 8.04 install, standard repositories etc., so how do I "request a backport to 8.04 for PowerPC"??

---

### Post by albandy on 2009-03-19
if you can specify the JVM  you can use the IBM java machine, it supports powerpc architecture

---

### Post by icorbyn on 2009-03-19
"if you can specify the JVM you can use the IBM java machine, it supports powerpc architecture "

I can't find a way to specify a JRE for OpenOffice, it's supposed to find one.  I think the problem is with the OpenOffice build, not with a JRE for PPC.

---

### Post by albandy on 2009-03-19
Hope this could help you, see the screenshot attached

---

### Post by cyberdork33 on 2009-03-19
> **icorbyn said:**
> I think the problem is with the OpenOffice build, not with a JRE for PPC.
that is correct.

Go to that bug report and state that a fix needs to be backported to Gutsy (8.04). Of course, it might even be there already, check if the backports repository is enabled in your sources.list.

---

