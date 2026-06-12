---
title: "Replacing HD thats got grub on it"
date: 2006-04-30
forum: Absolute Beginner Talk
---

### Post by Digidiz on 2006-04-30
i want to replace a slow and inefficient hard drive, but the problem is that grub has been installed on that hard drive and not on the hard drive that has the ubuntu partition on it. how do i repair the grub menu (BOOTLOADER) when i eventually replace it or how can i put the grub menu on the hard drive that the ubuntu partition is on?

---

### Post by codejunkie on 2006-04-30
[quote=Digidiz]i want to replace a slow and inefficient hard drive, but the problem is that grub has been installed on that hard drive and not on the hard drive that has the ubuntu partition on it. how do i repair the grub menu (BOOTLOADER) when i eventually replace it or how can i put the grub menu on the hard drive that the ubuntu partition is on?[/quote] 
Boot from the ubuntu install cd at the cd boot prompt enter
```
rescue
```and press enter from there follow the instructions until you reach the command line then enter
```
sudo grub
``` it will display something like this
```
    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>

``` enter 
```
grub> root (hd
```**now hit the TAB key and it will display something like this**

```
     GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd
 [COLOR=Blue]Possible disks are:  hd0 hd1[/COLOR]

grub> root (hd
```it lists the drives in order, so if ubuntu is installed on the second drive for this example you would use hd1, now enter the drive number in this case it would be 1
```
grub> root (hd1
```and ```
**hit the TAB key twice**
```this lists the partitions for the drive like this
 ```
GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd
 Possible disks are:  hd0 hd1

[COLOR=Black]grub> root (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x82
   [COLOR=Blue]**Partition num: 1,  Filesystem type is ext2fs, partition type 0x83**[/COLOR]
   Partition num: 2,  Filesystem type is fat, partition type 0xb
[/COLOR]
grub> root (hd1,
``` on this step find your ubuntu root partition, it will be the one with the [COLOR=Blue]0x83[/COLOR] partition type, so for the example you would enter 
```
grub> root (hd1,1)
``` and press enter, this points grub to the ubuntu partition, now you have to install grub to the first harddisk in this example, the first harddisk is hd0 so enter 
```
grub> setup (hd0)
```this install's grub to the first harddisk and will output something like this
```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd1,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```enter 
```
grub> quit
``` to exit grub. remove the cd and reboot and you should be all set, if you have any problem or questions let me know and i'll try my best to help.

---

