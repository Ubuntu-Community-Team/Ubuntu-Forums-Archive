---
title: "Mac mini will not boot into Ubuntu or boot from linux cd"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by bluepumpkin00100001 on 2009-04-26
Hello,

I have recently installed Ubuntu 9.04 on an intel mac mini (1.83GHz core duo). I had 8.10 for a long time before and it worked perfectly, but when I tried to update, it failed.

Anyway, I did a fresh install of 9.04 and after a bit of tweaking I got everything working properly.
Last night I restarted the computer and booted back into OSX before I went to bed. This morning I tried booting back into Ubuntu and it wouldn't :(
Also, somehow the firmware became password protected, and I never set it.
I've spent the last few hours searching the internet and trying everything I can find to get it to work again... I removed the password protection, reinstalled refit, reset the pram, and reset the firmware and it still won't work. It will boot into OSX and the 10.5 install DVD just fine, but whenever I try to boot any Linux cd or boot Ubuntu off the hard drive it never gets past the grey screen, and the computer gets ridiculously hot really quickly (like after 20 seconds it's almost painful to put my hand next to the fan). This happens when I try to use refit, when I hold down C, and when I use the boot camp menu.

any other ideas?

---

### Post by bluepumpkin00100001 on 2009-04-26
oh, and also when I reboot now it takes significantly longer than it used to. Before it would restart almost immediately after the screen went black, but now after the screen goes black it just sits there for 10-15 seconds before I hear the startup chime again

---

### Post by cyberdork33 on 2009-04-27
can you post the output of /Applications/Utilities/Partition Inspector

---

### Post by bluepumpkin00100001 on 2009-04-28
Sure:

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    271048407  Mac OS X HFS+
 3      271048408    310761298  Basic Data
 4      310761299    312581774  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    271048407  af  Mac OS X HFS+
 3      271048408    310761298  83  Linux
 4      310761299    312581774  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 271048408:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux

Partition at LBA 310761299:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

```

---

### Post by cyberdork33 on 2009-04-28
I think you need to mark the Ubuntu partition as active with fdisk (alter it in the MBR table). If that doesn't help, put it back on the OSX partition.

---

### Post by bluepumpkin00100001 on 2009-04-28
k, thanks a bunch :D
I'll try it tomorrow... (don't have time to mess with the computer tonight :P)

---

### Post by bluepumpkin00100001 on 2009-04-29
It worked :D
Thank you very much

---

