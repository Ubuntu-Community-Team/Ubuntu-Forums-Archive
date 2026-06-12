---
title: "Removing GRUB"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by shador on 2006-03-25
How do I remove GRUB? I'm removing my whole Ubuntu system for now, Iäll pick it up again with dapper.

---

### Post by dermotti on 2006-03-25
Do you have another OS on that harddrive currently?

---

### Post by akiro.yamamoto on 2006-03-25
If you have a WinXP install CD, boot from it. Select Recovery console (R - I think) and type 
```

fixmbr

```
If you don't have an install CD download a win boot floppy / CD from
[** HERE !!!**](http://www.bootdisk.com/bootdisk.htm)
Boot from the floppy and then :
```

fdisk /mbr

```
Either one should remove grub from your system.
Hope this helps ;)

---

