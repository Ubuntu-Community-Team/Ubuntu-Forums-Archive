---
title: "grub loading error"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by mitchboy on 2005-10-19
Hi  Been a Windows user for years and want to use UBUNTU  I purchased a new hardrive for Ubuntu so deleted old partition so I could do a clean Ubuntu install on new drive now my puter wont boot up without Windows Boot Disk cos I get Grub loading stage 1.5 then Grub Loading Error 17 how do I get my boot back to normal Kind Regards

---

### Post by leaber on 2005-10-19
If you have win XP, boot from the cd rom and go to the repair console (or recovery console, i dont remember). Once there type *fixmbr* . This will overwrite the disk MBR so you can boot Windows without the CD.

additional info: 
[http://www.ubuntuforums.org/showthread.php?t=75965]("http://www.ubuntuforums.org/showthread.php?t=75965")

or just search the forums for "Grub error 17"

---

### Post by patrick295767 on 2005-10-19
[QUOTE=leaber]If you have win XP, boot from the cd rom and go to the repair console (or recovery console, i dont remember). Once there type *fixmbr* . This will overwrite the disk MBR so you can boot Windows without the CD.

additional info: 
[http://www.ubuntuforums.org/showthread.php?t=75965]("http://www.ubuntuforums.org/showthread.php?t=75965")

or just search the forums for "Grub error 17"[/QUOTE]


As said, CD bootable Repair console.
looks best way

---
in msdos, bootable floppy disk, u can clean up ur mbr from grub
with 
fdisk /mbr
but u'll need to use the CD bootable Repair console in ur case
(u'll have to type:
    
help
   
 then u'll see the light : it's a cmd ... that's i forgot)
---
Pat'

---

### Post by mitchboy on 2005-10-20
I will try your fixes I thank you very much for your quick response Regards

---

### Post by patrick295767 on 2005-10-20
[QUOTE=mitchboy] for your **quick** response Regards[/QUOTE]
  I really like this forum full of information and good advices from wise Linux users ! ;) :eek:

---

