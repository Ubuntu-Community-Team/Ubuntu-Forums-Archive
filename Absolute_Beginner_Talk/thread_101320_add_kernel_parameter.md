---
title: "add kernel parameter ?"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by widjajayd on 2005-12-09
I am setup VGA SiS 630 with Dri
how I can add the kernel parameter 

"video=sisfb:mode:1024x768x16.." 
I am using grub not lilo

Thanks.

---

### Post by ssam on 2005-12-09
to do it as a one off at boot time, you press 'E' to Edit the boot line, make you changes, then press enter, and B to Boot.

to make it perminent make changes to the file
```
/boot/grub/menu.lst
```
(read all the comments in the file for clues).

if your not sure how to do this, or need further help, just ask :-)

---

### Post by widjajayd on 2005-12-10
thanks,

I try to enable DRI on my SIS 630 / 740 
I have Sis 630 onboard in ASUS TUSI-M motherboard.
it said from [www.winischhofer.net](www.winischhofer.net) it can work with dri
but I'been working 48 hours (slept 4 hour to solve but still no result).
I have recompile my kernel, activate sisfb but no good result

if anyone have same experience installing this device 
please help

thanks before

---

