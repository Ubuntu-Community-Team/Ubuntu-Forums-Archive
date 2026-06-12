---
title: "how to install printer driver and printer"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by raidard on 2007-09-02
Hello,
I want  a Canon S750 printer to work under Ubuntu 7.04.
I loaded down the recommended gutenprint driver [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S750](http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-S750)
used alien and installed it with  dpkg -i
then system-administration-printer to add the printer - it is recognized as S750, from the dropdown menu I chose a similar name (s630 or s800) as s750 is not in the list, selected a gutenprint driver from the dropdown below (did not select "install driver" as i think installation was done with dpkg -i) and continue.
If I want a testpage nothing happens and printer job status changes to "stopped".

I tried to follow the instructions on [http://www.linux-foundation.org/en/OpenPrinting/Database/DriverPackages](http://www.linux-foundation.org/en/OpenPrinting/Database/DriverPackages)
i think 7.04 is lsb 3.1 compliant and cups, foomatic-filters and ghostscrpt are contained in the distribution (are they not?)
i actually loaded down foomatic-filters and esp ghostscript but didnt know what to do with the folders after unpacking. I could not download cups.
what did i do wrong/forget?
really appreciate some advice

---

### Post by moore.bryan on 2007-09-02
> **raidard said:**
> I could not download cups.
[i]it's not called cups in the repos, it's cupsys:
```
sudo aptitude install cupsys
```[/i]

---

