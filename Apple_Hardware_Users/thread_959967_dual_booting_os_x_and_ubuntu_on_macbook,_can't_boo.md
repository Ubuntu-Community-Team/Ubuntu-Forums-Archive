---
title: "dual booting os x and ubuntu on macbook, can't boot into os x!"
date: 2008-10-26
forum: Apple Hardware Users
---

### Post by iDante on 2008-10-26
I just recently installed ubuntu 8.04 onto my macbook, all went smoothly. I made a separate partition for ubuntu. Here is what fdisk -l gives:
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000134d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26        3926    31326208   af  Unknown
/dev/sda3            3926        6965    24414063   83  Linux
/dev/sda4            6965        7296     2659180   82  Linux swap / Solaris

I'm pretty sure that /dev/sda2 is the one that I want to boot into, so I took /boot/grub/menu.lst and added in:
> title MacOSX
root (hd0,1)
makeactive
chainloader --force +1
Unfortunately, nothing happens when I attempt to boot into it with GRUB.

Anything I'm doing wrong?

Edit: a quick thing, when I hold down option as the computer starts, I get an image of just a lock, with a password input field. My admin password doesnt unlock it. What do I use?

---

### Post by cyberdork33 on 2008-10-27
> **iDante said:**
> I just recently installed ubuntu 8.04 onto my macbook, all went smoothly. I made a separate partition for ubuntu. Here is what fdisk -l gives:

I'm pretty sure that /dev/sda2 is the one that I want to boot into, so I took /boot/grub/menu.lst and added in:

Unfortunately, nothing happens when I attempt to boot into it with GRUB.

Anything I'm doing wrong?

Edit: a quick thing, when I hold down option as the computer starts, I get an image of just a lock, with a password input field. My admin password doesnt unlock it. What do I use?

You do not use grub to boot OSX (it won't work). Rather, you use the Mac EFI bootloader to load grub. 

That password sounds like a Firmware password. It would have been set manually and is not the same as your admin password. This would not have been modified by installing Ubuntu.

You could try installing refit to a USB drive and see if that will boot your machine.

---

### Post by Frak on 2008-10-27
Hold the option (mac, Alt on win keyboards) and tell it to boot from your OS X drive.

As for the password, tthat sounds like firmware password. To reset it, move your sundial to face directly east, then say the Ein Van Auto chant and dance like a cat.

Joking aside, to reset the password, you must either take out, or put in a stick of RAM. This alters the RAM amount. When you hear the "gong", hold down the keys

```
Command+Option+P+R
```

and let it "gong" twice. Afterward, let the keys go, press Option to choose startup disc, and you should be fine.

---

