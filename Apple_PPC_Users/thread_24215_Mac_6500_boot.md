---
title: "Mac 6500 boot"
date: 2005-04-05
forum: Apple PPC Users
---

### Post by mpscoggins on 2005-04-05
I have a Mac 6500/225 that I would like to install ubuntu on.  How would I force the cdrom to boot or do i need floppies.  I am new to the linux game and run it on my imac (works great) :-(

---

### Post by erkki70 on 2005-04-06
Hi,
You should have a look to these:
[http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs]("http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs")
[http://penguinppc.org/mac/]("http://penguinppc.org/mac/") A lot of very useful infos, Bootx, Quik and almost all you need to successfully install on OldWorld Macs. 


Alternatively there's also the possiblility to use the Debian netinstall, wich comes on floppy or as an image bootable from OpenFirmware (I've done it successfully on Imac G3 266 but never on OldWorld Macs. Yaboot is included and I think you need Bootx instead but it's worth trying anyway...). Then once booted into the installer you'll just have to change the mirrors to get the Ubuntu repositories.
See here:
[http://www.debian.org/distrib/netinst]("http://www.debian.org/distrib/netinst")

Also here: [http://www.wrigley.me.uk/wp/?p=71]("http://www.wrigley.me.uk/wp/?p=71") useful info for a custom Ubuntu net install. You'll have to change the vmlinuz and initrd.gz to the PPC versions though. I guess that once you have Bootx and vmlinuz + initrd.gz installed at the root of your existing Mac OS you should be fine booting BootX from OpenFirmware. (At least that's how it works with Yaboot...


Good luck and hope this helps.
Cheers,
Erkki

---

