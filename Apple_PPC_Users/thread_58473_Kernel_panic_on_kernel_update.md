---
title: "Kernel panic on kernel update"
date: 2005-08-20
forum: Apple PPC Users
---

### Post by Entity on 2005-08-20
I'm running hoary PPC on my Powerbook and I just upgraded the kernel using synaptic this morning and I get a kernel panic on reboot:

Kernel panic - not syncing: VFS Unable to mount root fs on unknown-block(0,0)

Also, I tried to use the "old" kernel and it won't boot either as it says;

/pci@f4000000/ata-6@d/disk@0:3,/boot/vmlinux.old: No such file or directory.
boot:

I don't know what I should do from this point?  ](*,) 

I'm just downloading a live CD so i can look what's in /boot... maybe I could chroot the powerbook's fs and run ybin again?

Any suggestion is welcome, thanks

---

### Post by pierba on 2005-08-20
Yes, you must enter in  your system, with chroot, update your /etc/yaboot.conf and run ybin

Pietro

---

