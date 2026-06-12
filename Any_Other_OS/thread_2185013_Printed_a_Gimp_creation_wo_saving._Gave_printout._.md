---
title: "Printed a Gimp creation w/o saving. Gave printout. How can I retrieve digital copy?"
date: 2013-10-31
forum: Any Other OS
---

### Post by akoubu.9a on 2013-10-31
I printed something from Gimp to my HP laserjet printer. I did not save a file. I just printed to my printer. I no longer have the printout with me. How can I review a copy of the Gimp file that I printed out. On my Windows 8 computer, are the most recently printed stuff saved somewhere? 
Or is there a hidden cache of stuff I've done on Gimp, even if I haven't saved to Gimp?

---

### Post by tgalati4 on 2013-10-31
You might have some files in:  /var/spool/cups-pdf/SPOOL

But the files will only reside there if a printer is down, for later respooling.  There is a setting in CUPS to keep a copy of print jobs, but it is turned off by default.  Only print jobs that don't complete successfully are kept for later respooling.

Open *gimp* and look in "Open Recent".

---

### Post by akoubu.9a on 2013-11-01
tgalati4,
Is your advice for Windows 8? I tagged my thread "Windows"

---

