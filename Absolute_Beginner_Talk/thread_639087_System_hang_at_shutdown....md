---
title: "System hang at shutdown..."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by WebEyeX on 2007-12-12
Hi,
I am shutting down my system without any splash or usplash but it just hangs at shutdown.Some line from shutdown is..

NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed -
[ 226.137045] System halted.

It just hangs up here,mean to say does not power off or go further.

It is booting well.I am also using 'acpi=off apm=off' boot parameters with grub menu list because 'kacpid' process was eating my 90% CPU.

How can i bring my system to proper shutdown again.Plz help.

Thanks.

---

### Post by WebEyeX on 2007-12-12
These are the exact lines after which system hangs up
(last few lines)
--------------------
--------------------
NetworkManager:<Warn>nm_hal_deinit();libhal shutdown failed - connectin is closed

NetworkManager:nm_dbus_signal_device_status_change:assertion 'cb_data->dbus-connection' failed

NetworkManager:nm_dbus_signal_device_status_change:assertion 'cb_data->dbus-connection' failed

[220.511772]System Halted.

System just hangs up here..

PLz help.

---

### Post by otchie1 on 2007-12-28
Same here. Just started doing it for no reason that I can work out

nm_dbus_signal_device_status_change
'cb_data->data->bus_connection' failed

---

### Post by Yuzem on 2008-01-06
I had the same problem.
I replaced acpi=off with noapic and now it shut down correctly.

---

### Post by otchie1 on 2008-01-12
> **otchie1 said:**
> Same here. Just started doing it for no reason that I can work out

nm_dbus_signal_device_status_change
'cb_data->data->bus_connection' failed

although clearly I'ma bit dense as I forgot that I had just fitted a new wifi card.

The lock up is due to the Netwrok Manager having trouble with the wifi and was fixed after some Googling.

In /etc/modules add the following line to the end,

apm power_off=1

In /boot/grub/menu/lst add the following line to the end of your kernel line for your booting kernel,

apm=power_off

Lost original source of fix but kudos to whoever you were.

---

### Post by steveneddy on 2008-02-07
> **otchie1 said:**
> although clearly I'ma bit dense as I forgot that I had just fitted a new wifi card.

The lock up is due to the Netwrok Manager having trouble with the wifi and was fixed after some Googling.

In /etc/modules add the following line to the end,

apm power_off=1

In /boot/grub/menu/lst add the following line to the end of your kernel line for your booting kernel,

apm=power_off

Lost original source of fix but kudos to whoever you were.

That should /boot/grub/menu.lst

---

### Post by otchie1 on 2008-02-07
> **steveneddy said:**
> That should /boot/grub/menu.lst

That should be,

"That should BE /boot/grub/menu.lst"

:)

---

### Post by brander on 2008-02-12
I too get this problem after the updates of February 10th. I can edit the menu.lst but can somebody tell me where the kernel line is please.

---

### Post by otchie1 on 2008-02-12
> **brander said:**
> I too get this problem after the updates of February 10th. I can edit the menu.lst but can somebody tell me where the kernel line is please.

At the very bottom of you /boot/grub/menu.lst file you will have a series of lines like these,

```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a607ed19-087b-42ea-be7a-22e4326f4549 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a607ed19-087b-42ea-be7a-22e4326f4549 ro single
initrd		/boot/initrd.img-2.6.22-14-generic
```

Those are the two top sections of my file.
I boot to Ubuntu 7.10, kernel 2.6.22-14-generic so I only need to edit that section.

Add the "apm=power_off" to the kernel line so it looks like this,

```
kernel		/boot/vmlinuz-2.6.22-14-generic  apm=power_off
```

HTH

---

