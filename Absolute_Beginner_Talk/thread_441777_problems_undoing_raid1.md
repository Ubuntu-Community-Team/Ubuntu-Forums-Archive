---
title: "problems undoing raid1"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by superwazn on 2007-05-12
hi. sorry, this problem isnt really about ubuntu, but this is the only forums i know where people are friendly or anywhere near helpful. i have a raid1 setup between 2 drives (with windows on them, unfortunately) and wanted to be able to un-raid them so i can use one of the drives for an ubuntu install while keeping the other one with windows to keep my mom happy. my problem is that when i disable the raid setup in BIOS, neither of the windows drives can boot properly. they get to that part with the loading bar then the screen flashes an error message that you cant read and reboots. i really need to sort this out before i put ubuntu on one of the drives since my mom already flipped out when she saw me using a liveCD and thought her "precious" windows was gone.:-({|= 
does anyone know what could make it break just because i turned off the raid setup? any help would be greatly appreciated! thanks

---

### Post by superwazn on 2007-05-13
c'mon, no one knows whats up with this? this is the only thing stopping me from installing ubuntu right now.

---

### Post by psusi on 2007-05-14
What is the contents of your c:\boot.ini file?  I think the problem is that windows was configured to boot from the promise fake raid driver, but now that you disabled the raid support, it can't do that.  You will need to tell windows to boot from a normal ide disk.

---

