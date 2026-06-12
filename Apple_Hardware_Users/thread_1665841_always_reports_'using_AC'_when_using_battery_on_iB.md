---
title: "always reports 'using AC' when using battery on iBook G3"
date: 2011-01-12
forum: Apple Hardware Users
---

### Post by danieru on 2011-01-12
Hi,
I have Maverick 10.10 installed on a 14" iBook G3 ([here]("http://www.everymac.com/systems/apple/ibook/stats/ibook_600_14.html")). The gnome power manager thinks the system is always plugged into AC power, even when I'm unplugged and running on battery. 
The apm_emu module is properly loading on boot, /proc/apm looks good and I'm getting expected output from the apm -v command when the system is unplugged:
```
Off-line, battery status high: 94%
```
and the proper output when the system is plugged into AC:
```
On-line, battery charging: 95%
```

So, what's the deal? Why isn't the gnome power manager picking this info up correctly?

Any help appreciated to gain insight on this and/or fix it:)

---

### Post by KiLaHuRtZ on 2011-01-15
I'm also having this same problem but on an iBook G4.  Other than this issue, I have no other complaints with the PPC build of Ubuntu 10.10.

---

### Post by davidron on 2011-01-17
The solution for me was to add the following to /etc/modules and reboot:
pmu_battery

Source:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/458004](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/458004)

---

### Post by KiLaHuRtZ on 2011-01-23
Thanks!  This worked for me.  Did a live test and it worked so I added it to '/etc/modules'.

```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/power/pmu_battery.ko
```

```
echo pmu_battery | sudo tee /etc/modules
```

---

