---
title: "Print Hang Ups"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by BruisedQuasar07 on 2007-10-22
After researching this problem, I've discovered it is common. 

Printer Ques or Spool failing to process a document print. So far, I've found
it happens with different brands of Printers, so it is not driver specific. My
guess is it is bug caused in Cups or somewhere beyond the driver.

I did not encounter the problem for weeks, I realize now, because I did
not reboot or turn off my printer for weeks. So far, I have narrowed the
problem to this. When Ubuntu (or Suse and other distros) reboots printing
is rebooted to the "stopped" setting.

When you investigate why your printer is reported as "ready" yet print jobs 
are not printed, in "job" box you find "stopped" at the end of reference to
the print job. 

I found no mention or solution to this common problem here. I found
several posts here about printers "not printing" but no explanation or 
solution of what the problem is. My Internet searches netted no solution but 
I found many calls for help with the problem. A few users figured out
the problem is in the auto load que commands. The printing should
be ready and paused, I guess, but it the rebooting status is "stopped".

The problem is not limited to manufacturer unsupported printers. I have
the problem with a supported HP psc 1310 series printer. But I have never 
had the problem with a simple HP Deskjet D2345 printer connected to an old
IBM Thinkpad with Xubuntu.  

I examined many 'How to' instructions about printing and found them all 
about the same -- Very short and limited to the administrator > Print> 
forward, etc instruction mantra and 'if this don't work, try manual installation 
and go to linuxPrint.org,' which does not address the print no print problem.
I found the same in the huge manuals "Beginning Ubuntu Linux and the "Linux Bible' 
2nd and 3rd Edition. Three expensive books, fellow newbies, that are extremely 
prolix (verbose) and in severe need of a professional editor. 

More Linux experienced users do not seem, thus far, to comprehend the problem. 
They tend to tell newbies they have a hardware problem and ignore them when 
they reply that their printer is fine.  My HP 1310 is also connected (by switch box, 
not network) to a Windows 2000 laptop and it works fine. 
 
Would a real Ubuntu master please permanently post the cause and 
solution to this problem? 

Thank You
--Bruised

---

