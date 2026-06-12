---
title: "CD Image Creation Error"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-11-30
Hi,

OK, I have a Windows XP setup CD. I want to create an ISO so I can install XP on a partition I've created. I'm using GnomeBreaker but when I select the option to create an image from a disk I get the following error message:
[B]
readcd: Permission denied. Cannot open '/dev/sg0'. Cannot open or use SCSI driver.
readcd: For possible targets try 'readcd -scanbus'. Make sure you are root.
readcd: For possible transport specifiers try 'readcd dev=help'.[/B]

Anyone know what's wrong?

CosmicFlux

---

### Post by quandary on 2007-11-30
> **CosmicFlux said:**
> 
 Make sure you are root.
CosmicFlux

Make sure you are root. either use sudo or su
or probably better:
login as root

---

