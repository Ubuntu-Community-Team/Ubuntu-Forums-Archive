---
title: "Kernel Panic &amp; boot problems"
date: 2008-06-16
forum: Arch and derivatives
---

### Post by Dr Small on 2008-06-16
I am in desperate need of help. I have had problems since 8:00 this morning, and have been trying to fix them all day. I am at my whit's end.

It all started when I ran the update command to update the system with pacman. It loaded in some extra libraries that I needed for Deluge to work, and installed the kernel26-2.6.25 or so kernel. Deluge then worked, but I was afraid that is was going to mess things up, so I rebooted to be sure.

Sure enough, It had a kernel panic. Basically I panicked too. So after getting some help (very little help) on IRC, I was able to chroot into system from the Arch CD, and upgrade back to the old kernel26-2.6.24. Well, I no longer have the kernel panic, but the system won't boot past the message that looks like this:
```
> Arch Linux (Core Dump)

> http://www.archlinux.org
> Distributed under the GNU General Public License (GPL)

 ------------------------------

```

And that is as far as it gets. Like I said, I am at my whit's end. I desperately need help and suggestions. You can see where I was posting on the ArchLinux Forum about it, but wasn't receiving any help for it:
[http://bbs.archlinux.org/viewtopic.php?id=50310](http://bbs.archlinux.org/viewtopic.php?id=50310)

Dr Small

---

### Post by Barrucadu on 2008-06-17
Can you boot with the fallback kernel?
Also, it was complaining about not finding root, can you post the output of *sudo fdisk -l* please?

---

### Post by Dr Small on 2008-06-17
Before we get too far ahead, let me explain what else I have found out while aimlessly tinkering last night. To your first question, no. I could not boot from fallback either. But I went ahead and deleted /boot/kernel26.img and /boot/kernel26-fallback.img because things acted like it wasn't changing when I was downgrading to the older 2.6.24 kernel.

So after deleting those, I then ran:
```
pacman -U /var/cache/pacman/pkg/kernel26-2.6.24.4-1-i386.pkg.tar.gz
```

And this is where things went bad. I'll only output the error here, since having the entire thing would require me to type it all:
```

==> Building Image "default"
...
...
:: Parsing hook [usbinput]
FATAL: Hook 'keymap' can not be found.
==> FAIL
==> Building Image "fallback"
...
...
:: Parsing Hook [usbinput]
FATAL: Hook 'keymay' can not be found.
==> FAIL
```

Of course, with so many failures, it never creates the kernel's in /boot. My next plan was to remove 'keymap' from HOOKS is /etc/mkinitcpio.conf, which then created the kernels, but now when I boot, I get another kernel panic, which doesn't make any sense.

As to your second question, here is the results:
```

   Device Boot       Start     End     Blocks    ID  System
/dev/sda2                1     136    1092388+    5  Extended
/dev/sda3              137    1093    7687102+   83  Linux
/dev/sda4             1094   19457  147508830    83  Linux
/dev/sda5                5      38     273105    82  Linux swap / Solaris
/dev/sda6               39     136     787153+   83  Linux
/dev/sda7                1       4      32035+   83  Linux

```

And for a simpler summary:
sda3 = /
sda4 = /home
sda5 = swap
sda7 = /boot

---

