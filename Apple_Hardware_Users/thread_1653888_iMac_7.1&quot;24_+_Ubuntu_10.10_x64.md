---
title: "iMac 7.1&quot;24 + Ubuntu 10.10 x64"
date: 2010-12-27
forum: Apple Hardware Users
---

### Post by Yaroslav_L on 2010-12-27
I tryed to look here for some answeres, but can't find.
My mac: iMac 7.1"24 + Ubuntu 10.10 , C2D 2.4, ATI RadeonHD2600, standard kbd (big aluminium) and mouse.
I have 4 Volumes on my HD: System, 3DArchive, Data and Test.
1. With Disk Utill I format Test vol to fat 32 format.
2. I installed rEFIt 0.14 and see it after rebooting.
3. I want to install Ubuntu 10.10 x64 to Test vol. So I boot from CD and select "try Ubuntu without installation". After that I can't see nothing, but finally hear good known sound "booting complete" but steel see nothing - only black screen.
4. Then, I try to install LinuxMint 10 x64. This time everything was ok. "Test" volume I change to / - disk0s5, swap and /3DArchive - disk0s7. I also set grub to install to disk0s5.
5. After install finished, in rEFIt I make sync and try to boot linux. No chance - only frozen Pinguin, or black screen with blinking cursor...
Snow Leo boots fine, but I want to install Ubuntu 10.10 too.
Looks like LinuxMint's grub was installed with errors, and Ubuntu can't identify my iMac 7.1"24 monitor...
Please - heeelp!

P.S. And this is my Partition Inspector log:



*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    208790455  Mac OS X HFS+
 3      209052600    417433415  Mac OS X HFS+
 4      417695560    521025767  Mac OS X HFS+
 5      521287912    540819161  Basic Data
 6      540819456    548632575  Linux Swap
 7      548632576    625141759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    208790455  af  Mac OS X HFS+
 3      209052600    417433415  af  Mac OS X HFS+
 4      417695560    521025767  af  Mac OS X HFS+

MBR contents:
 Boot Code: None

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 209052600:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 3, type Mac OS X HFS+
 Listed in MBR as partition 3, type af  Mac OS X HFS+

Partition at LBA 417695560:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 4, type Mac OS X HFS+
 Listed in MBR as partition 4, type af  Mac OS X HFS+

Partition at LBA 521287912:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 5, type Basic Data

Partition at LBA 540819456:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 6, type Linux Swap

Partition at LBA 548632576:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 7, type Basic Data

---

### Post by srs5694 on 2010-12-27
Please boot the Ubuntu installer into "live CD" mode, run the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) and post the RESULTS.txt file that it produces. Please post the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

---

### Post by Yaroslav_L on 2010-12-29
SOLVED!
1. In most recommendation we can read: "change grub install path to linux volume. Dont use MBR!!!". BULL SH! In rEFIt 0.14 docs there are something like this: in dual-boot system (mac+linux) install grub/lilo into MBR!!!
2. Use correct alternative iso. For me it was "desktop-mac-x64"

And I have the next questions:
1. How to turn on "Num Lock"?
2. How to change Fn key to always on? For F1, F2, ... to works without pressing Fn key, but multimedia keys (volumes, ...) with Fn?
3. Quality of sound not so good. I have found that right speaker works fine, but the left one works with noises (under Mac OSX everything is OK).
Thanks.

---

