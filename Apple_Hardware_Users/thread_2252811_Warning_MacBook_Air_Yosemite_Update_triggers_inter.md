---
title: "Warning: MacBook Air: Yosemite Update triggers interrupt storm"
date: 2014-11-14
forum: Apple Hardware Users
---

### Post by ckk2 on 2014-11-14
Hi,

for those of you dual-booting between OSX and Linux-based distros, I strongly advise that you do not install the free Yosemite update. It contains a firmware update that changes something GPU-related, and the result is an interrupt storm that will eat away your battery in no time.

More details can be found here: [https://bugzilla.kernel.org/show_bug.cgi?id=85881](https://bugzilla.kernel.org/show_bug.cgi?id=85881)

If anyone has a Macbook Air (Mid 2013) and has not yet applied the Yosemite update, you can greatly help debug this issue by posting the output of acpidump and dmidecode either in that bug report above, or here (I'll forward it).

MBAs (Mid 2014) are apparently also affected.

You can create the dumps as follows:
```

$ sudo apt-get install acpidump
$ acpidump > acpidump.out
$ dmidecode> dmidecode.out

```

---

### Post by rican-linux on 2014-11-15
Awesome! I read this after I upgrade my MacBook Pro to Yosemite...

---

### Post by ckk2 on 2014-11-15
> **rican-linux said:**
> Awesome! I read this after I upgrade my MacBook Pro to Yosemite...

If you are affected by this problem ('top' will should you a kworker thread running at 70% or so), then check which of the gpeXX is responsible for this. Usually, it's gpe66. If you execute

```
$ sudo cat /sys/firmware/acpi/interrupts/gpe66
```

the output should be a large number that grows by tens of thousands per second. If that is indeed the case (or for any other gpe66), then this should help:

```
$ sudo echo disable > /sys/firmware/acpi/interrupts/gpe66
```

---

