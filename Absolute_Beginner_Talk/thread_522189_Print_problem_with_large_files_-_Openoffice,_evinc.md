---
title: "Print problem with large files - Openoffice, evince, lpr"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by LJ97 on 2007-08-10
Hello, Ubuntu newbie here:

I've just installed the 64-bit version of Feisty onto my desktop PC.

I installed the printer (Samsung ML-1610) by:
System -> Administration -> Printing

It's a Local printer attached to by PC by USB
=> I can select the SAMSUNG ML-1610 USB #1 detected, default gdi driver & can successfully install the printer.

It can print webpages & some pdf files fairly happily.

The problem seems to be that it is unable to print more than 1-2 pages of large files of any format (.pdf, .ps, .doc). 

I've tried using:
Open office - red light indicating error flashes on printer
Acroread (32-bit version installed using Automatix) - red light
kpdf - red light
lpr - red light
lp (on .ps) red light & "/usr/lib/cups/filter/foomatic-rip failed" 
Now won't print anything.

My /etc/cups/printers.conf looks like this:

# Printer configuration file for CUPS v1.2.11
# Written by cupsd on 2007-08-10 13:43
<Printer ML-1610>
Info Office
Location Under my desk!
DeviceURI usb://Samsung/ML-1610
State Idle
StateTime 1186749799
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job

My /var/log/cups/error_log has the following 
PID 9732 (/usr/lib/cups/backend/socket) crashed on signal 9!

& then it repeats (for the next 6000 lines):

cupsdAuthorize: Local authentication certificate not found! 

I tried to follow the instructions in Bug #112803 (May 2007) & install the latest version of CUPS: cupsys_1.2.11-2ubuntu2.dsc
but this hasn't solved anything & may be a red herring.

So I now have no idea what to do 
& I don't really understand about all this cups stuff & don't really want to have to do any messy pseudo 32-bit fixes.

I briefly installed the 32-bit version of Feisty which seemed to have fewer printing problems
- so is this a 64-bit problem?

If anyone has any ideas on how to fix it  would be extremely grateful.

LJ

---

### Post by Hospadar on 2007-08-10
Well yeah I would say first try the 32 bit version, in general It will be less buggy.  It might be the case also that your printer doesn't have a lot of memory, but that seems unlikely as you've probably printed stuff before with it.

---

### Post by LJ97 on 2007-08-10
Don't want to go back to 32-bit because the codes that I run will be much quicker on 64-bit. 

Since printing seems to be pretty fundamental I was hoping that there was a solution out there - but maybe you're right & I will just have to learn to print a few pages at a time. Sigh.

---

