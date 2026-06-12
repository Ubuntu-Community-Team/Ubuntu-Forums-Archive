---
title: "Dual boot 7.04 and 7.10 - can it be done?"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by dhavalbbhatt on 2007-09-28
Hi all -
I would like to know whether the following dual boot options would work or not -
I have 3 HDDs (SATA - 160GB, SATA - 320GB and 1 IDE 80GB) - can the any of the following be possible?

1) Dual boot with Ubuntu 7.04 and 7.10 (Beta) installed on two different hard drives (for example: Ubuntu 7.04 on the SATA 160 and 7.10 Beta on IDE 80GB).

2) Dual boot with Ubuntu 7.04 i386 architecture and 7.04 AMD64 - again on different HDDs.

3) Dual boot with Ubuntu 7.04 and Kubuntu 7.04 same architectures but on different HDDs.?

Thanks,
DB

---

### Post by kellemes on 2007-09-28
Sure..
A lot of threads about this, this is one.
[http://ubuntuforums.org/showthread.php?t=560625]("http://ubuntuforums.org/showthread.php?t=560625")

The most informative site about dualboot you really have to visit is [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by overdrank on 2007-09-28
> **dhavalbbhatt said:**
> Hi all -
I would like to know whether the following dual boot options would work or not -
I have 3 HDDs (SATA - 160GB, SATA - 320GB and 1 IDE 80GB) - can the any of the following be possible?

1) Dual boot with Ubuntu 7.04 and 7.10 (Beta) installed on two different hard drives (for example: Ubuntu 7.04 on the SATA 160 and 7.10 Beta on IDE 80GB).

2) Dual boot with Ubuntu 7.04 i386 architecture and 7.04 AMD64 - again on different HDDs.

3) Dual boot with Ubuntu 7.04 and Kubuntu 7.04 same architectures but on different HDDs.?

Thanks,
DB

HI anything is possible and all the ideas sound feasible. good luck!

---

### Post by USPB on 2007-09-28
tried it but having some bugs

---

### Post by dhavalbbhatt on 2007-09-28
Well - so I did try installing KUBUNTU 7.04 on my IDE hard drive - and now when I boot, it won't even say that KUBUNTU has been installed on my IDE drive - any reasons for that?

Thanks,
DB

The attached is what's on my grub menu.lst

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a0d9b7d2-1fad-4fcf-bc0f-eb34262700dd ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a0d9b7d2-1fad-4fcf-bc0f-eb34262700dd ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda1) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01c6e6fb-8475-4a03-aeb4-2632504efeaf ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda1) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01c6e6fb-8475-4a03-aeb4-2632504efeaf ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, memtest86+ (on /dev/sda1) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by dpar on 2007-09-28
I am currently duel booting Feisty and Gutsy. I did put Gutsy's grub on the Gutsy partition and chainload in Feisty. I do that to keep them entirely seperate when one is a test version.:)

---

### Post by dhavalbbhatt on 2007-09-29
There is obviously something wrong that I am doing - although I can't figure out what - I am only installing from the CD on to my various hard drives. Here is what I have / did -

I have on my first hard drive (SATA 160GB) Ubuntu 7.04 installed - works fine, except for the nvidia issue, for which I have a work around for the time being - not entirely happy though - but it works. I don't plan to install anything on this HD.

On my second HD, which is an IDE 80GB HD, I would like to install Kubuntu 7.04 from the CD. What I did do was, installed it from the CD, however, when the grub loads up and asks me which HD I want to boot from and when I select my IDE HD, it seems to me that the computer freezes and doesn't do anything. I have to power the machine down and re-start - fortunately, I haven't lost my first HD - I can still boot from that HD (phew!).

On my third HD, which is a SATA 320GB, I would like to install either Kubuntu 7.10 or Ubuntu 7.10 but for AMD64 architecture. I have not done anything with that HD - it does have Ubuntu 7.04 on it, however, it has the same problem as the IDE HD - seems to freeze when I select it from the grub.

Any help would be greatly appreciated.

BTW, all this started after I got really frustrated with the nvidia driver not working in Ubuntu 7.04.

I am still going to stick with Ubuntu / Kubuntu - I think it makes more sense than Windows!!

Thanks,
DB

---

