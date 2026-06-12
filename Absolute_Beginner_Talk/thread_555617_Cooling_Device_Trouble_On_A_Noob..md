---
title: "Cooling Device Trouble On A Noob."
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by n00b-e on 2007-09-20
Kernel: ACPI: Unable to turn cooling device [df807dec] 'on'

:confused:

Maybe this could be the reason why my computer will get very laggy and freeze after a while? anyways if its not the reason , that message just spams up my logs every few seconds. Help please? There really isent much success in reading other peoples forums about it...got no use out of it. Thanks!

Keep in mind im a noob-e , and i want to get rid of it quick , and i work alot , so if you can post suggestions rather quickly , I would really appreciate it!

---

### Post by energiya on 2007-09-20
It seems to be a bug. See here [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63550)

**BUT**
You say your PC freezes?!? This is usualy due to CPU temeprature.
First check if you fans are working and keep an eye on your CPU/motherboard temperatures. Could you please post the output of
> 
lsmod | grep thermal
lsmod | grep fan
 and maybe CPU type?
It would also be a good ideea to install some kind of app to check temperatures.

---

