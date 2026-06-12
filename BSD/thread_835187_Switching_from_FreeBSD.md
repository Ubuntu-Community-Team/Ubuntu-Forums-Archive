---
title: "Switching from FreeBSD"
date: 2008-06-20
forum: BSD
---

### Post by lil_elvis2000 on 2008-06-20
Hello,
I'm having plenty of issues with my RAID 1 on my system. I'm running freeBSD on it. BUt when I copy or manipulate the large files on the mirror - the mirror falls apart (the drives disconnect) and it can occaisionally cause a panic (a crash). This can happen even when reading the files over a NFS mount, so not just a write issue at all.
My hardware is Celeron 800Mhz, 640MB RAM, MB don't know, 1X11Gig IDE drive (the OS drive / /usr swap), 2X320GB SATA drives, PCI 3COM NIC, PCI ATI video, PCI SiL 3512.
I'm waiting for the FreeBSD developers to get back to me on my problems. Looks to me like a problem with the meta writes with my configuration. Don't know if its a hardware issue. Have to check all connectors and cards and slots when I get time.

Anyone with similar hardware have any RAID issue with Linux. Which file system should one use. I see that there is XFS, maybe ZFS in the future and ext3.

---

### Post by lil_elvis2000 on 2008-06-20
Oh additionally, I was able to run the liveCD and mount the harddrives as read-only ufs2. So ubuntu can detect the disks. But will it have problems running a RAID?

BTW: the ufs2 option is not in the documentation for mount, that I can find. i only noticed in the message log when I ran dmesg.

---

### Post by PmDematagoda on 2008-06-20
You will have a hard time using ufs2 on Linux since from the way I remember it, the kernel only has the ability to read it and not write to it, so you may have to use drivers like ntfs-3g, but I have no idea if such drivers for ufs2 exist.

---

### Post by lil_elvis2000 on 2008-06-20
That's okay. As I can format one disk to ext3 copy my data from the other onto it and then format the other. then create my mirror...come to think of it..do I need to format the other one at all.

I need to check out how Xubuntu handles the KVM. freebsd gives me no end of trouble with it. Someone mentioned that its my BIOS and not the OS. But when I was using the liveCD it seemed to work better.

The liveCD seemed to take up quite a bit more RAM than FreeBSD does when running Xfce. Why is that?

---

