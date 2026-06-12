---
title: "how to do a clean install?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-25
I have two HD's , # 1 All Windows XP , # 2 Partioned  with XP & Ubuntu so i'm dual booting right now.
If I want to do a clean install of Ubuntu without messing up any Windows Partitions how do I erase just the Ubuntu partitions & grub?

---

### Post by the_darkside_986 on 2007-08-25
I'm not sure I understand fully, but I recommend downloading and using the GParted liveCD. It allows one to safely delete the Ubuntu partition. Just be sure not to try to resize any Windows partitions or that will most likely ruin them. After deleting the Ubuntu partition with GParted, you can simply run the Ubuntu liveCD once again and there should be free space on the drive that Ubuntu will want to use. It should also reinstall grub and recognize the presence of Windows.

---

### Post by oilchangeguy on 2007-08-25
or, just unplug the drive with windows. install ubuntu. the plug in the windows drive. grub should see the drive, and give you the option to use either os.

---

### Post by jay4e on 2007-08-25
you will want to use manual partitioning and set the root partition to the root ubuntu partition and do the same for /home, swap, /boot, ect if they are separate partitions.  during the install grub should take care of it self and not effect your windows dual booting.  using manual partitioning only the partitions you tell it to will be formated though you have to formate the root ubuntu partition so if you have /home in the same partition you will want to back that up.

---

