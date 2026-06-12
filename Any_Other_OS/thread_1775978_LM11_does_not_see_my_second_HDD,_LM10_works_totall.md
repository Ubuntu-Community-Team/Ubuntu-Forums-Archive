---
title: "LM11 does not see my second HDD, LM10 works totally fine"
date: 2011-06-05
forum: Any Other OS
---

### Post by anatolik on 2011-06-05
Hi,

I just upgraded my computer from Linux Mint 10 to Linux Mint 11 and I have a problem with my second HDD that is used as a storage. The symptom is - approximately in 9 of 10 boots Linux does not see my harddrive (/dev/sdb). I cannot mount /dev/sdb1 partition and I gparted shows that the disk is unpartitioned. Sometimes (1 of 10 boots) Linux Mint 11 loads fine and sees my disk.

I've never saw such problem with Linux Mint 10. I think this is somehow related to kernel/driver rather than to LinuxMint changes, so I think I would probably see the same issue on Ubuntu 11.04.


Here is the result of "sudo lshw -class storage -class disk"

```
  *-ide                   
       description: IDE interface
       product: 631xESB/632xESB IDE Controller
       vendor: Intel Corporation
       physical id: 1f.1
       bus info: pci@0000:00:1f.1
       version: 09
       width: 32 bits
       clock: 33MHz
       capabilities: ide bus_master
       configuration: driver=ata_piix latency=0
       resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:20c0(size=16)
  *-storage
       description: RAID bus controller
       product: 631xESB/632xESB SATA RAID Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       logical name: scsi2
       logical name: scsi3
       logical name: scsi4
       version: 09
       width: 32 bits
       clock: 66MHz
       capabilities: storage pm bus_master cap_list emulated
       configuration: driver=ahci latency=0
       resources: irq:19 ioport:20e0(size=8) ioport:20f8(size=4) ioport:20e8(size=8) ioport:20fc(size=4) ioport:2080(size=32) memory:f0204400-f02047ff
     *-disk:0
          description: ATA Disk
          product: ST3500630AS
          vendor: Seagate
          physical id: 0
          bus info: scsi@2:0.0.0
          logical name: /dev/sda
          version: 3.CH
          serial: 5QG2W6RM
          size: 465GiB (500GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=0007f186
     *-cdrom
          description: DVD-RAM writer
          product: CDDVDW TS-H653N
          vendor: TSSTcorp
          physical id: 1
          bus info: scsi@3:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/scd0
          logical name: /dev/sr0
          version: HB01
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: ansiversion=5 status=nodisc
     *-disk:1
          description: ATA Disk
          product: SAMSUNG HD154UI
          physical id: 0.0.0
          bus info: scsi@4:0.0.0
          logical name: /dev/sdb
          version: 1AG0
          serial: S1XWJ1KSB16490
          size: 1397GiB (1500GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=1cda849d-34f2-48c6-87c8-a65451b3f91f

```

Here is the result of "$ dmesg | grep sdb" for **successful** boot.

```
[    2.443190] sd 4:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.443261] sd 4:0:0:0: [sdb] Write Protect is off
[    2.443264] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.443295] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.489629]  sdb: sdb1
[    2.489845] sd 4:0:0:0: [sdb] Attached SCSI disk
[   14.333710] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   17.750643] EXT4-fs (sdb1): re-mounted. Opts: commit=0
[   38.443408] EXT4-fs (sdb1): re-mounted. Opts: commit=0

```

Does anybody have something similar? Are there any info that might be helpful to debug the problem?

---

### Post by srs5694 on 2011-06-05
Was your lshw output from a successful or an unsuccessful boot? On an unsuccessful boot, what happens when you type the following commands:

```

ls -l /dev/sd*
sudo fdisk -lu
sudo gparted -l

```

---

### Post by anatolik on 2011-06-05
> **srs5694 said:**
> Was your lshw output from a successful or an unsuccessful boot?

Sorry, just added more information to my previous post. The lshw/dmesg output is for successful boot. I'll reboot and post information for unsuccessful boot later.

---

### Post by anatolik on 2011-06-06
It took several reboots until I was able to reproduce the same problem. Here is output from the tools for the **unsuccessful boot**:

"sudo lshw -class storage -class disk"
```
  *-ide                   
       description: IDE interface
       product: 631xESB/632xESB IDE Controller
       vendor: Intel Corporation
       physical id: 1f.1
       bus info: pci@0000:00:1f.1
       version: 09
       width: 32 bits
       clock: 33MHz
       capabilities: ide bus_master
       configuration: driver=ata_piix latency=0
       resources: irq:17 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:20c0(size=16)
  *-storage
       description: RAID bus controller
       product: 631xESB/632xESB SATA RAID Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       logical name: scsi2
       logical name: scsi3
       logical name: scsi4
       version: 09
       width: 32 bits
       clock: 66MHz
       capabilities: storage pm bus_master cap_list emulated
       configuration: driver=ahci latency=0
       resources: irq:19 ioport:20e0(size=8) ioport:20f8(size=4) ioport:20e8(size=8) ioport:20fc(size=4) ioport:2080(size=32) memory:f0204400-f02047ff
     *-disk:0
          description: ATA Disk
          product: ST3500630AS
          vendor: Seagate
          physical id: 0
          bus info: scsi@2:0.0.0
          logical name: /dev/sda
          version: 3.CH
          serial: 5QG2W6RM
          size: 465GiB (500GB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=0007f186
     *-cdrom
          description: DVD-RAM writer
          product: CDDVDW TS-H653N
          vendor: TSSTcorp
          physical id: 1
          bus info: scsi@3:0.0.0
          logical name: /dev/cdrom
          logical name: /dev/cdrw
          logical name: /dev/dvd
          logical name: /dev/dvdrw
          logical name: /dev/scd0
          logical name: /dev/sr0
          version: HB01
          capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
          configuration: ansiversion=5 status=nodisc
     *-disk:1
          description: ATA Disk
          product: SAMSUNG HD154UI
          physical id: 0.0.0
          bus info: scsi@4:0.0.0
          logical name: /dev/sdb
          version: 1AG0
          serial: S1XWJ1KSB16490
          size: 1397GiB (1500GB)
          capabilities: gpt-1.00 partitioned partitioned:gpt
          configuration: ansiversion=5 guid=1cda849d-34f2-48c6-87c8-a65451b3f91f

```

"dmesg | grep sdb"
```
[    2.463151] sd 4:0:0:0: [sdb] 2930275055 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.463206] sd 4:0:0:0: [sdb] Write Protect is off
[    2.463208] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.463232] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.475160]  sdb: unknown partition table
[    2.475358] sd 4:0:0:0: [sdb] Attached SCSI disk
```


"ls -l /dev/sd*"
```
brw-rw---- 1 root disk 8,  0 2011-06-06 20:20 /dev/sda
brw-rw---- 1 root disk 8,  1 2011-06-06 20:20 /dev/sda1
brw-rw---- 1 root disk 8,  2 2011-06-06 20:20 /dev/sda2
brw-rw---- 1 root disk 8,  3 2011-06-06 20:20 /dev/sda3
brw-rw---- 1 root disk 8,  5 2011-06-06 20:20 /dev/sda5
brw-rw---- 1 root disk 8, 16 2011-06-06 20:20 /dev/sdb
cr-------- 1 root root 8, 17 2011-06-06 20:25 /dev/sdb1
```

"sudo fdisk -lu"
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f186

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39064547    19531250   83  Linux
/dev/sda2        78127102   976771071   449321985    5  Extended
/dev/sda3        39065600    78125055    19529728   83  Linux
/dev/sda5        78127104   976771071   449321984   83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1500.3 GB, 1500300828160 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930275055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  2930277167  1465138583+  ee  GPT
```


"sudo gparted -l"
```
======================
libparted : 2.3
======================
Invalid argument during seek for read on /dev/sdb
```
gparted starts a GUI tool where /dev/sdb marked as unallocated (1.36T).

---

### Post by srs5694 on 2011-06-07
OK, your lshw output is identical, but for some reason the kernel isn't recognizing your GUID Partition Table (GPT) on /dev/sdb on some boots. This is rather peculiar. My first thought, given the erratic nature of the problem, is that this may be a hardware fault; such problems are often erratic in much this way. Thus, I recommend you run a SMART utility on the disk. The smartctl text-mode tool and GSmartControl GUI tools are both in the repositories, and the Palimpsest Disk Utility is probably already installed and has a way to look at SMART data. Something may pop out (I believe GSmartControl and Palimpsest both flag specific trouble areas in pink or red), or you may want to run a long self-test on the drive if nothing seems bad. (You may need to leave it running for at least an hour or two.)

Another type of hardware fault could be in cabling. You can try unplugging the SATA cable at both ends and plugging it in again, in case it's worked itself loose. You could even try replacing the SATA cable. This is a bit of a shot in the dark, but it might help.

My second suggestion is to install the gdisk package from the repositories and use it to view the partition table on the disk, as in "sudo gdisk -l /dev/sdb". There's also a verify function ("v" on the main gdisk menu if you launch it without "-l", or use the sgdisk program instead of gdisk and pass it "-v", as in "sgdisk -v /dev/sdb"), which checks for data structure inconsistencies and reports on them. It's conceivable that there's a subtle GPT data structure corruption that's causing the kernel problems on some boots but not others (although why the inconsistency I can't say). This test is likely to be quicker than a full SMART self-test run, so you might want to do it first.

---

### Post by anatolik on 2011-06-12
Here is my session:

```
$ sudo smartctl --all /dev/sdb
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F2 EG series
Device Model:     SAMSUNG HD154UI
Serial Number:    S1XWJ1KSB16490
Firmware Version: 1AG01118
User Capacity:    1,500,301,910,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Thu Jun  9 22:41:03 2011 PDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (19807) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (  34) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   099   065   051    Pre-fail  Always       -       502
  3 Spin_Up_Time            0x0007   072   072   011    Pre-fail  Always       -       9150
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1168
  5 Reallocated_Sector_Ct   0x0033   020   020   010    Pre-fail  Always       -       3494
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       3851
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1138
 13 Read_Soft_Error_Rate    0x000e   099   069   000    Old_age   Always       -       454
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       6453
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   073   063   000    Old_age   Always       -       27 (Lifetime Min/Max 18/29)
194 Temperature_Celsius     0x0022   071   062   000    Old_age   Always       -       29 (Lifetime Min/Max 18/30)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       79358246
196 Reallocated_Event_Count 0x0032   016   016   000    Old_age   Always       -       3494
197 Current_Pending_Sector  0x0012   100   065   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   099   091   000    Old_age   Always       -       3665
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```


```
$ sudo smartctl --attributes --log=selftest --quietmode=errorsonly /dev/sdb
[sudo] password for anatol: 
Short INQUIRY response, skip product id
```
This is weird, something wrong with my disk?

```
$ sudo smartctl --all /dev/sdb
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

Short INQUIRY response, skip product id
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
anatol@anatol-desktop ~ $ sudo smartctl --all -T permissive /dev/sdb
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

Short INQUIRY response, skip product id
SMART Health Status: OK
Read defect list: asked for grown list but didn't get it

Error Counter logging not supported
Device does not support Self Test logging
```

```
$ sudo fsck.ext4 -fv /dev/sdb1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
$ sudo mke2fs -n /dev/sdb1
mke2fs 1.41.14 (22-Dec-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
91578368 inodes, 366284637 blocks
18314231 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
11179 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848
$ sudo e2fsck -f -b 294912 /dev/sdb1
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
$ sudo mount -o sb=20480000 /dev/sdb1
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

anatol@anatol-desktop ~ $ dmesg | tail
[205220.094269] end_request: I/O error, dev sdb, sector 0
[205220.094299] sd 4:0:0:0: [sdb] Unhandled error code
[205220.094301] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[205220.094304] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[205220.094310] end_request: I/O error, dev sdb, sector 0
[205301.243764] sd 4:0:0:0: [sdb] Unhandled error code
[205301.243768] sd 4:0:0:0: [sdb]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[205301.243772] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 02 71 00 22 00 00 02 00
[205301.243782] end_request: I/O error, dev sdb, sector 40960034
[205301.243795] EXT4-fs (sdb1): unable to read superblock
```

I cannot mount the disk now....


... RESTART THE COMPUTER ...

And now the disk looks fine:
```
$ sudo fsck.ext4 -fv /dev/sdb1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sdb1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? yes

STORAGE: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

    1540 inodes used (0.00%)
       2 non-contiguous files (0.1%)
       1 non-contiguous directory (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 528/985/17
304954335 blocks used (83.26%)
       0 bad blocks
     121 large files

    1348 regular files
     183 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
    1531 files





$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 2930277168 sectors, 1.4 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1CDA849D-34F2-48C6-87C8-A65451B3F91F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 2930277134
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34      2930277134   1.4 TiB     0700 





$ sudo sgdisk -v /dev/sdb1
Creating new GPT entries.
No problems found. 2930277034 free sectors (1.4 TiB) available in 1
segments, the largest of which is 2930277034 (1.4 TiB) in size
```


I feel like my HDD is dying. From other side I restarted machine several times already and in every case disk was mounted fine. I need more time to reproduce this problem with the harddrive or make sure that smartctl fixed it.

---

### Post by srs5694 on 2011-06-12
The smartctl utility doesn't fix problems; it's a diagnostic tool only.

Although your smartctl output claimed that your disk passed, there were several values in your output that I found suspicious:

```

  1 Raw_Read_Error_Rate     0x000f   099   065   051    Pre-fail  Always       -       502
  5 Reallocated_Sector_Ct   0x0033   020   020   010    Pre-fail  Always       -       3494
 13 Read_Soft_Error_Rate    0x000e   099   069   000    Old_age   Always       -       454
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       6453
196 Reallocated_Event_Count 0x0032   016   016   000    Old_age   Always       -       3494

```

Unfortunately, I'm not an expert on SMART utilities, and many of these values can be difficult to interpret. Thus, I recommend you research this more. You might also want to use smartctl, GSmartControl, or Palimpsest Disk Utility to run an active test. You can run either short or long tests, which take a couple of minutes or several hours, respectively.

It's also possible that there's a hardware problem that's not in the disk -- a loose or bad cable or a flaky disk controller circuit, for instance.

---

### Post by anatolik on 2011-08-22
Finally my HDD died. It rejects to mount neither under 2.6.32 nor 2.6.38 kernel. I believe that the problem was with HDD, not with kernel or Linux itself.

---

