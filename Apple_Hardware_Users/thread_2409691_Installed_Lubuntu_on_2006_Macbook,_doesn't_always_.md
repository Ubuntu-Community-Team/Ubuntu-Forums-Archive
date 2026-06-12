---
title: "Installed Lubuntu on 2006 Macbook, doesn't always boot."
date: 2019-01-05
forum: Apple Hardware Users
---

### Post by berncs98 on 2019-01-05
I recently installed Lubuntu 16 on a 2006 model Macbook (i388). The OS works great but I can't get it to boot 100% of the time.

I get the mac "chime" when you turn it on, and after it gets to GRUB, normally this happens:

First, Lubuntu does not boot.
I tried with recovery mode, and apparently the problem is that it gets stuck in "loading initial ramdisk". Before this happens, GRUB seems normal, with my 10s timeout setting working.

I am forced to reboot, do the same thing again, get to GRUB, and then wait. For some reason the keyboard tends to not respond in GRUB. Sometimes GRUB has a timeout of 30s, and I realized that when this happens, this time it will boot.

Once this weird ritual is complete, Lubuntu boots and it works very well.

I have tried reinstalling GRUB, to no avail.

---

### Post by mwei19 on 2019-01-05
> **berncs98 said:**
> I recently installed Lubuntu 16 on a 2006 model Macbook (i388). The OS works great but I can't get it to boot 100% of the time.

I get the mac "chime" when you turn it on, and after it gets to GRUB, normally this happens:

First, Lubuntu does not boot.
I tried with recovery mode, and apparently the problem is that it gets stuck in "loading initial ramdisk". Before this happens, GRUB seems normal, with my 10s timeout setting working.

I am forced to reboot, do the same thing again, get to GRUB, and then wait. For some reason the keyboard tends to not respond in GRUB. Sometimes GRUB has a timeout of 30s, and I realized that when this happens, this time it will boot.

Once this weird ritual is complete, Lubuntu boots and it works very well.

I have tried reinstalling GRUB, to no avail.

DId you add in "**nomodeset**" into the GRUB linux line? if not, give that a shot. 

I'm not a pro at this but I recently installed Ubuntu 18.04 LTS onto my mid-2010 macbook pro and read up that the macs need the "**nomodeset" **in the grub configuration. May or may not be related to your issue? Also, another suggestion is to remove the quite splash option in the grub so you can see what exactly is happening in the boot up process and perhaps get a good message that can pin point the issue?

---

### Post by francoisdelabre on 2019-01-13
I had an issue with a Macbook (late 2006) and Ubuntu 16.04, where boot was OK one every two starts.


It seems Grub has a different configuration when it detects a previous boot did not succeed.
I had a look at the grub.cfg configuration file and it does different things when the "recordfail" attribute is set.
On my configuration, the difference was mainly on the GFXmode setting.


So I added the following line to the Grub configuration in /etc/default/grub to force the text mode :
GRUB_GFXPAYLOAD_LINUX=text


The grub configuration then needs to be regenerated with sudo update-grub


Hope this helps!

---

### Post by francoisdelabre on 2019-01-13
I don't have this Macbook (2,1 Late 2006) anymore.
But after I installed Ubuntu 16.04 in 32 bits, I did upgrade it to Ubuntu 18.04 LTS (Bionic Beaver) 32 bits.

First I installed Ubuntu 16.04.5 32 bits from DVD, standalone (disk erased, no macOS).
Standard installation (BIOS emulation).
As explained, to boot consistently in graphics mode, GFX must be in text mode. Otherwise, boot will fail every other start (crash on the first boot, boots ok in failure mode the second boot, etc.).
Just add the next line to /etc/default/grub and run sudo update-grub :
GRUB_GFXPAYLOAD_LINUX=text


Then I upgraded to 18.04 (thus 32 bits).
Crash on boot, Wayland must be disabled in GDM. Simply uncomment the line WaylandEnable=false in /etc/gdm3/custom.conf.


Everything seems fine afterwords : wifi, trackpad, keyboard (even special keys for screen brightness and volume control work), etc.

---

