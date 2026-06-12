---
title: "[SOLVED] Printing problem - Stopped: Job-stopped also status 22 in error log"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-08-08
Here is the cups error log.

E [08/Aug/2007:11:58:55 +0100] PID 6291 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [08/Aug/2007:12:12:54 +0100] PID 6810 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [08/Aug/2007:12:16:50 +0100] Filter "/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0" for printer "Stylus-Photo-R200" not available: No such file or directory
E [08/Aug/2007:12:16:50 +0100] Filter "/opt/gutenprint/cups/lib/filter/commandtoepson" for printer "Stylus-Photo-R200" not available: No such file or directory
E [08/Aug/2007:12:16:51 +0100] Filter "/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0" for printer "Stylus-Photo-R200" not available: No such file or directory
E [08/Aug/2007:12:16:51 +0100] Filter "/opt/gutenprint/cups/lib/filter/commandtoepson" for printer "Stylus-Photo-R200" not available: No such file or directory
E [08/Aug/2007:12:20:25 +0100] CUPS-Delete-Printer: Unauthorized
E [08/Aug/2007:12:31:55 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [08/Aug/2007:12:32:14 +0100] PID 7732 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [08/Aug/2007:12:38:43 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [08/Aug/2007:12:39:33 +0100] PID 8185 (/usr/lib/cups/filter/rastertogutenprint.5.0) stopped with status 22!
E [08/Aug/2007:12:39:46 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:39:46 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:39:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:39:51 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:39:56 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:39:56 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:40:01 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:40:01 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:40:06 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:40:06 +0100] cupsdAuthorize: Local authentication certificate not found!
E [08/Aug/2007:12:46:52 +0100] PID 8442 (/usr/lib/cups/filter/rastertogutenprint.5.0) stopped with status 22!
E [08/Aug/2007:12:55:53 +0100] CUPS-Delete-Printer: Unauthorized
E [08/Aug/2007:12:57:39 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [08/Aug/2007:12:57:58 +0100] PID 8902 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!
E [08/Aug/2007:13:02:32 +0100] PID 9240 (/opt/gutenprint/cups/lib/filter/rastertogutenprint.5.0) stopped with status 22!

Thanks in advance

---

### Post by jnorthr on 2007-08-08
Phil - can you take a look at this : [http://ubuntuforums.org/showthread.php?t=245124](http://ubuntuforums.org/showthread.php?t=245124)
sure looks like a permissions problem - not authorised and all that.

---

### Post by jnorthr on 2007-08-08
Dunno if this will help: [http://home.swbell.net/berzerke/printing.html](http://home.swbell.net/berzerke/printing.html)

---

### Post by philinux on 2007-08-08
From poking on google the Solution was

sudo aptitude purge gs-esp
sudo aptitude install cupsys cupsys-driver-gutenprint foomatic-db-gutenprint foomatic-filters fontconfig libtiff4 libfreetype6 gs-esp

## evince pdf viewer also gets purged so needed to re-install from spm.

Havn't a clue what gs-esp is though but I'm back printing. Although Mtink wont work anymore even though I've completely removed it and re-installed.

---

### Post by jnorthr on 2007-08-12
Phil -
Here's your link to the GS (ghost script) doc.s [http://packages.ubuntu.com/dapper/text/gs-esp](http://packages.ubuntu.com/dapper/text/gs-esp) Ghost script is the logic to construct post script documents for printers and [http://packages.ubuntu.com/edgy/misc/mtink](http://packages.ubuntu.com/edgy/misc/mtink) is Mtink is a status monitor which allow to get the remaining ink quantity, printing of test patterns, changing and cleaning cartridges. Do you have an epson salts printer ?:rolleyes:

---

