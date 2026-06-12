---
title: "refit problem"
date: 2011-11-01
forum: Apple Hardware Users
---

### Post by persiankid40 on 2011-11-01
Ok, so im on a Mac Book Pro (5,5) and I wanted to dual boot with Ubuntu 11.10. I followed these instructions [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) , and ran into an error on the part where I sync my partion tables. I havea Mac partion, a 1gb swap, and a 90 gig linux. rest is for mac. When i try and sync the tables, this is what i get
 
```
Startng gptsync.efi
 
Current GPT partition table
#        Start LBA                             End LBA                           Type
1         409640                                4741087                           Mac OS X HFS+
2         474105856                           476153855                       Linux Swap
3         476153856                           625141759                       Basic Data
 
 
Current MBR   partition table:
#A     Start LBA               End LBA          Type
1      1                          409639            Efi Protective
2      409640                 474103847       Mac OS X HFS+
3 *     474105856            476153855       Linux swap / Solaris
4      476153856            625141759       Linux
 
Status: Analysis inconclusive, will not touch this disk.
Error: No Found returned from gptsync.efi
 
* Hit Any Key to continue *

```
This is the internal hard drive report:
```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1         409640    474103847  Mac OS X HFS+
 2      474105856    476153855  Linux Swap
 3      476153856    625141759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    474103847  af  Mac OS X HFS+
 3      474105856    476153855  82  Linux swap / Solaris
 4 *    476153856    625141759  83  Linux

MBR contents:
 Boot Code: GRUB

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 1, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 474105856:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 2, type Linux Swap
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 476153856:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 4, type 83  Linux, active


```Any help? At first i thought that this would fix it, [http://ubuntuforums.org/showthread.php?t=1297229](http://ubuntuforums.org/showthread.php?t=1297229), but it didnt change anything.

---

### Post by persiankid40 on 2011-11-02
*Bump*
Can someone please help? I cant start my whole computer now..

---

