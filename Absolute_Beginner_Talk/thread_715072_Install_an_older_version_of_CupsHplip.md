---
title: "Install an older version of Cups/Hplip"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by jbrown96 on 2008-03-04
I'm having a lot of problems printing, and I think it may have to do with the version of CUPS that I have installed. How do I move back to a previous version? I would like to try 1.12.

I have found the apt sources from Debian, but I'm not sure which packages to change. Do I only need to change Cupsys or all of the packages associated with it, including HPLIP/HPJIS?

If anyone could help with the printing problem, I would greatly appreciate it. Whenever I queue a print job, there is a delay of almost exactly 5 minutes everytime. If multiple jobs are queued, there is a 5 minute wait in between jobs. Also, about halfway through the wait a message pops up from the print queue icon stating that the printer is disconnected, although its not and the print manager seems to get over it. The printer is a HP Officejet 6310 originally connected via ethernet but the same problems persist via USB, too.

Thanks for the help

---

### Post by Oldsoldier2003 on 2008-03-04
> **jbrown96 said:**
> I'm having a lot of problems printing, and I think it may have to do with the version of CUPS that I have installed. How do I move back to a previous version? I would like to try 1.12.

I have found the apt sources from Debian, but I'm not sure which packages to change. Do I only need to change Cupsys or all of the packages associated with it, including HPLIP/HPJIS?

If anyone could help with the printing problem, I would greatly appreciate it. Whenever I queue a print job, there is a delay of almost exactly 5 minutes everytime. If multiple jobs are queued, there is a 5 minute wait in between jobs. Also, about halfway through the wait a message pops up from the print queue icon stating that the printer is disconnected, although its not and the print manager seems to get over it. The printer is a HP Officejet 6310 originally connected via ethernet but the same problems persist via USB, too.

Thanks for the help
If you want an older version than what is in the Ubuntu repositories you need to uninstall your current version the download the .debs from your preferred source and manually install them. then go into synaptic and lock the version so they wont be prompted for upgrade

---

### Post by jbrown96 on 2008-03-04
How would I go about locking them?

Would I need to change all of the CUPS packages to the same version?

Thanks

---

