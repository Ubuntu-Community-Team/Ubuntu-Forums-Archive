---
title: "Installing Windows 7 from Disc after a Dual Boot with Windows XP"
date: 2013-07-13
forum: Any Other OS
---

### Post by shakaka on 2013-07-13
I currently have Ubuntu 13.04 dual booting with Windows XP. I want to uninstall the windows XP and replace it with Windows 7. What is the easiest way to do this?

---

### Post by oldfred on 2013-07-14
Moved to Other OS since really Windows.

Be sure to backup all data you may think is important. Windows should just install to the NTFS primary partition with the boot flag that your XP is in. 

       [http://www.sevenforums.com/](http://www.sevenforums.com/)
Install Windows 7
[http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html](http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html)
Repair install
[http://www.sevenforums.com/tutorials/3413-repair-install.html](http://www.sevenforums.com/tutorials/3413-repair-install.html)
[https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/](https://windowssecrets.com/top-story/win7s-no-reformat-nondestructive-reinstall/)
f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

---

### Post by mips on 2013-07-15
Backup your data, format the XP partition, install Win7 to the old XP partition.

---

### Post by Majorix on 2013-07-15
You will most likely have to restore GRUB since Windows will overwrite MBR.

---

### Post by mips on 2013-07-15
> **Majorix said:**
> You will most likely have to restore GRUB since Windows will overwrite MBR.

Oh this as well.

---

