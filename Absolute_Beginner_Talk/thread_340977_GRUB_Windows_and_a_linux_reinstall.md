---
title: "GRUB Windows and a linux reinstall"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by tophatandy on 2007-01-18
OK.

so.. recently had a lot of trouble with wireless on my ubuntu (which i would still love help with btw..cant get my card to work with my WPA-PSK with TKIP in 6.10) so I decided to completely wipe, reinstall windows first then 6.06 and upgrade to 6.10.. but sadly after I got done installing windows (which took a while) I installed linux and to my suprise it had wiped the entire hard disk and installed linux over everything.. so I say to myself.. no problem.. I will pop in the live cd partition it again and set up windows. So i did that but now I cant boot into Linux, although the partition and the data is still there..is there anything I can do to get GRUB up and running without wiping the linux partition and reinstalling linux?

would love any help I can get.

Thanks

=]

---

### Post by seshomaru samma on 2007-01-18
Boot from a live CD
open a terminal 
then go:
```
grub
```
then:
```
find /boot/grub/stage1
```
replace the question marks in the next command with the output of the last command(probably hd0,1):
```
root (hd?,?)
```
then:
```
setup (hd0)
```
finally
```
quit
```

---

### Post by tophatandy on 2007-01-18
i am in live cd right now and after inputing```
find /boot/grub/stage1
```i get this```
Error 15: File not found
``` am I not doing something right here?

thanks for the help.

---

### Post by seshomaru samma on 2007-01-18
strange
are you sure you typed the first command ? 
> grub

maybe your windows installation wiped your linux out? 
whats your fdisk?
```
sudo fdisk -l
```

---

### Post by Zaffe on 2007-01-18
For the WPA thing read [this]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")

---

### Post by tophatandy on 2007-01-18
alright. I typed this```
sudo fdisk -l
```and got this```
Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        6545    52572681   83  Linux
/dev/hda2   *        6546       24605   145066950    7  HPFS/NTFS
/dev/hda3           24606       24792     1502077+   5  Extended
/dev/hda5           24606       24792     1502046   82  Linux swap / Solaris

``` 
yep. I typed grub first.
Thanks

---

### Post by seshomaru samma on 2007-01-18
I see Linux is still there but for some reason there is no grub,
I think you need to reinstall brub
please read[ this ]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub")

for a complete understanding of grub , read [this ]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by tophatandy on 2007-01-20
well just decided to wipe again..

thanks for the wpa thing.. am going to try that.

thanks once again.

=]

---

