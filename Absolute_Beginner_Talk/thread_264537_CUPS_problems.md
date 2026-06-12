---
title: "CUPS problems"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by topheth on 2006-09-24
I have set-up Ubuntu 6.06 on both my home Desktop and my Laptop.  After a few initial stuggles with the Laptop wireless, everything is working wonderfully.  My Laptop mounts the /home directory of the Desktop to make files available.  On my Desktop, I installed an HP812C printer by way of CUPS without problems; prints just fine.  However, when it comes to my Laptop, I cannot access my System->Administation->Printing without this error: "The CUPS server could not be contacted".  And I am at a loss.  I have read various helps on-line and in forums, but to no avail.  Being a newbie is my fault.  

I will post what files are needed if anyone could help me out here.  Thank you in advance.

---

### Post by dmizer on 2006-09-24
what is the output of:
```
grep cups /var/log/syslog
```

---

### Post by MetalMusicAddict on 2006-09-24
I think this is a known bug. I got around it by using SAMBA. Works just as well.

---

### Post by topheth on 2006-09-24
> **dmizer said:**
> what is the output of:
```
grep cups /var/log/syslog
```
 
Nothing is shown when I enter that by Terminal.  Sorry.

---

### Post by juseal on 2007-01-26
I followed this thread and it started working for me.
[http://ubuntuforums.org/showthread.p...ould+contacted](http://ubuntuforums.org/showthread.p...ould+contacted)

A condensed version is:

Remove cups

sudo apt-get remove cupsys cupsys-client

Purge cups

sudo apt-get remove --purge cupsys cupsys-client

Re-install cups

sudo apt-get install cupsys cupsys-client

I hope that helps

---

