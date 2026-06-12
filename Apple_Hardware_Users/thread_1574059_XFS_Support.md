---
title: "XFS Support"
date: 2010-09-13
forum: Apple Hardware Users
---

### Post by downindm on 2010-09-13
I have loaded Ubuntu 10.04 on my PPC mac, and I was under the impression that the XFS file system was supported out of the box.  I am trying to recover some data on 2 old IRIX SCSI drives.  I have both the drives on different addresses (3 & 4) and have the chain terminated properly.  When I go in to the Disk Utility, it shows my SCSI adapter but does not show either of the volumes attached to it, so I am unable to mount them.

Was I wrong in thinking XFS should just work or do I need to load some sort of package.  Or is it perhaps my Adaptec SCSI card is not supported?  I would figure the card is ok since Disk Utility seems to recognize it.

---

### Post by srs5694 on 2010-09-13
Post the output of "ls /dev/sd*" on this system, and tell us what other disks your computer has. If you've got only one other disk, then it will probably be /dev/sda (and all the partitions it contains). If there's then no /dev/sdb, that means that the disk isn't being detected. If /dev/sdb shows up but if there are no partitions (no /dev/sdb1, /dev/sdb2, and so on), then it means that the partition table isn't being recognized. As I understand it, IRIX used its own partition table. The Linux kernel does include SGI/IRIX partition table support, but I have no idea if it's compiled into a standard Ubuntu kernel, so it could be that it's not being recognized on your system.

---

### Post by downindm on 2010-09-14
Output of "ls /dev/sd*":

ls: cannot access /dev/sd*: No such file or directory

The computer has 2 internal HD... One on the primary IDE master (that is a Journaled HFS+ system with 2 partitions for OS X and OS 9).  The other drive is on the secondary IDE master and contains Ubuntu.  The 2 SCSI drives that were previously on a SGI running IRIX 5.3 I believe are hooked up externally via a PCI Adaptec AIC-7850 card.  Disk Utility shows the driver as "aic7xxx" and it appears that the driver for it is loaded as I can see the following when doing a "lsmod | grep scsi":

scsi_transport_spi     26921  1 aic7xxx

From what I had read, XFS support is supposed to be compiled in to the kernel... you only had to add it if you compiled it yourself - which I did not.  I just did a standard Ubuntu desktop install for PPC.  Could it be perhaps that the PPC version does not include the support?  How can I tell?

---

### Post by anubhavrocks on 2010-09-14
1. I think you need to insert the xfs module:
 
```
sudo modprobe xfs
```

2. If this does not work can you post the output of:

```
sudo lshw  -C disk
```

---

### Post by downindm on 2010-09-14
I tried the "sudo modprobe xfs" - and it didn't return an error, didn't seem to do anything.

Here's the output of "sudo lshw -c disk":
```
  *-disk                  
       description: ATA Disk
       product: Maxtor 7Y250P0
       vendor: Maxtor
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: YAR41BW0
       serial: Y649YX1E
       size: 233GiB (251GB)
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:mac
       configuration: apm=off mode=udma4 smart=on
  *-cdrom
       description: DVD reader
       product: PHILIPS CDD5101
       vendor: Philips
       physical id: 0
       bus info: ide@2.0
       logical name: /dev/hde
       logical name: /media/Ubuntu 10.04 LTS ppc
       version: A3.5
       serial: H92380R99LXVA
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
       configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hde
          logical name: /media/Ubuntu 10.04 LTS ppc
          capabilities: partitioned partitioned:mac
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted
  *-disk
       description: ATA Disk
       product: ST360021A
       vendor: Seagate
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 5.21
       serial: 3HR1VYT8
       size: 57GiB (61GB)
       capacity: 57GiB (61GB)
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:mac
       configuration: mode=udma5 smart=on

```It doesn't look like it's seeing the SCSI drives at all.  Also, here is the output of "sudo lsmod | grep xfs":

```

xfs                   617495  0 
exportfs                4173  1 xfs

```

---

### Post by srs5694 on 2010-09-14
It's almost certainly not seeing the SCSI drive. Try "cat /proc/scsi/scsi". If it returns information on your SCSI disk, then I'm wrong, but I expect you won't see anything.

You can also try "dmesg | grep scsi", preferably soon after booting, to return information on recent kernel activity returning SCSI devices, including SCSI host adapters. That may provide some clues.

It's unclear to me whether the disk isn't being detected because of a problem with the disk or with the host adapter you're using. The dmesg output may help clarify this issue.

---

### Post by downindm on 2010-09-14
Ok, I feel like an ***... Turns out the enclosure was not turned on - although the terminator was lit up, making me believe it was on and functioning.  I can now see the drives on /dev/sda and /dev/sdb.  Thanks for the help.

---

### Post by downindm on 2010-09-14
Ok, now I am able to see that the drives are there and I can see the various partitions (using the KDE Partition Manager) - how do I go about mounting them so I can copy the data off them.  I don't see an option to mount any of the partitions.

---

### Post by downindm on 2010-09-14
dmesg shows the following entries:

```
[   23.755573] sd 0:0:1:0: Attached scsi generic sg0 type 0
[   23.755850] sd 0:0:3:0: Attached scsi generic sg1 type 0
[   23.814113]  sda: sda1 sda2 sda9 sda11
[   23.826891]  sdb: sdb1 sdb2 sdb7 sdb8 sdb9 sdb11

```

---

### Post by anubhavrocks on 2010-09-14
Firstly you will need to install xfsprogs
```
 sudo aptitude install xfsprogs
```

Then use the mount command.Check the mount manpage.
man mount

---

### Post by downindm on 2010-09-14
I have installed xfsprogs and I am getting the following when trying to mount:

```
$ sudo mount -t xfs /dev/sda /media/sda
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```I have tried to mount all the partitions using the above but get the same message.

I have also tried the following:

```
$ sudo xfs_repair -n /dev/sda
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!

attempting to find secondary superblock...
...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................Sorry, could not find valid secondary superblock
Exiting now.

```

---

### Post by srs5694 on 2010-09-14
First, you should definitely *not* try mounting the main device (/dev/sda or /dev/sdb); only the partitions are likely to be mountable. Also, don't try using fsck on the disk, since it's conceivable this tool could do more harm than good.

I recommend you peruse the /usr/src/linux/Documentation/filesystems/xfs.txt file. (You'll need to have the Linux kernel source code installed to get this file -- or you can probably track it down online if you prefer.) It specifies a large number of mount options. Most of these don't seem likely to help, but some might. The inode64, noalign, and noattr2 options look particularly promising, on a first glance through the documentation. It's possible that the logdev and/or rtdev options will help out, but if so you'll need to know which devices to specify. If the disks used some sort of RAID configuration, perhaps sunit and/or swidth will be helpful.

I must emphasize that I'm just guessing about these XFS mount options; I've never tried to do what you're doing, so I don't know what the likely problems are once you start to actually mount the partitions.

---

### Post by downindm on 2010-09-15
Thanks, I found it online and will look at it and see if anything helps.  I actually tried mounting ALL the partitions (not just the main) and got no where.  I was trying also to use xfs_repair in the make no changes mode just to see if it found anything - which the result on all the partitions was the same as I posted above.

I do know the drives are OK as I was able to browse them on the SGI box - but I think there was an issue with the main IRIX install as I could only get as far as the standalone shell which is seriously limited.  Also, I don't have access to any install discs for it so I figured the best way to recover the data would be to mount them on Ubuntu and then copy the data over.

---

### Post by srs5694 on 2010-09-15
If you've got access to an SGI system, you may want to track down the IRIX equivalent of the fdisk and df utilities in Linux. That may help you determine which partition(s) hold actual data and which ones hold metadata or are otherwise less important. That could help you focus your efforts on the Linux side.

---

