---
title: "boot ubuntu first"
date: 2007-07-15
forum: Apple Intel Users
---

### Post by MichaëlVD on 2007-07-15
I have a OSX install and a Gutsy install on my iMac. I would like Gutsy to start up by default instead of OSX. Is there a way to change the order? Currently, I always have to hold the alt key when booting, or else I'm in OSX.

Thanks!

---

### Post by Feba on 2007-07-15
Are you using GRUB as a bootloader?

[http://forums.fedoraforum.org/archive/index.php/t-22272.html](http://forums.fedoraforum.org/archive/index.php/t-22272.html)

---

### Post by C0d3Runr on 2007-07-15
> **MichaëlVD said:**
> I have a OSX install and a Gutsy install on my iMac. I would like Gutsy to start up by default instead of OSX. Is there a way to change the order? Currently, I always have to hold the alt key when booting, or else I'm in OSX.


Rather than using BootCamp, you should be able to install rEFIt from OS X (it's much prettier and doesn't require you to hold down alt).  Then, you can configure it to default to BIOS-Based boot options, which should make it find Grub first.

---

### Post by thully on 2007-07-16
Yes, rEFIt will work.

There may be a way to do it without, though - I know that if you use Boot Camp to install Ubuntu on an OS X-only drive, it will be set as default after the install (because Boot Camp sets the legacy BIOS boot - in this case, Linux instead of Windows - as the default).

To do this without reinstalling, you could try inserting an Ubuntu CD in OS X, setting it as the startup disk in the Startup Disk preferences applet.  Then reboot and eject the CD (you will need to hold down Option to do this).  If my thinking is right, that should set legacy BIOS booting as the default - and thus make Ubuntu the default without any stopover at a boot menu (as rEFIt does).

I'm unsure about this, but I know I've done it before...  It may just be Boot Camp, though.

On a side note, if you plan to install just Ubuntu (no OS X), install Boot Camp and use it as if you were installing Windows.  When it somes time to boot your 'Windows" CD, give it Ubuntu instead and wipe the drive.  That way, it will boot straight into Ubuntu with only an MBR and no delay to search for an EFI-bootable partition.  Essentially, your Mac will behave just like a standard PC (save for fancy BIOS menu and boot screen).

---

### Post by rami1983 on 2007-07-16
> **MichaëlVD said:**
> I have a OSX install and a Gutsy install on my iMac. I would like Gutsy to start up by default instead of OSX. Is there a way to change the order? Currently, I always have to hold the alt key when booting, or else I'm in OSX.

Thanks!

2 Ways of doing it:

1) Using Bootcamp ... after you partition your harddisk select start windows installation .. it will set windows partition as default boot partition 

2) Using Mac OSX DVD ... insert OSX dvd .. after booting the dvd .. there is a menu iteam to select start up disk

---

