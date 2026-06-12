---
title: "OldWorldG3 install; scsi weirdness"
date: 2005-01-30
forum: Apple PPC Users
---

### Post by tonyB on 2005-01-30
My system: Mac7300 with G3 upgrade card; 2GB internal disk with MacOS9, 4GB external disk w/ MacOS8; 9GB external disk w/gentoo linux.  Installing ubuntu on 4GB disk.

I d/l'd the iso, md5 checked it, and burned it on a different system.  In order to get it to boot on my "7300" I had to set the size to 32000 and check the "no video driver" button.  The installer came up fine, and everything progressed in what seemed a normal manner.  When the partitioner came up, however, the disk addressing seemed fubar.  When I installed gentoo, the addresses were: sda = internal 2GB;
sdb = external 9GB disk;  sdc = external 4GB disk.  Under ubuntu the addressing was: scsi1(0,0,0) sda = 9GB disk;  scsi1(0,1,0) sdb = 4GB disk;  scsi2(0,0,0) sdc = 2GB disk.  I picked manual partitioning, selected sdb, and everything seemed to progress smoothly -- including the write-select light on the correct disk coming on when the disk was being written, I am happy to say.  After I got to the end of the CD phase of installation, I used gentoo linux to copy the kernel to the Linux Kernels folder in the System Folder on MacOS8 and then used MacOS9 to copy from MacOS8 to the appropriate MacOS9 folder.  Then I tried to boot into the ubuntu partition.  I tried several partition specifications -- although it is "really" on sdc8 -- and all of them failed with messages like: "VFS cannot mount root device sdc8"  and  "unable to mount root device on unknown-block(0,0)".  Some of the variations of boot parameters I tried just caused a hang during boot with no message.

This all seems rather weird to me, but then Hazel and Adam didn't raise any real smart male children.  Hopefully I've done something truly ignorant which someone can readily point out to me.  Whatever.  I will be greatful for any assistance since, at this point, I'm rather at a loss as to what to try next.

thank you muchly in advance,
tonyB


ACK!  I forgot to include that I booted into gentoo linux and mounted sdc8.  It appears to have the files one would expect at this point in the installation, e.g., hardware recognition logs identifying what stuff the installer found.  And, of course, the important fact that sdc8 does indeed hold an ext3 fs.

tonyB

---

### Post by heavyt on 2005-01-31
Try  using your initrd in the Bootx Options and putting your root  location in Kernel arguments section. Sound strange but it work for me on my mac clone (g3)

---

### Post by tonyB on 2005-01-31
[QUOTE=heavyt]Try  using your initrd in the Bootx Options and putting your root  location in Kernel arguments section. Sound strange but it work for me on my mac clone (g3)[/QUOTE]

Thanks heavyt!  You get the Golden Penguin award for the day. :)  I would never have figured to include the initrd in the BootX options, since I assumed that would put me back on the cdrom installer.  BootX is just one of the mysteries of life for me.

Many thanks again!

tonyB

---

### Post by heavyt on 2005-02-02
You're Welcome.

---

### Post by eby on 2005-11-25
[QUOTE=heavyt]Try  using your initrd in the Bootx Options and putting your root  location in Kernel arguments section. Sound strange but it work for me on my mac clone (g3)[/QUOTE]

Hello **heavyt**,
I too get "VFS cannot mount root device" with SCSI CD Drives. Could you post BootX how-to, step by step for newbies like me. Thanks.

---

