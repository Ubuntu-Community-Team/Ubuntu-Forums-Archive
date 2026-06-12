---
title: "how do you go back to previous kernel?"
date: 2005-01-06
forum: Apple PPC Users
---

### Post by tiiim on 2005-01-06
i installed the test ppc kernel that puts ur ibook to sleep works great. However when i load i get a few error msgs which im not happy about. So i think i wait to the official release of the PPC version so how do i remove the current kernel and go back to the previous one i had?

---

### Post by tiiim on 2005-01-06
[QUOTE=tiiim]i installed the test ppc kernel that puts ur ibook to sleep works great. However when i load i get a few error msgs which im not happy about. So i think i wait to the official release of the PPC version so how do i remove the current kernel and go back to the previous one i had?[/QUOTE]
 ps if i have to download could you tell me the ubuntu ppc image address cos my SPM got probs over my uni network. unless of cause someone wants to sort out my start error msgs...

---

### Post by kezz on 2005-01-06
The old kernel shows up in yaboot under old (on mine anyway) so just type old at the yaboot prompt to test this. If it works just edit yaboot.conf and reload the bootloader to make the changes permanent.

---

### Post by jbh on 2005-01-06
doesn't sudo apt-get remove (kernel name) --purge work? that will nuke whatever u installed.

---

### Post by tiiim on 2005-01-06
[QUOTE=jbh]doesn't sudo apt-get remove (kernel name) --purge work? that will nuke whatever u installed.[/QUOTE]
 well i alreay just removed it under SPM before all that was written....

if i upgrade to a new kernel in future will that fix the links? if not how do i create the links. when i removed it under SPM it said i needed to run yaboot.

---

### Post by tiiim on 2005-01-06
[QUOTE=tiiim]well i alreay just removed it under SPM before all that was written....

if i upgrade to a new kernel in future will that fix the links? if not how do i create the links. when i removed it under SPM it said i needed to run yaboot.[/QUOTE]
 if not do i install the other kernel again then sudo <kernel> --purge? but that may cause more probs now. At moment i only have the links to the .old kernel files which i have edited under yaboot.conf to run them instead for the time being.

---

