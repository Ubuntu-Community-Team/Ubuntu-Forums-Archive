---
title: "Screen Ratio is messed up, and everything is scrambled"
date: 2008-03-23
forum: Apple Intel Users
---

### Post by neonbagpiper on 2008-03-23
I have an aluminum imac 24". It was working perfectly until, in all of my infinite wisdom, decided to turn on the widescreen option in screens and resolutions (I am not entirely sure if it was in that though). Heres the kicker it is so scrambled and messed up I can't even turn it off! After 3 days of configuring Ubuntu and booting between Mac OS X and Gusty numerous times to do so, I don't want it all to be wasted on a stupid mistake I made. Please help.

Specs

ATI,RadeonHD2600
Running Ubuntu 7.10

Since I am not the most savvy with linux can you please be detailed in your explanations, but anything helps.

---

### Post by afterkelsen on 2008-03-24
I have no idea to what the actual problem might be but an easy fix may be to boot up, without entering X, and simply to a "dpkg-reconfigure xserver-xorg". Or you can manually edit "/etc/X11/xorg.conf" to see if you can find the mistake. If you cannot prevent your machine from entering X on boot then boot the machine from a Ubuntu Live CD, mount your partition(s) and edit xorg.conf.

Or once booted from the Live CD chroot into your usual enviroment, which would can be done something like this:
[LIST=1]
[*]Mount partitions: For instance ```
mount /dev/sda1 /mnt
``` if you're Linux root partition is the first on /dev/sda.
[*]Chroot: ```
chroot /mnt /bin/su - 
```
[*]You probably want to mount proc as well: ```
mount -t proc none /proc
```
[*]Now do a: ```
dpkg-reconfigure xserver-xorg
``` and reboot.
[/LIST]

Hopefully that will make things work.

Just got another idea. If you have two machines, and a SSH server running on your broken Ubuntu, simply ssh into the machine on reconfigure X.

---

### Post by cyberdork33 on 2008-03-24
and don't mess with the screens and graphics thingy because it usually just messes things up.

---

### Post by neonbagpiper on 2008-03-29
dpkg-reconfigure xserver-xorg is what I found online, so I did this, and now it is stuck on the starting boot scripts line when is boots up, and can keystroke in terminal but if I keystroke out I can't get back in. I will try it via the boot cd

By the way cyberdork, I know your intentions are good, but that doesn't really help after the fact.

---

### Post by cyberdork33 on 2008-03-29
> **neonbagpiper said:**
> By the way cyberdork, I know your intentions are good, but that doesn't really help after the fact.
It does for the future. Just because you did it once, doesn't mean you know what caused the problem...

If you had fglrx working correctly previously, you need to set it back as the driver to you in the xorg.conf. If the boot process is dying at the "boot scripts" area then you might have bigger issues though...

---

