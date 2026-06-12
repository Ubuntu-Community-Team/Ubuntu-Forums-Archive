---
title: "Modprobe issues"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Picatta on 2008-01-28
So, I'm trying to install cpu temp sensors and find a way to change my fan s[eed (computer seems too hot and fans are hardly on..).  Anyway, I installed the appropriate packages, and did sensors-detect.  That went well, and it said I was supposed to add two kernel modules, k8temp and it87.  I added them to the file it said to, and then I tried to modprobe them, k8temp worked fine, but the other gave me this:

# modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/it87.ko): No such device

It's peculiar because that module's path does indeed exist..

Anyone know what's wrong?  Or am I completely missing the mark here..

EDIT:
CPU is AMD Athlon&#8482; 64 X2 4000+ (dual-core)
Chipset is NVIDIA® GeForce® 6150SE

---

### Post by Picatta on 2008-01-28
Hey, could it be an issue with the kernel?  If I rolled the kernel back a few version would it be fixed?

---

### Post by Picatta on 2008-01-28
bump

---

### Post by cubeist on 2008-01-28
You could try a simple program called Computer Temperature Monitor ([http://computertemp.berlios.de/](http://computertemp.berlios.de/))

This should give you an idea of your temps, but does not allow changing the fan speed.  If your temps are a serious problem there may be other reasons that the fan speed.  For example you could try compressed air to clean out the fans and make sure the system has adequate air flow around the machine...

---

### Post by Picatta on 2008-01-28
> **cubeist said:**
> You could try a simple program called Computer Temperature Monitor ([http://computertemp.berlios.de/](http://computertemp.berlios.de/))

This should give you an idea of your temps, but does not allow changing the fan speed.  If your temps are a serious problem there may be other reasons that the fan speed.  For example you could try compressed air to clean out the fans and make sure the system has adequate air flow around the machine...

I already had that installed, and managed to get k8temp to work, so I can see my temperature (usually between 20-25C, up to 45 if watching a video and spinning the cube in compiz).  So, there is really no way to control fan speed?

---

### Post by cubeist on 2008-01-29
The best way to control fan speed is a hardware controller, which are widely available at most computer stores.  Just use a drive bay and make the connections to the fan... some even come with a separate temp probe for reliable case measurement.  

However your temps are not high... If you were in the 50-80 degree range then I would be worried... I think the reason your fans rarely come on is because they don't need to.  If you put your hand by the exhaust vent is the air comfortably warm or does it burn your fingers?  Warm air is generally ok.

---

### Post by colini on 2008-03-04
I received the exact same error message after running sensors-detect and attempting to load the it87 module:

# modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/it87.ko): No such device

Like the original poster said, the it87.ko file does exist at that path.  

My platform: Kubuntu 7.10 x86-64 on AMD X2 BE-2350 with nVidia MCP61P chipset.

Any ideas?  I'd like to be able to gather temp information.

Thanks.

---

### Post by HarvesterOfBeer on 2008-04-21
I am also experiencing the same issues. Gutsy 7.10 x86-64, AMD BE-2300 on a ECS GeForce 7050m-m.

---

