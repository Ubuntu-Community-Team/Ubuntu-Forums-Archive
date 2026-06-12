---
title: "Problems printing to network printer - Brother MFC-8860DN"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by jrjazzman on 2006-10-04
I'm having trouble printing to a network printer.  The printer is a Brother MFC-8860DN.  I installed Brother's lpr driver and then the cups wrapper driver.  For printer type, I chose CUPS with a URI of ipp://10.1.10.75 (the printer's IP).  Any attempt to print fails, and the printer properties window shows Status: Paused: /usr/lib/cups/backend/ipp failed.  

/var/log/cups/error_log has the following:

E [04/Oct/2006:16:10:09 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [04/Oct/2006:16:10:18 -0500] [Job 3] Print file was not accepted (client-error-bad-request)!


I'm not very familiar with linux printing, so I'm not really sure where to go from here.  Any help would be greatly appreciated.

Thanks

---

### Post by skyjuice on 2007-10-10
i also faced a same problem i already refer a few tutorial in here but not work T_T any tutorial for network printing for this brothers model will really appreciate

---

### Post by jloveless on 2008-04-15
> **jrjazzman said:**
> I'm having trouble printing to a network printer.  The printer is a Brother MFC-8860DN.  I installed Brother's lpr driver and then the cups wrapper driver.  For printer type, I chose CUPS with a URI of ipp://10.1.10.75 (the printer's IP).  Any attempt to print fails, and the printer properties window shows Status: Paused: /usr/lib/cups/backend/ipp failed.  

/var/log/cups/error_log has the following:

E [04/Oct/2006:16:10:09 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [04/Oct/2006:16:10:18 -0500] [Job 3] Print file was not accepted (client-error-bad-request)!


I'm not very familiar with linux printing, so I'm not really sure where to go from here.  Any help would be greatly appreciated.

Thanks
================
Did you ever get this combo working? I now have an MFC8660DN and you could probably save me a let of grief and heartache  ;-)

---

