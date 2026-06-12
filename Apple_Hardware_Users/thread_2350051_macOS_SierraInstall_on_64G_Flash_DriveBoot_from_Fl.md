---
title: "macOS Sierra/Install on 64G Flash Drive/Boot from Flash Drive"
date: 2017-01-20
forum: Apple Hardware Users
---

### Post by mlee136 on 2017-01-20
Hi,

I would appreciate help on this.

I have 
- MBP running MacOS Sierra
- 64G Flash drive(FAT) for Ubuntu to reside.
- 8G Flash Drive(FAT) for Unetbootin.

So far I've done the following.

1. Download ubuntu-16.04.1-desktop-amd64.iso file.
2. Used Unetbootin so I can boot(with option key during boot) to the flash drive(8G MS-DOS partition, I'm using a different flash drive just for this purpose)
3. Boot from the "efi drive" and started the installation. (Boot loader pointing to sdc (which is the 64G Flash drive))
4. I get the following fatal error message during grub-install.

installing grub on '/dev/sdc'
grub-install does not support --no-floppy
Running chroot /target grub-install --force "/dev/sdc"
Installing for x86_64-efi platform.
grub-install: error: cannot open `/boot/efi/EFI/ubuntu/shimx64.efi':Not a Directory
error: Running 'grub-install --force "/dev/sdc" ' failed.

TIA,

Mike

---

### Post by QIII on 2017-01-20
Moved to Apple Hardware Users.

---

### Post by mlee136 on 2017-01-21
Instead of struggling with Ubuntu-16.4, I decided to install with 16.10 and it worked! There was an error message at the end but installation finished without a failure.

The error message was.
E:Sub-process /usr/bin/dpkg returned an error code(1)

So, I'm happy that Ubuntu 16.10 is installed onto my 64G flash drive.  When I reboot(with option key pressed) my mac with the 64G flash drive inserted, I expected to see a bootable EFI icon for 64G flash drive but I didn't.

How do I boot to 64G Flash Drive??

Thanks,

Mike

---

