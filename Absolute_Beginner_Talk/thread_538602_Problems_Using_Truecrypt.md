---
title: "Problems Using Truecrypt"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by padamon on 2007-08-30
I am using Truecrypt 4.3a on Feisty.
When I try to mount my volume (that I made on Vista) it won't mount. 
It's called temp and it's in my home folder.

$ truecrypt -u temp /media/mnt
Enter password for '/home/padamon/temp': 
mount: wrong fs type, bad option, bad superblock on /dev/mapper/truecrypt1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Mount failed
padamon@pony:~$ dmesg | tail
[26312.196000] EXT3 FS on dm-0, internal journal
[26312.196000] EXT3-fs: mounted filesystem with ordered data mode.
[27170.568000] kjournald starting.  Commit interval 5 seconds
[27170.568000] EXT3 FS on dm-0, internal journal
[27170.568000] EXT3-fs: mounted filesystem with ordered data mode.
[27703.468000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value
[30694.420000] kjournald starting.  Commit interval 5 seconds
[30694.420000] EXT3 FS on dm-0, internal journal
[30694.420000] EXT3-fs: mounted filesystem with ordered data mode.
[31592.500000] EXT3-fs: Unrecognized mount option "uid=1000" or missing value

I have no idea what to do. :S

---

### Post by FleetAdmiral74 on 2007-08-30
try a 'man truecrypt' command, and see if it tells you how to specify the file system type.

Although unless you installed extra software, you cannot write to an NTFS by default (if thats what you used, instead of FAT)

---

### Post by capink on 2007-09-02
have you tried using:

```
truecrypt -u --filesystem ntfs temp /media/mnt
```

---

### Post by padamon on 2007-09-06
It is an ntfs file system. It's also 'dynamic'.  And when I put in the code capink provided, it gives the same message.

I tried to google some help with the dynamic filesystem and I got the impression dynamic is only supported on Windows. So I guess my only option is to open them in windows?

Thanks for your guys' help, anyways. I probably wouldn't have been able to correlate the problem with the ntfs thing.

---

