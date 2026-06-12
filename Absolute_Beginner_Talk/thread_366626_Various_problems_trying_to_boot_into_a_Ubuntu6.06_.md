---
title: "Various problems trying to boot into a Ubuntu6.06 LTS installation"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by cygnus81 on 2007-02-21
Hi everyone,

I recently obtained an Ubuntu CD (6.06 LTS).

I have 3 HD's:
IDE0: 20GB HD NTFS, with no OS on it.
IDE1: 40GB HD NTFS, with Windows XP on it (running fine).
IDE2: 10GB HD EXT3, with Ubuntu installed (problem here..).

I can boot from the LiveCD just fine. And even managed to mount and access both the disk on IDE0 (ntfs, no os) and the disk on IDE2 (ext, ubuntu) from Ubuntu (LiveCD).

I installed grub onto the Ubuntu disk.
The device map it created maps hd2 to hdd (which is the Ubuntu disk on IDE2).

When booting from IDE2 (using the BIOS boot menu) I got the grub menu alright. However, I get the following (probably not the exact words):
```

root (hd2,0)
    Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdd1 ro quiet splash
    Error 17: Cannot mount selected partition.

```

I tried to *find /boot/grub/stage1* and got "(hd0,1)" :confused: .

So I went on and tried manually:
```

root (hd0,1)
    Filesystem type ext3 bla bla bla all ok here.
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hdd1 ro

```

and got this:
```

VFS: Cannot open root device "hdd1" or unknown-block (0,0)
Please append a correct "root" boot option
Kernel panic - not syncing: VFS: unable to mount root fs in unknown-block (0,0)

```

Again, the filesystem seems ok - I can do *cat (hd0,1)/boot/grub/.......* .

Help?

---

### Post by cygnus81 on 2007-02-21
Well.. nevermind. Got it.

I simply forgot the *initrd /boot/initrd.img-2.6.15-26-386* line just before *boot*.

And appearently, booting using the BIOS boot menu changes the order of disks (logically of course). Somehow.. 
When I booted from the CDROM, Ubuntu was installed on (hd2).
When I booted from IDE2, Ubuntu was (surprisingly) on (hd0).

Moving on to the next problem - internet connection :arrow: .........

---

