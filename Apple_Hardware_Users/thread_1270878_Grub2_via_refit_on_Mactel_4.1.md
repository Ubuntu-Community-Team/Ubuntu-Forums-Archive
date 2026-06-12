---
title: "Grub2 via refit on Mactel 4.1"
date: 2009-09-20
forum: Apple Hardware Users
---

### Post by e-gandalf on 2009-09-20
Hi all,

I tried to install nightly Ubuntu 9.10 on my mactel 4.1 and hit problems. :(

Info:
 - Mactel 4.1
 - MacOS X 10.6 (64bit)
 - refit 0.13
 - Ubuntu 9.10 64bit nightly CD from yesterday

I created two FAT partitions on the /dev/sda aside from the HFS+ partition for MacOS. In result my partition table looks like this:

bash-3.2# fdisk /dev/rdisk0
Disk: /dev/rdisk0	geometry: 30401/255/63 [488397168 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE 1023 254  63 - 1023 254  63 [         1 -     409639] <Unknown ID>
 2: AF 1023 254  63 - 1023 254  63 [    409640 -  365872448] HFS+        
 3: 0B 1023 254  63 - 1023 254  63 [ 366282088 -   72265626] Win95 FAT-32
*4: 83 1023 254  63 - 1023 254  63 [ 438547714 -   47656251] Linux files*

The install CD failed to  boot into graphic mode and I installed Ubuntu using text mode installer (using ext4). Then I installed grub2 on /dev/sda4 to avoid overwriting refit on MBR.

The next step was to compile grub.efi using grub-mkimage with some modules and following all documentation I could find I copied grub.efi, *.mod, *.lst and grub.cfg to my HFS+ partition into /efi/grub AND to /dev/sda4/efi/grub.

From that point, according to all docs I found, refit should autodiscover grub2, but nothing like this happened.

I rebooted over and over and my refit just says "Mac OS" and "Legacy OS" (probably FAT32 partition for Windows).

Executing "Legacy OS" freezes machine.

I tried the partition tool but it said "everything is OK".

I don't know what to do next. What to analyze, where to check why refit does not find /efi/grub/grub.efi on any partition :(

Anyone has any clue on what could go wrong and what should I do to find what's wrong? Thanks!

---

### Post by pxwpxw on 2009-09-20
Perhaps you used the grub-pc package grub-mkimage to try to build 'grub.efi' which it is not.
The grub-pc grub2 install should work well if installed as part of the ubuntu install, to the MBR /dev/sda, not the ext4  /dev/sda4. There is no need to avoid the MBR, unless windows is installed, and there have been some problems with ext4 for bootloaders.

---

### Post by e-gandalf on 2009-09-20
hmm. Yes, I used what came by default with ubuntu installation to build grub.efi. What's wrong with this approach?

If I install grub2 to MBR on /dev/sda will it work as an option in refit or will it replace refit?

---

### Post by brian.takita on 2009-11-03
I'm also having this issue with the 9.10 release. Any resolution?

Thanks,
Brian

---

### Post by Derrick Zuk on 2009-11-04
Try out a solution found in this thread: [http://ubuntuforums.org/showthread.php?t=1305309&page=2](http://ubuntuforums.org/showthread.php?t=1305309&page=2)

Worked for me. :)

---

