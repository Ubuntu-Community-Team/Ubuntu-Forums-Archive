---
title: "updates download/install problem"
date: 2009-03-12
forum: Apple Hardware Users
---

### Post by Lexwebb on 2009-03-12
I can't install any updates and even repair 5! broken files. it said something about no free space (or something similar), so i whacked in the install disk and booted up from it. i opened up the partition editor from the disk. These are my partitions:

********
```
             Type               size                    used            free space
/dev/sda 1 Unknown           31.50kb                    -                   -
unalocated unalocated        124.48MB                   -                   -
/dev/sda 3 hfs+             136.72GIB                  93.09GIB         43.63GIB            ((this is my mac partition))
/dev/sda 2 ext 3             11.14GIB                 258.47MB            10.19GIB
unalocated unalocated        2.48 GIB                   -                     -
/dev/sda 4 hfs                997KIB                172.5KIB               80.45KIB(boot)
/dev/sda 5 ext 3             2.05 GiB                2.05GIB                 0B
.dev/sda 6 Linux swap        160.41MB                   -                    -        (swap)
```

********
Now, i'm guessing that the 2.05 GIb partition (/dev/sda 5 ext 3), is the ubunto system, as you can see it has no free space in it, i think this i right, but if i wrong please correct me. 

Oh, and i have already tryed to grow the size of that partition ^ but i am not able to.

Also any tips i could try would be appreciated. ;)

---

### Post by Lexwebb on 2009-03-12
the REAl post

---

### Post by Kevbert on 2009-03-12
Boot into Ubuntu.
First thing to try is to get rid of any redundant files in terminal with
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
Next, are there any linux kernels that you aren't using ? These will show up in grub. It's best to keep the latest and previous kernels which you can see with
```
cd /boot
ls -l
```
Here's my one output for Hardy:
```
total 31080
-rw-r--r-- 1 root root  420395 2008-11-24 22:19 abi-2.6.24-22-generic
-rw-r--r-- 1 root root  420395 2009-01-26 03:57 abi-2.6.24-23-generic
-rw-r--r-- 1 root root   74177 2008-11-24 22:19 config-2.6.24-22-generic
-rw-r--r-- 1 root root   74166 2009-01-26 03:57 config-2.6.24-23-generic
drwxr-xr-x 3 root root    4096 2009-02-22 19:45 grub
-rw-r--r-- 1 root root 8169231 2008-12-08 07:40 initrd.img-2.6.24-22-generic
-rw-r--r-- 1 root root 8169042 2009-02-11 12:50 initrd.img-2.6.24-23-generic
-rw-r--r-- 1 root root 8168969 2009-01-29 10:50 initrd.img-2.6.24-23-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 12:03 memtest86+.bin
-rw-r--r-- 1 root root 1153201 2008-11-24 22:19 System.map-2.6.24-22-generic
-rw-r--r-- 1 root root 1153457 2009-01-26 03:57 System.map-2.6.24-23-generic
-rw-r--r-- 1 root root 1905656 2008-11-24 22:19 vmlinuz-2.6.24-22-generic
-rw-r--r-- 1 root root 1907352 2009-01-26 03:57 vmlinuz-2.6.24-23-generic

```
In my case I want to keep 2.6.24-22 and 2.6.24-23 kernels, but I've got a .bak file which can be removed with
```
sudo rm *.bak

```
If I had unwanted kernels I would now go to Synaptic and remove the kernel by searching for linux-image and selecting the kernel file for complete removal - for example, linux-image-2.6.24-21-generic (if it was installed). This would remove the -21 kernel and the corresponding grub menu entry.

---

