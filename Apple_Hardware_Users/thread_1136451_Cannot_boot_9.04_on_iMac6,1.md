---
title: "Cannot boot 9.04 on iMac6,1"
date: 2009-04-25
forum: Apple Hardware Users
---

### Post by realplayer on 2009-04-25
I have an iMac6,1
After installation, I can see GRUB loading, entering stage1.5.
Then I am at command line for GRUB. Then I do not know how to boot after that.

My partition set up is the following:

parti


```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640   1875001383  Mac OS X HFS+
 3     1875263528   1936222535  Basic Data
 4     1936222536   1951523317  Basic Data
 5     1951523318   1953523318  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640   1875001383  af  Mac OS X HFS+
 3     1875263528   1936222535  0c  FAT32 (LBA)
 4 *   1936222536   1951523317  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 1875263528:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA)

Partition at LBA 1936222536:
 Boot Code: GRUB
 File System: ReiserFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 1951523318:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap
```

I tried to install directly, or after boot into live CD and then install. I installed GRUB on (hd0,3). 
After installation, I tried to install GRUB again when booted into GRUB, but still won't boot. I did update partition map in rEFIt.

Thank you for your advice in advance.

---

### Post by pxwpxw on 2009-04-25
> **realplayer said:**
> I have an iMac6,1
After installation, I can see GRUB loading, entering stage1.5.
Then I am at command line for GRUB. Then I do not know how to boot after that.

My partition set up is the following:

parti


```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640   1875001383  Mac OS X HFS+
 3     1875263528   1936222535  Basic Data
 4     1936222536   1951523317  Basic Data
 5     1951523318   1953523318  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640   1875001383  af  Mac OS X HFS+
 3     1875263528   1936222535  0c  FAT32 (LBA)
 4 *   1936222536   1951523317  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 1875263528:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0c  FAT32 (LBA)

Partition at LBA 1936222536:
 Boot Code: GRUB
 File System: ReiserFS
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active

Partition at LBA 1951523318:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap
```

I tried to install directly, or after boot into live CD and then install. I installed GRUB on (hd0,3). 
After installation, I tried to install GRUB again when booted into GRUB, but still won't boot. I did update partition map in rEFIt.

Thank you for your advice in advance.

You can boot it from the grub> command line
```

grub> find /vmlinuz
#### that will show what to use in the next line
grub> root (hd0,3)
grub> kernel /vmlinuz root=/dev/sda4
grub> initrd /initrd.img
grub> boot

```
If that gets booted into ubuntu with no problem, then from ubuntu command line you can reinstall grub
```

$ sudo grub-install /dev/sda4
$ sudo update-grub

```
That assumes ubuntu / is on sda4 and you also want grub boot code installed to sda4 as before.

---

### Post by realplayer on 2009-04-26
Thank you! It worked.

---

