---
title: "Lost Windows after installing Ubuntu updates"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by 138742 on 2006-09-08
After updating Ubuntu I lost windows in Grub. I don't think it deleted it, but is there a way to back track a day? 

/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913       12030    81272835    f  W95 Ext'd (LBA)
/dev/sda3           12031       12161     1052226   82  Linux swap / Solaris
/dev/sda5            3825       12030    65914663+   c  W95 FAT32 (LBA)
/dev/sda6            1913        1976      514017   83  Linux
/dev/sda7            1977        2103     1020096   82  Linux swap / Solaris
/dev/sda8            2104        3251     9221278+  83  Linux
/dev/sda9            3252        3824     4602591   83  Linux


title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,5)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sda9 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sda9 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,5)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/sda9 ro quiet splash
initrd		/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,5)
kernel		/vmlinuz-2.6.15-23-386 root=/dev/sda9 ro single
initrd		/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/memtest86+.bin 
boot

Thanks,

---

### Post by ciscosurfer on 2006-09-08
This should help you out: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

