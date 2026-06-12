---
title: "I am trying do an OS X usb stick boot able with ubuntu 12.04"
date: 2012-06-16
forum: Apple Hardware Users
---

### Post by lse123 on 2012-06-16
I am trying do an OS X usb stick boot able with ubuntu 12.04, well:
after creation always get 
"This disk you inserted was not readable by this computer." and usb stick is becoming non-usable...well?
what iso must use for the mac, the ...amd64+mac.iso?
```
Last login: Sat Jun 16 21:02:14 on console
mymac:~ new$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *120.0 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            119.2 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *8.1 GB     disk1
   1:                        EFI                         209.7 MB   disk1s1
   2:                  Apple_HFS mymac                   7.8 GB     disk1s2
mymac:~ new$ diskutil unmountDisk /dev/disk1
Unmount of all volumes on disk1 was successful
mymac:~ new$ sudo dd if=~/Downloads/ubuntu.img.dmg of=/dev/rdisk1 bs=1M
Password:
dd: bs: illegal numeric value
mymac:~ new$ sudo dd if=~/Downloads/ubuntu.img.dmg of=/dev/rdisk1 bs=1m
696+1 records in
696+1 records out
730116096 bytes transferred in 72.277344 secs (10101590 bytes/sec)
mymac:~ new$ diskutil eject /dev/disk1
Disk /dev/disk1 ejected
mymac:~ new$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *120.0 GB   disk0
   1:                        EFI                         209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            119.2 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *8.1 GB     disk1
   1:                        EFI                         209.7 MB   disk1s1
   2:                  Apple_HFS mymac                   7.8 GB     disk1s2
mymac:~ new$ diskutil unmountDisk /dev/disk1
Unmount of all volumes on disk1 was successful
mymac:~ new$ sudo dd if=~/Downloads/ubuntu.img.dmg of=/dev/rdisk1 bs=1m
Password:
696+1 records in
696+1 records out
730116096 bytes transferred in 62.675817 secs (11649088 bytes/sec)
mymac:~ new$ 

```

---

### Post by conbot on 2012-06-16
You want your Mac to boot your USB disk?

---

### Post by lse123 on 2012-06-16
yes

used macbook pro (first time used / learnt many about) on boot appears like something ReFit...

---

### Post by conbot on 2012-06-16
OK, what exactly did you do to "get OS X" on your flash drive?? Is this the installer?

---

### Post by lse123 on 2012-06-16
not os x but ubuntu on flash drive...

os x is in laptop not to get moved recreated.

ubuntu usb stick insert in mac to use linux from mac...boot from stick(flash drive).

---

### Post by rocklife on 2012-06-17
Wonderful file recovery software for Mac users

[http://www.applexsoft.com/](http://www.applexsoft.com/)

---

### Post by blueshead on 2012-06-19
Go [here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx") to make an Ubuntu USB stick that will boot in OSX..

---

