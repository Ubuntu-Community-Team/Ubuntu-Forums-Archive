---
title: "hal.dll problem"
date: 2008-02-25
forum: Apple Intel Users
---

### Post by rocxet on 2008-02-25
I tried to install ubuntu 7.10 to my macbook pro. I already had windowsXP with bootcamp.

ubuntu installation was good, but after i reboot to XP. It appears hal.dll missing problem. So I searched on google and ubuntu forum. Then I tried to change the partition number to 3 in boot.ini. After I restarted, hal.dll message didn't appear again, but a short while after XP loggin window appears, there's a blue screen flash and it restarted automatically.


here's my GPT and MBR list:

 ```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    245776423  Mac OS X HFS+
 3      246038568    304769035  Basic Data
 4      304769036    310628411  Basic Data
 5      310628412    312581537  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    245776423  af  Mac OS X HFS+
 3 *    246038568    304769035  0b  FAT32 (CHS)
 4      304769036    310628411  83  Linux

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

Partition at LBA 246038568:
 Boot Code: Windows NTLDR
 File System: FAT32
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 0b  FAT32 (CHS), active

Partition at LBA 304769036:
 Boot Code: GRUB
 File System: ext3
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 310628412:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap



```

---

### Post by cyberdork33 on 2008-02-25
I think you are going to have to do a repair on your windows partition.

---

