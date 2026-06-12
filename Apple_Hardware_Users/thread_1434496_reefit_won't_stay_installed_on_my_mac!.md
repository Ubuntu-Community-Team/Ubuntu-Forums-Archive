---
title: "reefit won't stay installed on my mac!"
date: 2010-03-20
forum: Apple Hardware Users
---

### Post by tyre_ on 2010-03-20
So I followed the [COLOR="red"]reefit[/COLOR] manual instructions to install.  I tried using the installer package and it seemed to work fine, only when I reboot there is no option which operating system I want to use, and when I go back into OSX [COLOR="red"] reefit[/COLOR] isn't there anymore.  I also tried the manual install putting it into the system folder on OSX and I get the same problem, it's gone again after I reboot.  

Not sure if it helps but this is what [COLOR="red"] reefit's[/COLOR] partion tool tells me:
(Im using the option button to boot into Linux right now, and when I do my Linux partition is called "Windows", I don't know if that matters either.)

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    360857639  Mac OS X HFS+
 3      360857640    360859593  GRUB2 BIOS Boot
 4      360859594    483101781  Basic Data
 5      483101782    488397134  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640    360857639  af  Mac OS X HFS+
 3      360857640    360859593  ef  EFI System (FAT)
 4      360859594    483101781  83  Linux

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

Partition at LBA 360857640:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type GRUB2 BIOS Boot
 Listed in MBR as partition 3, type ef  EFI System (FAT)

Partition at LBA 360859594:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux

Partition at LBA 483101782:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 5, type Linux Swap

---

### Post by linuxopjemac on 2010-03-20
[http://refit.sourceforge.net/help/install_reboot.html](http://refit.sourceforge.net/help/install_reboot.html)

---

### Post by tyre_ on 2010-03-20
Ok, apparently it does work.  I discovered that if I just push the "option" button and release it.. rather than holding it down, the reefit menu comes up.  Strange.  Thanks for your help tho!

---

