---
title: "Grip and Grub"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-14
This is a line from the Help for grip:
> To enable SCSI emulation, add "hdx=ide-scsi" (where the "x" in "hdx" is is replaced with the appropriate letter for your CDRom device) to end of the "kernel" line in /etc/grub.conf (if you are using grub)
Unfortunately, I don't have a file named /etc/grub.conf, and a search found only /usr/src/linux-headers-2.6.17-10/debian/exampleskpkg_grub.conf.  Do any of you have /etc/grub.conf and if so can you explain why I don't.  I seem to boot up just fine without it, but I would like to speed up grip's ripping.

Thanks,
Buck

---

### Post by robenroute on 2006-12-14
Might they mean the menu.lst file in /boot/grub ? I've checked my system and grub.conf is nowhere to be found.....

BTW, have a look at DMA settings for your CD-ROM drive, that might speed up things.

---

### Post by Buck2348 on 2006-12-14
> **robenroute said:**
> Might they mean the menu.lst file in /boot/grub ? I've checked my system and grub.conf is nowhere to be found.....
I thought of that and took a look at the grub menu, but I believe that kpkg_grub.conf file is an example or template for the file they're talking about.  It's a text file only four lines long and does have the "kernel" line they mentioned.  The other lines would have to be modified to fit my system if it were used.  I'm tempted to edit it and copy it into /etc but I'd hate to mess up my boot.

> **robenroute said:**
> BTW, have a look at DMA settings for your CD-ROM drive, that might speed up things.
Thanks, I checked and the drive is using DMA.

Thank you very much for your reply.

Buck

---

### Post by logos34 on 2006-12-14
The config file is /boot/grub/menu.lst.

I've been wondering about this too.  As best I can make out, scsi emulation is no longer necessary with the 2.6 kernel (with the new SG_IO interface) and/or the latest cdparanoia release 10.  Although I should add that I haven't noticed any speed difference between version cdparanoia III 9.8 and cdparamoia III 10pre0 beta release.  

more info: [http://xiph.org/paranoia/trouble.html](http://xiph.org/paranoia/trouble.html) (You can get release 10 there too).

Here's the response I got from the moderator of Grip-users forum:

"...No, ide-scsi was only needed in 2.4 (and perhaps early 2.6) kernels.
With your 2.6.17 kernel cdda2wav should work with the normal (ide-cd)
/dev/cdrom.

> > I use GRUB bootloader, so do I edit the 'kernel' line in the config file
> > (in my case /boot/grub/menu.lst) to read:
> > 
> > kernel    /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash hdc=ide-scsi

If you insist on trying it: yes, that is the way to append a kernel option in grub."
[end]

At any rate if you decide to try adding the emulation option to your kernel line, do post your before and after rip speeds here in the forum.  I'm sure it would interest some people.

---

