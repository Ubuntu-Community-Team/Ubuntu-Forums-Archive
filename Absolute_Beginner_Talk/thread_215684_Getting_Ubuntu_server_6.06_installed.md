---
title: "Getting Ubuntu server 6.06 installed"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by leefw on 2006-07-14
Hi

Sorry to bother you all with this, but I have now officially given up trying to install Ubuntu Server 6.06 on my my old Pentium-MMX 200 MHz PC (196608K RAM, older BIOS from 1997).

I think I must have tried to install the damn thing at least 10 times over the last two days... repartioning, re-installing GRUB, removing partitions using the "Rescue a broken system" part of the install CD, etc. 

The trouble seems not to be the actuall install, but the uncompressing of Linux at boot time. This is a brief (manual) print of the boot procedure as it now stands (subject to possible typos):

...

Verifying DMI pool data
Boot from ATAPI CD-ROM failure
GRUB Loading stage 1.5
GRUB Loading, please wait...
Booting 'Ubuntu kernel 2.6.15-23-server'
root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /vmlinuz-2.6.15-23-server root=/dev/hda2 ro quiet splash
   [Linux-bzImage, setup 0x1c00, size=0x16675f]
initrd /initrd-img-2.6.15-23-server
   [Linux-initrd @0xb950000, 0x69f72c bytes]
savedefault
boot

... and at this point the machine reboots itself and repeats.

Comparing this to my newer machine running Kubuntu 6.06 the next thing to happen should be "uncompressing linux", but it never gets there and I have no clue why not. Can I enable any form of boot logging?

Another thing I notice is that the system is trying to find a kernel file that isn't in the /boot directory or hda1 like it was supposed to.

Let me add that I am no expert on Linux and partitioning, boot sectors, GRUB etc are almost terrifying... and I'm not 100% sure I know what I'm doing.

Anyway, I recently removed Fedora Core 5 from this old machine because it was just moving too slow and I only want a server interface anyway (seems not possible with Fedora install process anymore?). I am not sure if the Fedore de-install procedure (I just removed the existing partitions, I think) left the system in an odd state, but now I really just want to clear everything (boot sector, partitions etc) from the discs and start fresh.

Can anyone shed some light to why this might be happining? 

How can I get rid of absolutly everything from the harddrives?

I anxiously await you wisdom... :-)

---

### Post by mdrenwick on 2006-08-04
You are not the only one suffering from this. I've stuggled for a few late nights trying to get the 6.06 server to boot up after a seemingly successful install.

There are other forums that claim the "alternative" CD ISO image is the way to fix this.

I aim to try the alternative install over the weekend.

---

### Post by leefw on 2006-08-04
Sorry, I should have responded to my own thread earlier. I too used the Ubunutu alternative CD ISO version to install my server. It seemed to work fine. 

So I guess this just means there is a serious problem with the Ubuntu server ISO file. :rolleyes:

---

