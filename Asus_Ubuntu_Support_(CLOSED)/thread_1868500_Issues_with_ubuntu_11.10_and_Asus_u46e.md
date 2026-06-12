---
title: "Issues with ubuntu 11.10 and Asus u46e"
date: 2011-10-24
forum: Asus Ubuntu Support (CLOSED)
---

### Post by djpemberton on 2011-10-24
I have recently been able to solve the first, and most serious, problem I had with my new Asus u46e and ubuntu 11.10 64-bit. The failures to boot were solved by adding "acpi=off" to the boot options. The only hardware modification I have made to the computer is the installation of a solid state hd.

Now that I have been able to spend some more time in the system, I have found a few other issues, some I consider serious, and some of which may be related.

[LIST=1]
[*]Once the screen goes to sleep I cannot fully wake it again. It "wakes" but the screen is so dark that no work can be done. It is only remedied by restarting.
[*]Suspend does not work. It looks like it will work at first, but only takes me to the login prompt.
[*]When I close the laptop lid, the screen turns off but the computer continues running at full speed otherwise.
[*]The fan stays on at full speed continually.
[*]The battery life (perhaps due to the last item?) is horrible.
[/LIST]

Otherwise, the computer is running great with Ubuntu 11.10. However, the battery life problems are significant for a laptop, and must be solved to make it worthwhile. I am searching for solutions, but would appreciate any offered here.

---

### Post by djpemberton on 2011-10-25
Removing "acpi=off" and adding "noapic" or "nolapic" (not sure what all of these actually are), solve most of these problems, while retaining the ability to boot well. The sleep and suspend problems were fixed. I gained the battery indicator back. It also solved a problem I hadn't mentioned - inability to shutdown or restart properly.

However, the fan problem seems to remain. Any boot option changes that could fix that problem as well?

---

### Post by duduklein on 2011-11-12
djpemberton,

I also have an asus u46e and I'm having problems to boot within ubuntu 11.10. 

Just for the record, I first installed ubuntu 10.04, the lts version, since I have it everywhere else. I needed to upgrade to 11.10, because I could get the wi-fi to work in the other version, however, I can say that there was no fan either boot problems there. 

I'm not an advanced user, so I'm giving you these info, since it may help you or someone else to drilldown the problem. 

I haven't been that lucky and my ubuntu is not loading at all, only windows. Is it possible to add the "noapic" option from windows? 

Thanks

---

### Post by rockanjan on 2012-01-21
I had the same issue. I upgraded my kernel to version 3.2.1. Everything works fine now.

---

### Post by vra5107 on 2012-02-21
nolapic solved my boot issues as well and I am using Asus U46E BAL7. Not sure how you guys figured that out but thanks for the post. 

Venkat

edit

Once I installed upgrades the boot problems resurfaced, kernel version was upgraded from 3.0.0-12-generic to 3.0.0-16-generic. I am not sure where @rockanjan got 3.2.1 from, I see the latest kernel version is 3.0.0-16-generic. 

nolapic boot option still works for 3.0.0.12-generic. 

Any help is appreciated. 

Thanks
Venkat

---

