---
title: "Copying kernel in OldWorld install"
date: 2005-01-17
forum: Apple PPC Users
---

### Post by perroboy on 2005-01-17
After reading the OldWorld installation instructions, I have still not been able to copy the kernel from the target partition to the hfs partition so that I can boot into ubuntu using BootX. 

Interrupting the install seemed too risky (at least for me) and downloading the debian boot floppies doesn't help either, as I cannot create ext2 floppies of the root/rescue disks on the PowerMac.

Any other suggestions?

---

### Post by trash on 2005-01-17
I did a messy work around by installing a minimal yellowdog2.3 install on a small hard drive i had, with the yellowdog hard drive i was able to mount the harddrive where i just installed Ubuntu, got the files copied t to yellowdog and there i was able to mount the hfs where i needed to put the new kernel and init... it was kinda fun hehe... it's late so i don't know if this makes any sense to you. but if you have an extra drive around its worth it!


EDIT:
just had a thought about what is needed in the ppc world... a simple ppc live cd with just the basics to boot a machine and mount hfs/hfs+ and of course linux partitions.. seems like it could be simple enough to do no?

---

### Post by farruinn on 2005-01-18
[QUOTE=perroboy]
...
downloading the debian boot floppies doesn't help either, as I cannot create ext2 floppies of the root/rescue disks on the PowerMac.
...
[/QUOTE]

Is it only those two disks? You can use Apple's Disk Utility in OS X (Disk Copy I think in OS 9) to copy the disk images to your floppies.

Here are Debian's instructions:
[http://www.debian.org/releases/stable/powerpc/ch-install-methods.en.html#s-create-floppy](http://www.debian.org/releases/stable/powerpc/ch-install-methods.en.html#s-create-floppy)

---

### Post by perroboy on 2005-01-18
you da man, farruiin!

for all those who r nOO to this (like me), once you've booted into the Debian boot installer, you need to first execute a shell (from the menu)

Next, mount your hfs partition using:

mount -t hfs /dev/hdaX /target (given that you've installed it on an ide drive - sda for SCSI)

After that, create a directory for the linux files:

mkdir /target/nix

then mount your linux partition:

mount /dev/hdaY /mnt

next copy over the contents of /boot:

cp /mnt/boot/*.* /target/nix

And finally, boot into OS9, place the kernel(s) in the kernels folder (the one containing vmilnux) and the images outside of that in the System Folder.

The first time you start from BootX, designate the RAMdisc as the one labelled configure, so the install can finish. Then next time you boot, do so from your linux partition, hdaY

---

