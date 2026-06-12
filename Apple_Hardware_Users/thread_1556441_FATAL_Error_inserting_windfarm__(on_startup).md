---
title: "FATAL: Error inserting windfarm  (on startup) ???"
date: 2010-08-19
forum: Apple Hardware Users
---

### Post by 828688 Ben on 2010-08-19
[IMG]http://lh5.ggpht.com/_FI33gwIVx5s/TG1eqOrDv0I/AAAAAAAAAYo/vipixVxYLAQ/1.png[/IMG]
I get this fatal error every time I start up Ubuntu 10.04 LTS on my Dual 2.0 GHz PowerPC G5 Mac.
I am able to successfully start up and login into ubuntu, but I was wondering how can I fix this Fatal Error that I get on start up.


Thanks,
Ben

---

### Post by linuxopjemac on 2010-08-19
I would add:
```
windfarm_core
```

to /etc/modules

---

### Post by sha.goyjo on 2010-08-20
> **linuxopjemac said:**
> I would add:
```
windfarm_core
```

to /etc/modules

Yeah, you should try using a livecd and seeing if this works. Also, try using a debian livecd and using modconf, which will actually change the init to insmod windfarm at an earlier time.

If that doesn't work, it means something is borked about the module or.........insmod itself? the latter doesn't seem bloody likely.

---

### Post by slow photon on 2011-02-22
> **linuxopjemac said:**
> I would add:
```
windfarm_core
```

to /etc/modules

I tried this and the error remained on a restart. Any other ideas?

---

### Post by TODDMAN on 2011-09-15
> **linuxopjemac said:**
> I would add:
```
windfarm_core
```to /etc/modules
How do you do this? I tried using the text editor & it wouldn't save it in /etc/modules.

Thanks,

---

### Post by TODDMAN on 2011-09-15
> **TODDMAN said:**
> How do you do this? I tried using the text editor & it wouldn't save it in /etc/modules.

Thanks,
Never mind I installed NScripts.
[http://gtk-apps.org/content/show.php/NScripts?content=67655](http://gtk-apps.org/content/show.php/NScripts?content=67655) 

Thanks,

---

### Post by murdok186 on 2012-04-13
Ok here is the solution for my iMac G5 mac, none of the suggestions on the internet even came close!! And I am basically a noob!!  You will need to install modconf first, and then launch it.

1) Go to kernel/drivers/macintosh and hit enter
2) Go to windfarm_pm121 (which probably has a "-" next to it...) and hit enter to install the module


Done... At least it was that easy for me, hope this helps!!

---

