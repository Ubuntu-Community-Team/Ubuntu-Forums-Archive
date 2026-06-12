---
title: "How to mount partition created by VMware?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Balt603 on 2007-09-29
Hey,
         I installed VMware server in order to keep using Photoshop, and everthing there is running fine. However, I'd like to be able to drop files from ubuntu into the partition that VMware created for my xp pro vm. I've found lots of links about finding partitions using fdisk and mounting using fstab, which all seem straight forward. HOWEVER, when I "fdisk -l", I can see the extended partition listed that contains the VMware files, but no logical drives within it.

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29644   238115398+  83  Linux
/dev/sda2           29645       30401     6080602+   5  Extended
/dev/sda5           29645       30401     6080571   82  Linux swap / Solari

My question is: how do I find the logical drives in order to mount them in ubuntu? Is it using a proprietary file system or something that blocks me from doing this? I suppose I could just create another partition to use as a share and double copy between, but this is inelegant.

---

### Post by dwhitney67 on 2007-09-30
I would recommend installing (if you don't have it already), the SSHD (server) on your Ubuntu (aka host system), and under WinXP (aka guest system) install an SSH client application.  Then, while under WinXP, you can secure-copy (scp) files/directories from your guest OS.

Anyhow, that's how I do it between my Ubuntu host and my Fedora Core guests.

Btw, VMware uses a file(s) (not a partition) for your guest OS.  This file resides under your primary Ubuntu partition (/dev/sda1).

---

### Post by HermanAB on 2007-09-30
Yup, Vmware Server doesn't have file sharing built in - VMware Workstation does.  So the workaround is to use ssh or ftp as suggested above.  On Windoze I suggest using FileZilla, which has both a nice client and a server.

Cheers,

H.

---

### Post by Balt603 on 2007-09-30
Great, thanks for the help. 

So then I'm assuming that the partition is really telling me that the swap partition sda5 is really a logical drive of extended partition sda2?

That would explain why the sector info for each is the same...

---

