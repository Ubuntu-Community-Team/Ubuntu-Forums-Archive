---
title: "Any attempt at network printing through XP locks up printer"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-10-31
I have been having alot of trouble recently attempting to print to my HP Deskjet 3845 which is hooked up to my wife's windows XP Computer. Our computers are networked successfully, and the printer setup wizard found the printer immediately and installed the driver without any problems. When i attempt to print to this printer, my Ubuntu machine says the job is complete, but my wife's computer shows an enormous print job, which cannot print, pause, or be deleted. After I try to print from my computer, the printer is locked up. Last time i attempted to print anything was monday afternoon, and the printer is still locked up from it now (early wed. morning). Even a restart of her windows XP machine will not clear the print jobs, and we need our printer back. Any advice?

---

### Post by HermanAB on 2007-10-31
Install the printer on the Ubuntu machine and manage it from a browser: [http://localhost:631](http://localhost:631)

On Windows, simply choose any postscript printer driver for this printer, since Linux CUPS makes any printer look like a postscript printer.  I always use Apple Laserwriter II, since it is at the top of the list.

---

### Post by HermanAB on 2007-10-31
See this:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/ntcmds_o.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/ntcmds_o.mspx?mfr=true)

and this:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/prnjobs.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/prnjobs.mspx?mfr=true)

Cheers,

Herman

---

### Post by brennydoogles on 2007-10-31
> **HermanAB said:**
> See this:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/ntcmds_o.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/ntcmds_o.mspx?mfr=true)

and this:
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/prnjobs.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/prnjobs.mspx?mfr=true)

Cheers,

Herman

No luck whatsoever. XP does not recognize those commands, and the driver you mentioned was nowhere to be found. Any ideas?

---

### Post by brennydoogles on 2007-11-01
::::Polite Bump::::

---

### Post by brennydoogles on 2007-11-03
:::Polite Bump:::

---

### Post by HermanAB on 2007-11-03
Have you moved the printer to Ubuntu?  That is likely the only way that you are going to make it work properly.  Linux Samba and CUPS are much better than XP print spooler.

---

