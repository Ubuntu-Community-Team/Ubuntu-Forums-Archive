---
title: "fix grub"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-07-17
- I installed windows after ubuntu which removed my mbr
- i tried to fix with super grub disk and [urlhttp://ubuntuforums.org/showthread.php?t=224351=]this guide[/url]
- the grub menu is restored fine but when i try to load ubuntu, it says "error 17: cannot mount partition"
- I can access the drive fine in windowz and ubuntu live cd so the data itsnt corupted

---

### Post by mikewhatever on 2007-07-17
Use this guide [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
and this is for the next time [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by supersonicdarky on 2007-07-17
- the only difference is that I tried **setup (hd0)** instead of **setup (hda,1)**
- ubuntu is on the second partition, so shouldnt it be hd0,2 ?
- apparently I should have an output after **root (hd0,1)**, i didnt either way but it did say succeded after

---

### Post by mikewhatever on 2007-07-17
Did you run the find command? What was the output?
> grub> find /boot/grub/stage1

Read the guide again. In setup(hd0,x), you were supposed to use the number provided by the find command.

---

### Post by supersonicdarky on 2007-07-17
output was *(hd0,1)*, i tried using both *(hd0)* and *(hd0,1)* with **setup** (only used *(hd0,1)* with **root**)

---

