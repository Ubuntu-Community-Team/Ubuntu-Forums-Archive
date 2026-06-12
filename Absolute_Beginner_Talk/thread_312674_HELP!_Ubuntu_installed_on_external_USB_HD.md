---
title: "HELP! Ubuntu installed on external USB HD"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by TygerZoyd on 2006-12-04
I installed Ubuntu 6.10 onto an external HD (drive G:\) connected to my desktop computer via USB.  My main (internal SATA) HD (drive C:\) has Windows XP Pro on it and it my main system and OS.

Now that I've installed Ubuntu to my external HD (G:\) which has an on/off switch, I have to have G:\ connected and switched ON ALL the time to see the boot menu where I can choose between three Ubuntu loading options and Windows XP Pro.

Otherwise, if G:\ is not connected via USB or switched off, I get an "Error 21" code and the loading halts, I don't see the boot menu, and thus cannot get to either Ubuntu or Windows XP Pro.

My problem is that I do not want a boot menu.  I always want my system (as it did before) to go right into Windows XP Pro on my C:\ drive.  If I want to boot to Ubuntu, I will turn on G:\ manually and have it load from there.

Does anyone know what was modified on my system (BIOS setting, system or config file on C:\, system or config file on G:\, something else?) so I can change it to avoid the boot menu?

My intent was to play with Ubuntu to learn Linux, NOT create a dual-boot system.

PLEASE HELP.  I am very frustrated and don't know how to revert back to Windows XP Pro other than choosing it through the boot menu (and I've already modified /boot/grub/menu.lst to change the default boot OS to Windows XP Pro so the 10 second delay/timeout will choose that).  I don't want a boot menu at all.

Any suggestions?  Thanks in advance for any help anyone can offer.

---

### Post by tuxcantfly on 2006-12-04
pop open your windows recovery cd, and do a fixmbr

---

