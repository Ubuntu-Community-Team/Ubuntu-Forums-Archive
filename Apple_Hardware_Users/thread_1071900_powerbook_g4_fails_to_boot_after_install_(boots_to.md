---
title: "powerbook g4 fails to boot after install (boots to white screen)"
date: 2009-02-16
forum: Apple Hardware Users
---

### Post by bootdoc on 2009-02-16
just installed 8.1.  after install and reboot all I get is a bright white screen.

---

### Post by avtolle on 2009-02-17
Try, at second yaboot prompt (press Tab to slow things down): Linux video=ofonly.

---

### Post by bootdoc on 2009-02-17
Thanks, that worked.  I added video=ofonly to the /etc/yaboot.conf file and still not getting a clean boot.  I still have to enter this at the boot prompt.  here is a copy of my yaboot.conf.


boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/hda3
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash modprobe ide-scsi video=ofonly"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash modprobe ide-scsi video=ofonly"

---

### Post by tiresia on 2009-02-17
If X works for you, just giving at the second yaboot prompt the argument 'video=ofonly', you don't need to add "quiet splash..."

Anyway after you modify yaboot.conf you need to run 'sudo ybin -v' to update the new yaboot configuration

---

### Post by bootdoc on 2009-02-17
thanks!  I read that somewhere and completely forgot.

---

