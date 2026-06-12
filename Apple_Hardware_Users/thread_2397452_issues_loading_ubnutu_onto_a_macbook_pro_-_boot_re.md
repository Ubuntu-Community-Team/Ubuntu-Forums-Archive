---
title: "issues loading ubnutu onto a macbook pro - boot repair txt file attached"
date: 2018-07-29
forum: Apple Hardware Users
---

### Post by paddywaddywaterloo on 2018-07-29
Hi Guys, I have a 2012 macbook pro

It was running great, until apples last update about a month ago, during the update the laptop through up a lot of kernal codes before Dying

I have a new sshd for this and anything I have tried via apple to sort it isnt working, I have a time machine and back ups etc, problem seems to be with its boot firm ware

I had ubuntu a few years ago before I purchased this mac, and now I'd like to go back to Ubuntu.

I installed the bootable disk direct to the hdd and powered it up, this is the code i got on screen from terminal : 

[COLOR=#b22222]error: failure reading sector 0x57c480 from 'hd1'
error: you need to load the kernal first.

press any key to continue....[/COLOR]

Is there any way of re programming the boot firmware to take ubuntu? 

[COLOR=#b22222]I ran the boot repair [https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/)[/COLOR]

[COLOR=#000080]below is the txt file it gave me 
[/COLOR][Thank you in advance] 

 ```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]




============================= Boot Info Summary: ===============================


 => ISOhybrid (Syslinux 4.05 and higher) is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: /dev/sda1 already mounted or mount point busy.


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *              0     1,449,983     1,449,984  17 Hidden NTFS / HPFS




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/sda1        2017-10-29-00-56-18-00                 iso9660    Boot-Repair-Disk 64bit
/dev/zram0       3d0bc82f-da6d-437b-9759-dad71f850c3d   swap       
/dev/zram1       0831b775-6ed3-4bd6-9bea-91a12367b90a   swap       
/dev/zram2       7031e4cd-8d20-414d-8cd5-b8944300249f   swap       
/dev/zram3       a0451830-cdf5-46fb-a638-073355bf50d6   swap       


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root  9 Jul 29 21:20 ata-HL-DT-ST_DVDRW_GS31N_K06C97N3851 -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 29 21:23 ata-PNY_CS900_120GB_SSD_PNY12180007850101739 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 29 21:23 ata-PNY_CS900_120GB_SSD_PNY12180007850101739-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 Jul 29 21:23 wwn-0x5f8db4c121801739 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 29 21:23 wwn-0x5f8db4c121801739-part1 -> ../../sda1


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)




======================== Unknown MBRs/Boot Sectors/etc: ========================


Unknown BootLoader on sda1


00000000  33 ed 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |3...............|
00000010  90 90 90 90 90 90 90 90  90 90 90 90 90 90 90 90  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  68 03 00 00 00 00 00 00  67 45 8b 6b 00 00 80 00  |h.......gE.k....|
000001c0  01 00 17 3f a0 c3 00 00  00 00 00 20 16 00 00 00  |...?....... ....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200






ADDITIONAL INFORMATION :
=================== log of boot-repair 20180729_2123 ===================
boot-repair version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4
Error: Invalid partition table - recursive partition on /dev/sda.
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 1oct2017, zesty, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory


=================== os-prober:




=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="2017-10-29-00-56-18-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="6b8b4567" PTTYPE="dos" PARTUUID="6b8b4567-01"
/dev/zram0: UUID="3d0bc82f-da6d-437b-9759-dad71f850c3d" TYPE="swap"
/dev/zram1: UUID="0831b775-6ed3-4bd6-9bea-91a12367b90a" TYPE="swap"
/dev/zram2: UUID="7031e4cd-8d20-414d-8cd5-b8944300249f" TYPE="swap"
/dev/zram3: UUID="a0451830-cdf5-46fb-a638-073355bf50d6" TYPE="swap"




=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] Resetting Apple AirPort card (left enabled by EFI)
SecureBoot maybe enabled.




=================== PARTITIONS & DISKS:






=================== parted -lm:


BYT;
/dev/sda:120GB:scsi:512:512:unknown:ATA PNY CS900 120GB:;


BYT;
/dev/zram3:770MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:770MB:770MB:linux-swap(v1)::;


BYT;
/dev/zram1:770MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:770MB:770MB:linux-swap(v1)::;


BYT;
/dev/zram2:770MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:770MB:770MB:linux-swap(v1)::;


BYT;
/dev/zram0:770MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:770MB:770MB:linux-swap(v1)::;


=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs 629.3M
sda   disk iso9660  111.8G Boot-Repair-Disk 64bit
sda1  part iso9660    708M Boot-Repair-Disk 64bit
sr0   rom            1024M
zram0 disk            734M
zram1 disk            734M
zram2 disk            734M
zram3 disk            734M


KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      0  0  0 running /cdrom
sda1     0  0  0
sr0      1  0  1 running
zram0    0  0  0         [SWAP]
zram1    0  0  0         [SWAP]
zram2    0  0  0         [SWAP]
zram3    0  0  0         [SWAP]




=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2979064k,nr_inodes=744766,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=601252k,mode=755)
/dev/sda on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=27,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14551)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=601248k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)




=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 dvd dvdrw ecryptfs fb0 fd full fuse fw0 gpiochip0 hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 iio:device0 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control


=================== df -Th:


Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  2.9G     0  2.9G   0% /dev
tmpfs          tmpfs     588M  8.8M  579M   2% /run
/dev/sda       iso9660   708M  708M     0 100% /cdrom
/dev/loop0     squashfs  630M  630M     0 100% /rofs
/cow           overlay   2.9G   61M  2.9G   3% /
tmpfs          tmpfs     2.9G     0  2.9G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     2.9G     0  2.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     2.9G  100K  2.9G   1% /tmp
tmpfs          tmpfs     588M  8.0K  588M   1% /run/user/999


=================== fdisk -l:
Disk /dev/loop0: 629.3 MiB, 659873792 bytes, 1288816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6b8b4567


Device     Boot Start     End Sectors  Size Id Type
/dev/sda1  *        0 1449983 1449984  708M 17 Hidden HPFS/NTFS








Disk /dev/zram0: 734 MiB, 769601536 bytes, 187891 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/zram1: 734 MiB, 769601536 bytes, 187891 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/zram2: 734 MiB, 769601536 bytes, 187891 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/zram3: 734 MiB, 769601536 bytes, 187891 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Error: no partitions


** (zenity:24188): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.




=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems




=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2018-07-29
Moved to Apple sub-forum where those with Mac may be able to help.
Also please use code tags for longer txt or terminal output. With Boot-Repair better to just post link it gives when running report.
And with Boot-Repair better to use ppa with Ubuntu live installer as you get a newer version.

Do not know Mac, but it looks like you dd'd the live installer to your SSD, not to a flash drive, so you could then do a full install to SSD.

       Install to Mac
[https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640](https://ubuntuforums.org/showthread.php?t=2365454&p=13663640#post13663640)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) 
    
       FAT32 format  & label with boot flag on Mac
[https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation](https://askubuntu.com/questions/934783/untetbootin-not-recognising-usb-drive-for-ubuntu-installation) 
    
Most of the UEFI boot info in link in my signature is for PCs, but some general UEFI data may apply.

Mac is normally a UEFI install.
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by paddywaddywaterloo on 2018-07-29
Thank you oldfred

I will go through all the information you provided now- I appreciate the help and quick response

Thank you for the tips for using tags, I'm new to the forum, I will be more mindful in future

---

