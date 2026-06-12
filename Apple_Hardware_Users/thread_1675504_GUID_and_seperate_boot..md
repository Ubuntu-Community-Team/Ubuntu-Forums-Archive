---
title: "GUID and seperate /boot."
date: 2011-01-25
forum: Apple Hardware Users
---

### Post by TuxIsAwesome on 2011-01-25
Hello, I have a few questions.

I currently have Ubuntu 10.10 maverick meerkat installed on my 4,1 Macbook. I normally use my / partition to boot, but lately I've been having some thoughts on making a dedicated /boot partition. 

Is it possible to set up such a /boot partition from an existing installation? I dont really want to have to re-install everything again. Just got done with that yesterday from a botched upgrade to 11.04 (Go Figure, updating gnome-shell breaks everything), so a reinstall to achieve this is not an option.

Is it possible for the /boot partition to reside in the GPT part of the disk (Anything beyond the 4th partition)? I don't really want to have to re-arrange all of my partitions.

Will having a /boot partition force grub2 to install to said partition rather than /dev/sda (aka the entire disk, minus the HFS+ volume for OSX)?

Disk space is not a problem since it's a 500GB HDD. However partitions reside on the entirety of the disk. Now, I am not afraid to kill off OpenSuSE or something like that. I could also cleave off part of Ubuntu's partition after cleaning it up and that would work well also. Finally, since I'm going to do an install of Natty's daily build into /dev/sda6, I could create the /boot partition during it's setup.

Oh, if it helps, here's my current partition setup (Plus the EFI partition)

/dev/sda1 (EFI, REQUIRED) FAT32
/dev/sda2 (Winblowz 7) NTFS
/dev/sda3 (Massive Storage Partition) REQUIRED for storing stuff. EXT4
/dev/sda4 (Ubuntu) EXT4
/dev/sda5 (/Tmp) EXT4 
/dev/sda6 (Testing Grounds for Alpha Releases) EXT4
/dev/sda7 (Mac OSX) HFS+Journaled
/dev/sda8 (OpenSuSE) EXT4
/dev/sda9 (SWAP)

---

### Post by srs5694 on 2011-01-25
> **TuxIsAwesome said:**
> Is it possible to set up such a /boot partition from an existing installation?

Yes. You'll need to create the partition, juggle files around, update /etc/fstab, and update your GRUB configuration. (The automated tools should take care of the nitty-gritty of the GRUB reconfiguration, but you *must* remember to invoke them before rebooting!)

IMHO, it's not worth it unless you've got some specific reason. Moving/resizing partitions alone is too much risk if you're just casually interested in experimenting. OTOH, it sounds like you're experimenting with different distributions, in which case, creating a separate /boot partition on the next re-installation should be pretty straightforward. There'd probably be very little benefit to it, but you could do it.

(As a side note, one very minor benefit is that you can use unjournaled HFS+ on a /boot partition, thus making it accessible to both Linux and OS X. That way, you can edit your GRUB configuration from OS X, if that becomes necessary. Ubuntu won't install directly this way, but you can reconfigure it after the fact, if you like. IMHO, this probably isn't worth the hassle, but you can do it if you like to manually tweak your GRUB configuration and want the option of doing it from OS X.)

> Is it possible for the /boot partition to reside in the GPT part of the disk (Anything beyond the 4th partition)? I don't really want to have to re-arrange all of my partitions.

Yes. In fact, it's possible for *all* your Linux partitions to reside "in the GPT part of the disk," or to do away with the ugly and dangerous hybrid MBR altogether. (See [my Web page on how I set this up.](http://www.rodsbooks.com/ubuntu-efi/index.html)) When presented with a hybrid MBR, the Linux kernel uses the GPT side exclusively. GRUB 2 is also GPT-friendly. The only uses for a hybrid MBR are enabling Windows to boot and kicking the Mac into BIOS emulation mode (thus enabling use of grub-pc rather than grub-efi).

> Will having a /boot partition force grub2 to install to said partition rather than /dev/sda (aka the entire disk, minus the HFS+ volume for OSX)?

No. On a BIOS-based computer (which your Mac is, as far as Linux and GRUB are concerned, when you use a hybrid MBR), the initial GRUB code may reside in the MBR or in a boot partition, although GRUB 2 seems to be much happier in the MBR, so that's where it usually ends up. I wouldn't recommend attempting to move it unless you want to move away from hybrid MBRs and use native EFI booting, in which case you need to replace grub-pc with grub-efi.

BTW, unless you've got multiple disks or have removed OS X from your computer, OS X resides in /dev/sda, even if it's not accessible via MBR entries.

---

