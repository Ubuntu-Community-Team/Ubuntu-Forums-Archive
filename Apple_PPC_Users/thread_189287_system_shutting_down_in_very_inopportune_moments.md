---
title: "system shutting down in very inopportune moments"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by colinhayes on 2006-06-05
for a rather long time, I've run Debian on my shiny metal windtunnel dual G5.  I decided to switch to ubuntu, and installed 5.1 a bit before 6.06 came out, and didn't mess with it much before then, but I had the same problem that I'm currently having when I was trying to install 5.1.

Basically, when I attempt to install new software or do anything processor intensive (either via the terminal or graphically) there's a great chance that my computer will completely shutdown. No warning, no kernel panic, just the computer turning off.  Both processors will start going at it (not perfectly symmetrically either, I've seen 96% and 18% at the same time).  it seems that if I see one of them hit 100%, it'll shutdown.

Now, debian never did this, and when I had ubuntu 4.1 a while back, it never did this.

so, ideas?

---

### Post by Rxke on 2006-06-06
I've had exactly the same problem with my Clamshell (G3) quite awhile ago under 5.10. Shutting off without warning, very scary.
I couldn't find a reason, other than it was probably related to cpu maxing out and maybe getting too hot? 

Had it happen 6-10 times in short succession, sometimes 2-3 times a day, but after awhile it just... Stopped misbehaving :-k

---

### Post by colinhayes on 2006-06-06
[QUOTE=Rxke]I've had exactly the same problem with my Clamshell (G3) quite awhile ago under 5.10. Shutting off without warning, very scary.
I couldn't find a reason, other than it was probably related to cpu maxing out and maybe getting too hot? 

Had it happen 6-10 times in short succession, sometimes 2-3 times a day, but after awhile it just... Stopped misbehaving :-k[/QUOTE]


I'm thinking there might be the off chance that thermal management might not be working correctly and that compiling a new kernel would be a great fix, but I'll be damned if I can get through compiling the kernel without the thing shutting off.

just a thought, since youv'e had this problem, is there anything in the bug tracker discussing this?  I tried looking but couldn't find anything.

---

### Post by Rxke on 2006-06-06
a truly Catch-22 situation allright...

---

### Post by colinhayes on 2006-06-06
[QUOTE=Rxke]a truly Catch-22 situation allright...[/QUOTE]

but there still is the option of booting into my old 4.1 live cd and compiling it into a deb package through there

---

### Post by colinhayes on 2006-06-09
i'm going to go ahead and bump this.


I'm stuck, I can't compile a kernel from the live cd, and it shuts down every time I attempt to compile a kernel.

---

### Post by nkbj on 2006-06-09
Colin: Try adding the line ```
therm_windtunnel
``` to the /etc/modules file and reboot. Let us know if that makes a difference.

Regards,
Niels Kristian

---

### Post by colinhayes on 2006-06-09
[QUOTE=nkbj]Colin: Try adding the line ```
therm_windtunnel
``` to the /etc/modules file and reboot. Let us know if that makes a difference.

Regards,
Niels Kristian[/QUOTE]

well, it doesn't load the module, so it doesn't quite do anything.

sure you aren't thinking of windfarm?

**edit: I changed it to therm_windfarm, and still no load... doesn't the module need to be compiled and placed somewhere before it can be loaded?**

---

### Post by nkbj on 2006-06-10
You're right therm_windtunnel is for G4 systems. The windfarm thermal control code for G5 systems is not included in kernel 2.6.15. It seems you'll have to build you own kernel or wait for edgy to get working thermal control on your system.

Regards,
Niels Kristian

---

### Post by colinhayes on 2006-06-10
[QUOTE=nkbj]You're right therm_windtunnel is for G4 systems. The windfarm thermal control code for G5 systems is not included in kernel 2.6.15. It seems you'll have to build you own kernel or wait for edgy to get working thermal control on your system.

Regards,
Niels Kristian[/QUOTE]


well, I suppose I can continue trying to compile a post 2.16.15 kernel and hopefully it won't overheat sometime?

---

### Post by nkbj on 2006-06-11
It seems to be a known issue according to this bug report: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723)

It seems there is little chance of a backport. :-(

Regards,
Niels Kristian

---

### Post by colinhayes on 2006-06-11
[QUOTE=nkbj]It seems to be a known issue according to this bug report: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34723)

It seems there is little chance of a backport. :-(

Regards,
Niels Kristian[/QUOTE]

it's good to see that lack of thermal management is of "low" importance, especially when the fix involves click a single checkbox during configuration.

one other thing... this winfarm module seems to be designed for the iMac G5's, will it even be compatible with my dual 2.0GHz pmac G5?

---

### Post by nkbj on 2006-06-11
[QUOTE=colinhayes]one other thing... this winfarm module seems to be designed for the iMac G5's, will it even be compatible with my dual 2.0GHz pmac G5?[/QUOTE]

It seems you should use the **windfarm_pm112** module.

This is from linux-2.6.16.20/drivers/macintosh/Kconfig:```
config WINDFARM_PM112
        tristate "Support for thermal management on PowerMac11,2"
        depends on WINDFARM && I2C && PMAC_SMU
        select I2C_POWERMAC
        help
          This driver provides thermal control for the PowerMac11,2
          which are the recent dual and quad G5 machines using the
          970MP dual-core processor.
```

Regards,
Niels Kristian

---

### Post by colinhayes on 2006-06-11
[QUOTE=nkbj]It seems you should use the **windfarm_pm112** module.

This is from linux-2.6.16.20/drivers/macintosh/Kconfig:```
config WINDFARM_PM112
        tristate "Support for thermal management on PowerMac11,2"
        depends on WINDFARM && I2C && PMAC_SMU
        select I2C_POWERMAC
        help
          This driver provides thermal control for the PowerMac11,2
          which are the recent dual and quad G5 machines using the
          970MP dual-core processor.
```

Regards,
Niels Kristian[/QUOTE]


I have a PowerMac7,3

---

### Post by nkbj on 2006-06-11
[QUOTE=colinhayes]I have a PowerMac7,3[/QUOTE]
OK, then it is the therm_pm72 module.

Regards,
Niels Kristian

---

### Post by colinhayes on 2006-06-11
[QUOTE=nkbj]OK, then it is the therm_pm72 module.

Regards,
Niels Kristian[/QUOTE]


which was already loaded.

---

### Post by kellogs on 2006-06-11
hmm, does this have something to do with:

[   35.914062] PowerMac G5 Thermal control driver 1.2b2

in lsmod I get that therm_pm72 0, not loaded... but the system fans don't go full time only when I put lots of work into the system.

may be there is a preliminary fan driver then?

---

### Post by n00bWillingToLearn on 2006-06-11
I would just like to thank you guys because with your information and the help of my local linux expert I now have thermal management on my 17' powerbook ( no more keepin it cool with an ice pack:) ). This really should be given a higher priority given how easy it is to fix. Do you think, in the absense of an actual fix from the ubuntu devs, we sould ask the easyubuntu / automatix people to add this as a feature in the PPC versions?

---

### Post by colinhayes on 2006-06-12
[https://launchpad.net/distros/ubuntu/+bug/49514](https://launchpad.net/distros/ubuntu/+bug/49514)

I went ahead and stuck it in as a bug so it can get the attention of some other people.

---

