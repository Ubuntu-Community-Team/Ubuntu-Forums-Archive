---
title: "Unable to install Ubuntu 18.04 on mac, gparted fails"
date: 2019-11-09
forum: Apple Hardware Users
---

### Post by leep on 2019-11-09
I am trying to install Ubuntu 18.04 on an old MBP 2008.
I have a bootable USB stick, and the live demo starts and works perfectly.
I already had a previous version installed, but the SSD HD failed, and had to replace it.
So my situation is: a completely new SSD HD, and a live Ubuntu USB.
The mac boots correctly, and I can start the installation without any problem, but after selecting all the options, when gParted tries to create the required partition on the disk I obtain an "Impossible to format as ext4" error.

I tried to edit the disk partitions "manually" using gParted, and the error is a little bit more detailed, but I cannot understand it anyway:

```
GParted 0.30.0 --enable-libparted-dmraid --enable-online-resize

Libparted 3.2
Delete /dev/sda2 (unknown, 446.63 GiB) from /dev/sda  00:00:00    ( SUCCESS )
     	
calibrate /dev/sda2  00:00:00    ( SUCCESS )
     	
path: /dev/sda2 (partition)
start: 1050624
end: 937701375
size: 936650752 (446.63 GiB)
delete partition  00:00:00    ( SUCCESS )

========================================
Create Primary Partition #1 (ext4, 446.63 GiB) on /dev/sda  00:05:57    ( ERROR )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sda2 (partition)
start: 1050624
end: 937701375
size: 936650752 (446.63 GiB)
clear old file system signatures in /dev/sda2  00:00:00    ( SUCCESS )
     	
write 512.00 KiB of zeros at byte offset 0  00:00:00    ( SUCCESS )
write 4.00 KiB of zeros at byte offset 67108864  00:00:00    ( SUCCESS )
write 4.00 KiB of zeros at byte offset 274877906944  00:00:00    ( SUCCESS )
write 512.00 KiB of zeros at byte offset 479564660736  00:00:00    ( SUCCESS )
write 4.00 KiB of zeros at byte offset 479565119488  00:00:00    ( SUCCESS )
write 8.00 KiB of zeros at byte offset 479565176832  00:00:00    ( SUCCESS )
flush operating system cache of /dev/sda  00:00:00    ( SUCCESS )
set partition type on /dev/sda2  00:00:01    ( SUCCESS )
     	
new partition type: ext4
create new ext4 file system  00:05:55    ( ERROR )
     	
mkfs.ext4 -F -O ^64bit -L '' '/dev/sda2'  00:05:55    ( ERROR )
     	
64-bit filesystem support is not enabled. The larger fields afforded by this feature enable full-strength checksumming. Pass -O 64bit to rectify.
Discarding device blocks: failed - Remote I/O error
Creating filesystem with 117081344 4k blocks and 29278208 inodes
Filesystem UUID: edd6ec08-c695-4978-b70a-501266be5897
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000

Allocating group tables: done
Writing inode tables: done
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information:
mke2fs 1.44.1 (24-Mar-2018)

Warning, had trouble writing out superblocks.

========================================
```

Can anyone help me?
Thank you in adavnce,
Simone

---

### Post by leep on 2019-11-09
Is it possible that my system doesn`t support a 64bit installation and thus fails?

---

### Post by jeremy31 on 2019-11-09
Move to Apple Hardware

---

### Post by leep on 2019-11-09
Are you suggesting that the HD might not be compatible with my Mac?

---

### Post by uRock on 2019-11-09
> **leep said:**
> Are you suggesting that the HD might not be compatible with my Mac?

No, it was moved to the Apple Hardware support, as Apple's hardware tends to offer complications that other systems don't have. This subforum typically gets more attention from those who're more proficient in Apple's hardwares.

---

### Post by leep on 2019-11-09
:) Sorry didn't get it.

---

### Post by oldfred on 2019-11-09
Did you update firmware on SSD. Many have had to do that with PCs, even with new SSDs.
Do not know Mac and what firmware you may have.

Installed Lubuntu 18.04 LTS on a MacBook Air 1,1 (early 2008) 
[https://ubuntuforums.org/showthread.php?t=2402179](https://ubuntuforums.org/showthread.php?t=2402179)
Old Mac with core2duo & 32 bit UEFI
[https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/)

---

### Post by leep on 2019-11-11
No I did not, this is something I never thought about. I'll check with the manufacturer how to perform this update.

---

