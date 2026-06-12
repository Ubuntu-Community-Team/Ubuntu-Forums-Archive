---
title: "ibook g3 500 sleep"
date: 2006-01-27
forum: Apple PPC Users
---

### Post by sonofcolin on 2006-01-27
I've read in the ppc WIKi that sleep doesn't work on ibook g3 500 (I can confirm this!!). The WIKI states that there are fixes in the forum. I can't find any :(  Can someone 'enlighten' me please?!

---

### Post by Ptero-4 on 2006-01-28
Yes. Sleep won't work on those iBooks b/c they got a dodgy videocard. The solution is to disable dbus/hald b4 going to sleep and reenabling them after resuming. I can't recall how to automate that.

---

### Post by sonofcolin on 2006-01-28
[QUOTE=Ptero-4]Yes. Sleep won't work on those iBooks b/c they got a dodgy videocard. The solution is to disable dbus/hald b4 going to sleep and reenabling them after resuming. I can't recall how to automate that.[/QUOTE]

Thanks for the tip. Can I just kill the dbus process or should I find a more 'gentle' solution?

---

### Post by Ptero-4 on 2006-01-29
There's a more 'gentle' trick which involves stopping the optical drive polling (the problem is that when you resume the laptop, the power management daemon tries to check the optical drive to see if there's a cd in it but for some odd reason this puts the power management daemon in an infinite loop stopping the resume procedure dead and leaving the machine useless). But it have the nasty side effect that the MacOS-like automount won't work anymore and you'll have to mount and unmount the drive manually like in the old (prior to the kernel 2.4) days.

---

### Post by sonofcolin on 2006-01-29
[QUOTE=Ptero-4]But it have the nasty side effect that the MacOS-like automount won't work anymore and you'll have to mount and unmount the drive manually like in the old (prior to the kernel 2.4) days.[/QUOTE]

I can live with mounting and unmounting volumes manually, it's the sleep functionality that is more important.

How do I change the settings to achieve this?

---

### Post by lucaramel on 2006-02-02
I've recompiled the Ubuntu kernel with the ide patch to make sleep work again. You can find it at [http://brebis.org/truc/linux/](http://brebis.org/truc/linux/) . It's the exact same kernel. Hope it helps.

---

### Post by sonofcolin on 2006-02-02
[QUOTE=lucaramel]I've recompiled the Ubuntu kernel with the ide patch to make sleep work again. You can find it at [http://brebis.org/truc/linux/](http://brebis.org/truc/linux/) . It's the exact same kernel. Hope it helps.[/QUOTE]

Thanks! I'll give it a shot.

---

### Post by sikity on 2006-02-12
Thanks for the patched kernel.  That fixed my resume from sleep issues.

---

### Post by scottlpatterson on 2006-02-14
The sleep issue has been resolved with kernel 2.6.15 in Dapper Flight 3:

[https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz]("https://wiki.ubuntu.com/LaptopTestingTeam/Apple_iBookG3_12in_600Mhz")

---

