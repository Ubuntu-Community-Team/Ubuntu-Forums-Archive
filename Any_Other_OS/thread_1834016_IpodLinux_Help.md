---
title: "IpodLinux Help"
date: 2011-08-26
forum: Any Other OS
---

### Post by 7cardcha on 2011-08-26
Using these [http://mikesubuntu.com/2007/09/how-to-install-ipodlinux-on-your-ipod/]("http://mikesubuntu.com/2007/09/how-to-install-ipodlinux-on-your-ipod/") I installed IpodLinux on my ipod nano 1g. I followed the instructions to the letter

Here is a log of ./installer.sh

(I can't get the whole log)

First it says installing in 5 4 3 2 1 then starts installing
then there is a million errors and it seems to work

/tar: userland/modules: Cannot change ownership to uid 0, gid 0: Operation not permitted
/bin/tar: userland: Cannot change ownership to uid 0, gid 0: Operation not permitted
/bin/tar: Exiting with failure status due to previous errors
./installer.sh: line 302: tar_err: command not found
Installing bootloader...
ipodpatcher v0.9 with v1.0 bootloaders - (C) Dave Chapman 2006-2007
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[INFO] Reading partition table from /dev/sdb
[INFO] Sector size is 512 bytes
[INFO] Part    Start Sector    End Sector   Size (MB)   Type
[INFO]    0              63        160649        78.4   Empty (0x00)
[INFO]    1          160656       3999742      1874.6   W95 FAT32 (0x0b)
[INFO] Ipod model: 1st Generation Nano ("winpod")
[INFO] Reading original firmware...
[INFO]  Wrote 5620224 bytes to firmware partition
[INFO] Bootloader loader.bin written to device.
Your iPod was mounted before the installation started. If you want
the installer to umount and restart it for you, press y. Please make
sure that you're not using any files, directories or partitions on
your iPod before continuing.
Restart iPod? y
Installation done.

After this the ipod boots to a bootloader and let me choose between Apple OS, iPod Linux, Disk Mode and sleep

Booting up Apple OS works fine but iPod linux returns this error
Kernel panic : VFS(Or maybe its UFS hard to read): Unable to mount root fs on 03:02
Then it stays on that screen until it runs out of power or you restart. I have tried th install 3 times. Please help.

---

