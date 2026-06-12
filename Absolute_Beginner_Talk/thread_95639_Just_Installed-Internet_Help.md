---
title: "Just Installed-Internet Help"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by mattz0r1014 on 2005-11-27
I have just succesfully ran ubuntu live cd on my computer.. its so cool! ive been in windows all my life.. = \. well i loaded it and explored for awhile  and i saw theres Firefox in there and i run firefox on windows and i opened it and tried to connect to a site and it acted like i wasnt connected to the internet.. well i looked in like Network Options and all the internet/network typed stuff and it all seemed to be working (that i could see)but no internet apparently because no sites would run.. i tried many.. could someone please help me with getting internet to run?? no i am not wireless.. im thru a lan and i tried to insert the floppy that came with my network card but it wouldnt read that for some reason.. please help i run thru a lan if thats any help

---

### Post by 23meg on 2005-11-27
What's the brand and model of your network card? It may not be supported by default. Do you see an ethernet connection listed in System / Administration / Networking? 

If you don't know what brand/model it is, you may find it listed in System / Administration / Device Manager.

---

### Post by cwaldbieser on 2005-11-27
[QUOTE=mattz0r1014]I have just succesfully ran ubuntu live cd on my computer.. its so cool! ive been in windows all my life.. = \. well i loaded it and explored for awhile  and i saw theres Firefox in there and i run firefox on windows and i opened it and tried to connect to a site and it acted like i wasnt connected to the internet.. well i looked in like Network Options and all the internet/network typed stuff and it all seemed to be working (that i could see)but no internet apparently because no sites would run.. i tried many.. could someone please help me with getting internet to run?? no i am not wireless.. im thru a lan and i tried to insert the floppy that came with my network card but it wouldnt read that for some reason.. please help i run thru a lan if thats any help[/QUOTE]

Open a terminal and type:
```

$ ifconfig
$ route

```
post the results back here.  They will tell us if your network card was assigned an IP address, and if your routing table is set up to point to your gateway.

---

