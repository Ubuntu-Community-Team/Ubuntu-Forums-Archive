---
title: "previous installed grub from mint15 reinstalled from ubuntu 13.04 no mint boot entry"
date: 2013-08-30
forum: Any Other OS
---

### Post by cebif on 2013-08-30
I installed Mint 15 which overwrote the grub MBR from Ubuntu. The menu worked for Linux but not for Haiku OS which would not boot. So I reinstalled grub from Ubuntu and can now boot into Haiku. The trouble is this left out the menu entry for Mint 15, so cannot boot it anymore. I think it might be easier to get back the entry for Mint than for Haiku, if I reinstalled grub from Mint, so how can I get Mint back?
 Something that may have a bearing on the problem is: the path to my Mint root partition when mounted in Ubuntu; /media/greg/8a4032d3-4413-432e-9137-00c83240cf7f/@
I do not know why the extra directory step "/@" after the drive uuid?
Ubuntu 13.04 root is on /devsda1. Mint 15 root is on /dev/sdb1. Haiku 0S is on /dev/sdc1. The MBR is on /dev/sda.
Notice how there is two uuids each for the root 1st partition and /home second partition on sdb.
> greg@greg-desktop:~$ blkid
/dev/sda1: UUID="908f5381-b90e-4970-801b-2e24e1611896" TYPE="ext4" 
/dev/sda2: UUID="d6a47ce8-df40-4820-bf2d-75cab34e7671" TYPE="ext4" 
/dev/sda3: UUID="79e6e638-6ca1-412a-a265-31bd946cf01b" TYPE="swap" 
/dev/sdb1: UUID="8a4032d3-4413-432e-9137-00c83240cf7f" UUID_SUB="7ae6658b-37df-4ed2-b016-fd6ca0f90c50" TYPE="btrfs" 
/dev/sdb2: UUID="9ff209d5-2f5c-4823-89db-f9d5201adf4f" UUID_SUB="13a21927-7a1f-4847-8f98-cf40557f5f7f" TYPE="btrfs" 
/dev/sdb3: UUID="d3695a85-dc10-420b-bd66-5700e9dc54d8" TYPE="swap" 
/dev/sdc1: LABEL="Haiku" UUID="1008f0e43aff10f5" TYPE="befs" 
/dev/sr0: LABEL="XPLANE10" TYPE="iso9660"
The extra uuid's are they the problem?
```
sudo update-grub
``` won't put it there even when the Mint partition is mounted. So if anyone can help I would be grateful.

---

### Post by oldfred on 2013-08-30
You need the insmod for btrfs as is is not one of the default file systems.

If you have the btrfs drivers and tools installed in Ubuntu and mount the Mint partition, then run os-prober in Ubuntu it should find the Mint install. 

Also you do need extra space for core.img. Most installs now have that with the settings for new 4K drives and SSDs, but core.img becomes very large with btrfs.

Also
 10-Way Linux File-System Comparison On Linux 3.10
[http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1)
BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
Linux 3.11 File-System Performance: EXT4, Btrfs, XFS, F2FS
[http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE](http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE)

---

### Post by cebif on 2013-08-31
Thanks for the the advise and links. I did not really understand what you meant by insmod. Could not find it with apt-get or synaptic. Could not find what package might contain it with synaptic. I already had most of the files associated with btrfs tools installed but installed a few more that dealt with btrfs. I had just read about os-prober a day ago but forgot what I read today. I know it is invoked by update-grub and had a vague recollection it had something to do with grub.cfg but could not remember how to run it manually and could not find in browser history what I read just a day ago. Anyway what I have done is copy the Mint 15 menu entry fron /boot/grub on the Mint partition, into the /etc/grub.d/40_custom in Ubuntu 13.04. I then ran the application grub-customizer and it found the Mint 15 entry. I had ran it before puting the Mint entry in 40_custom but it had not found it. That was after installing everything that looked close to dealing with btrfs. So here is the Mint menu entry I put put there:
> menuentry 'Linux Mint 15 Xfce 64-bit, 3.8.0-29-generic (/dev/sdb1)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod btrfs
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  8a4032d3-4413-432e-9137-00c83240cf7f
	else
	  search --no-floppy --fs-uuid --set=root 8a4032d3-4413-432e-9137-00c83240cf7f
	fi
	linux	/@/boot/vmlinuz-3.8.0-29-generic root=UUID=8a4032d3-4413-432e-9137-00c83240cf7f ro rootflags=subvol=@   quiet splash $vt_handoff
	initrd	/@/boot/initrd.img-3.8.0-29-generic
}
That worked and I am now writing this from Mint 15. There might have been a better way to do it. Maybe I should have put the menu entry in some other file in grub.d but don't know how. It looks time consuming and complicated. I suppose there might be a more automatic way I don't know about.

---

### Post by cebif on 2013-08-31
Maybe I should have installed Ubuntu 13.04 with ext4. According to the benchmarks in the links you gave. It is still mostly better than btrfs. I might not have had this trouble with grub then.

---

### Post by oldfred on 2013-08-31
I guess I could have been clearer. But the way you did it is a good way also.

If you look at your entry you have this as 6th line, which is the command you needed.
insmod btrfs

And I have run this so many times I do not post much anymore. It also runs the os-prober
sudo update-grub

I do not remember if it is btrfs or one of the other file systems, but you also need to install its tools to be able to run the equivalent of fsck which is just for ext family.

---

