---
title: "lost swap after upgrade to Edgy"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by idrinkwhisky on 2006-12-19
Hi,

after upgrading to Edgy I  noticed that I have no swap drive anymore.
My etc/fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda2 -- converted during upgrade to edgy
UUID=3f5d3f93-8731-4329-997a-820a4afcdc6f / ext3 defaults,errors=remount-ro 0 1

# /dev/sda5 -- converted during upgrade to edgy
UUID=7f02fa9a-c0ab-47f9-8fd4-71176ed71ecc none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I browsed the ubuntuforums and somebody suggested removing
```
UUID=7f02fa9a-c0ab-47f9-8fd4-71176ed71ecc none swap sw 0 0
```

and replacing with 
```
/dev/sda5
```

I tried that but after reboot I still have no swap. I entered command free and it shows that my swap has size zero.

PLEASE help. Thank you guys

---

### Post by 5-HT on 2006-12-19
What happens when you enable the swap partition?
```
 sudo swapon -v /dev/sda5
```If that doesn't work, could you try ```
sudo swapon -av
``` and reply with the error messages?

When I installed Edgy, the UUID entries in my fstab and menu.lst were all screwed up and I lost my swap among other things. Not sure why explicitly stipulating the device name in fstab isn't working for you, but it might be worth a shot to see if the UUID for sda5 was correct and that it is your swap partition.

To double check the partition's UUID, 
```
 ls -l /dev/disk/by-uuid 
```To double check the swap partition,
```
 sudo fdisk -l 
```

Was the UUID in your fstab correct? If not, what happens after a reboot when you use the correct one  (you may need to do another 'sudo swapon -av')?

---

### Post by idrinkwhisky on 2006-12-19
first of all, thank you very much for your reply. I tried to do what you suggested but it did not quite work. 

1) When i punch in ls -l /dev/disk/by-uuid I get:

```
idrinkwhisky@whisky-laptop:~$  ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2006-12-19 12:16 0074FB5874FB4EC2 -> ../../sda1
lrwxrwxrwx 1 root root 10 2006-12-19 12:16 241AE3CB093902A2 -> ../../sda4
lrwxrwxrwx 1 root root 10 2006-12-19 12:16 3f5d3f93-8731-4329-997a-820a4afcdc6f -> ../../sda2
lrwxrwxrwx 1 root root 10 2006-12-19 12:16 b6a0159a-2caa-42c4-b9a7-2487652b2ee3 -> ../../sda5
```

2) So I noticed that the UUID for sda5 was incorrect in my original fstab. I change fstab as follows

```
# /dev/sda5 -- converted during upgrade to edgy
#UUID=7f02fa9a-c0ab-47f9-8fd4-71176ed71ecc none swap sw 0 0
UUID=b6a0159a-2caa-42c4-b9a7-2487652b2ee3  none swap sw 0 0

```

3) when I do sudo swapon -v /dev/sda5 or sudo swapon -av i get the following errors:

```
idrinkwhisky@whisky-laptop:~$ sudo swapon -v /dev/sda5
Password:
swapon on /dev/sda5
swapon: /dev/sda5: Device or resource busy

idrinkwhisky@whisky-laptop:~$ sudo swapon -av
swapon on /dev/disk/by-uuid/b6a0159a-2caa-42c4-b9a7-2487652b2ee3
swapon: /dev/disk/by-uuid/b6a0159a-2caa-42c4-b9a7-2487652b2ee3: Device or resource busy

```

I hope you can help me further. Thanks a lot

---

### Post by taurus on 2006-12-19
What's the output of this command and your /etc/fstab again?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by idrinkwhisky on 2006-12-19
thanks for the help. 
fdisk -l gives:

```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        4355    24740100   83  Linux
/dev/sda3            7109        7296     1510110    5  Extended
/dev/sda4            4356        7108    22113472+   7  HPFS/NTFS
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

my entire fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda2 -- converted during upgrade to edgy
UUID=3f5d3f93-8731-4329-997a-820a4afcdc6f / ext3 defaults,errors=remount-ro 0 1

# /dev/sda5 -- converted during upgrade to edgy
#UUID=7f02fa9a-c0ab-47f9-8fd4-71176ed71ecc none swap sw 0 0
#/dev/sda5   none   swap   sw   0   0

UUID=b6a0159a-2caa-42c4-b9a7-2487652b2ee3  none swap sw 0 0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by taurus on 2006-12-19
You need to remove the # sign in front of /dev/sda5 so it would look like this in your /etc/fstab.

```
/dev/sda5   none   swap   sw   0   0
```
And comment out the line after that.

```
#UUID=b6a0159a-2caa-42c4-b9a7-2487652b2ee3  none swap sw 0 0
```

---

### Post by idrinkwhisky on 2006-12-19
Taurus,

I did what you said and I think it worked!!!!
It's very strange cause I tried it myself earlier and it didn't work....oh well it works now i believe. :D

now when I type 

```
free
```

it gives:
```
idrinkwhisky@whisky-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:        515968     497968      18000          0      14352     257396
-/+ buffers/cache:     226220     289748
Swap:      1510068        192    1509876

```
this means that the swap is being used right?

One final question. Now that my swap is (probably) working, why can't I see the swap drive in my file browser?

anyways thanks alot for your help!!

---

### Post by taurus on 2006-12-19
Yip.  It is working alright and no, you can't see your swap partition in a file manager because you didn't mount it anywhere...  

Reboot again to make sure your swap is actually being mounted.  ;)

---

### Post by bodhi.zazen on 2006-12-19
Swap is working :p

---

