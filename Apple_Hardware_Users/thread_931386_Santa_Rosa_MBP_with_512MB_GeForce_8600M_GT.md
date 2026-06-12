---
title: "Santa Rosa MBP with 512MB GeForce 8600M GT??"
date: 2008-09-27
forum: Apple Hardware Users
---

### Post by lv1001 on 2008-09-27
Hi,

NVIDIA X Server Settings shows the following information in the section "GPU 0 - (GeForce 8600M GT)":

Graphics Processor: GeForce 8600M GT
VBIOS Version: 60.84.49.03.00
Memory: 512 MB
Bus Type: ...
.
.
.

While the memory should only be 128 MB for my Macbook Pro (Santa Rosa 15.4, the cheaper one).
The best Santa Rost MBP should have 256 MB of graphic memory AFAICS.

I guess this output is wrong. Do I have to worry about this? No further problems have occurred so far.
Is this known?

Thanks
  LV

---

### Post by cyberdork33 on 2008-09-27
I would actually trust that output more! Maybe you just got lucky and got the higher RAM.

Do you get the same information in OS X in System Profiler?

---

### Post by lv1001 on 2008-09-27
I just checked back and MacOS reports 128MB as expected.
Is there any other way to be sure?

Thanks,
  LV

---

### Post by cyberdork33 on 2008-09-27
> **lv1001 said:**
> I just checked back and MacOS reports 128MB as expected.
Is there any other way to be sure?
Well, I am sure that OS X reports the correct value.

I would file a bug report. Is it part of an Nvidia tool that gave that information?

---

### Post by lv1001 on 2008-09-27
The informations listed above are from the program "NVIDIA X Server Settings" (/usr/bin/nvidia-settings from the universe-package "nvidia-settings".
I did not try to install the latest nvidia-driver yet to see what it reports.

Are there other ways to be ultimately sure?

Thanks
  LV

---

### Post by Saeonate on 2008-09-30
wow what do you know.  mine also reports 512MB ram using nvidia's latest beta drivers.  I think I have 128 as well - SantaRosa MBP w/the 8600M ... I wonder if this is causing some of the many display problems I have !

---

### Post by cyberdork33 on 2008-09-30
this may be a bug that needs to be reported to nvidia.

---

### Post by Greettat on 2008-10-01
if you wish to be the best man, you must suffer the bitterest of the bitter.-------------------------[evening dresses](http://www.china-stylish.com/Evening-Gown.html), [evening gowns](http://www.china-stylish.com/Evening-Gown.html), [wedding dresses](http://www.china-stylish.com/Wedding-Dress.html), [bridal gowns](http://www.china-stylish.com/Wedding-Dress.html), [wedding gowns](http://www.china-stylish.com/Wedding-Dress.html)

---

### Post by nid3 on 2008-10-03
hi 
I have problem with GF 8600M gt.
When i run compiz fusion my Ubuntu (i've tested 7.10 and 8.04) my  computer slows. Aplications starts slower.what i'd do to elimate the problem?

---

