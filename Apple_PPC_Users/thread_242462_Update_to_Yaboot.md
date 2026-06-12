---
title: "Update to Yaboot"
date: 2006-08-23
forum: Apple PPC Users
---

### Post by avtolle on 2006-08-23
There is an updated Yaboot; I have downloaded, installed and rebooted without incident. FYI, I don't dual boot; Ubuntu 6.06.1 only.

---

### Post by gnumac on 2006-08-24
The yaboot update totally crashed my G5.

Running Dual Boot. 2.0 Ghz G5 with Mac Os X 10.4.x and Dapper.

After restart  I got light gray screen. 

Starting from cd with rescue-powerpc64 and reinstall bootloader gave no success.

Starting the live cd and then
```
sudo -s 
mount -a 
mkdir real_root_drive
mount -t /dev/sda3 /mnt/real_root_drive
yabootconfig --chroot /mnt/real_root_drive -r /dev/sda3 -b /dev/sda2 
```

was neither success.
Booting into OPenFirmware and then
```
boot devalias sd2:/boot/vmlinux
```
didn't work either.

Now I'm about to give up and reinstall the system but as I did that after the X-org update crashed my X-server yesterday I'm  a bit relunctant
](*,) 
Anyone got any ideas?

[EDIT] I did a reinstall.

---

