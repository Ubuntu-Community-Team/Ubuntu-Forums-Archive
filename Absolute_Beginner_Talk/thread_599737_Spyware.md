---
title: "Spyware"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by jordank on 2007-11-01
What steps should i be taking against spyware/adware on my ubuntu box?
I know windows has adaware/spybot S&D, is there something equivelent to that on ubuntu? just to give my system a good clean?
Also, for viruses, is there a free program, similar to AVG that i can run tests with now and then?

---

### Post by shad0w_walker on 2007-11-01
You really shouldn't need to worry about virus/spyware on Linux. The design of everything makes it much harder for anything to get onto your system with out permission.

---

### Post by Jittoku on 2007-11-01
The Ubuntu repository contains ClamAV (antivirus) and Firestarter (firewall), though as ShadowWalker said, your exposure on the web is quite low.  I ran Red Hat on a laptop for 2 years on the web with no AV or firewall, and never noticed any performance degradation - I suppose there could be something on there, but it would have to be benign.  Ubuntu appears to be even more "hardened".

---

### Post by nc_jed on 2007-11-01
Virus:  
ClamAV is also a contender.  [http://en.wikipedia.org/wiki/ClamAV](http://en.wikipedia.org/wiki/ClamAV)
As is PandaAV.  [http://www.pandasoftware.com/download/linux/linux.asp](http://www.pandasoftware.com/download/linux/linux.asp)

Additionally an article on the subject:  [http://www.linux.com/articles/60208](http://www.linux.com/articles/60208)

Spyware:
Linux is less of a fishing expedition than Windows, but I did get dinged once by package that installed itself to a directory named ' ' (that is one space).  Inside this dir, there were several files including a list of "common" passwords/usernames etc and scripts that try all of them.  This was probably due more to improperly configured ports/services, etc than clicking on suspect email attachments.  P.S.  I checked and found my username was on the list, but not my password, phew.

Regards.


> **jordank said:**
> What steps should i be taking against spyware/adware on my ubuntu box?
I know windows has adaware/spybot S&D, is there something equivelent to that on ubuntu? just to give my system a good clean?
Also, for viruses, is there a free program, similar to AVG that i can run tests with now and then?

---

### Post by bodhi.zazen on 2007-11-01
Spyware is rare in Linux, but it is possible. One potential is your browser (java).

See this link for some suggestions : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by BrendanM on 2007-11-01
ClamAV is quite good, there is also a free (as in beer) version of AVG available for Linux. I've never used it myself.

But yeah, spyware/viruses are almost a non-issue on Linux. I only run AV software to avoid passing things on to Windows machines.

---

### Post by feisty on 2007-11-01
how to install AVG ...written by Artificial Intelligence  	

[http://ubuntuforums.org/showthread.php?t=136064&highlight=avg+antivirus](http://ubuntuforums.org/showthread.php?t=136064&highlight=avg+antivirus)

---

