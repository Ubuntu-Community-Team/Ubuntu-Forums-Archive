---
title: "Implementing powertop recommendations"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by acl123 on 2008-03-05
Hi I have run powertop and it has given me some recommendations. What is the best way that I can have these recommendations turned on every time I boot up.

I created this script:
```

#! /bin/bash

hal-disable-polling --device /dev/hda

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs

mount -o remount,relatime /

echo 5 > /proc/sys/vm/laptop_mode

```

Most of these commands need to be run as root though. How can I have them run at startup as root?

Also, I am trying to get usb autosuspend to work, as powertop recommends, but it does not seemed to be turned on when I boot up.

I added it to the end of the kernel line in /boot/grub/menu.lst but it doesn't seem to do anything:
```

kernel          /boot/vmlinuz-2.6.22-14-rt root=UUID=bcd7d69d-4a8e-485e-b7a8-0e6c8100a105 ro usbcore.autosuspend=1 

```

I also tried adding it to /etc/modeprobe.d/options, like this:
```

options usbcore autosuspend=1

```

Could anyone help me out?

---

### Post by Whiffle on 2008-03-05
I made a script in 

/etc/acpi/battery.d/

that gets run every time the system goes to running on battery.

The mount -o remount command could be changed by adding the proper options to /etc/fstab.  The /etc/modprobe.d/options file looks correct to me.  The other one is only correct if usbcore is built into the kernel, which it is not.

---

### Post by acl123 on 2008-03-05
Cool thanks,
I ended up adding the script to /etc/init.d and it seems to be ok there.

I've left the usb autosuspend in modprobe.d/options but powertop still doesn't think it's implemented.

While I'm here, I might as well also say that I fixed a problem with nvidia wake ups (which constituted over 50% of wakeups), by implementing the solution here:
[http://www.smop.co.uk/mediawiki/index.php/Power_saving_on_Linux#nvidia_vblank_interrupts]("http://www.smop.co.uk/mediawiki/index.php/Power_saving_on_Linux#nvidia_vblank_interrupts")

---

### Post by Whiffle on 2008-03-05
It may be that the usb powersave option isn't activated in the kernel configuration.  I know AC97 power save wasn't on my default feisty, but i rolled my own kernel and took care of all that.

---

