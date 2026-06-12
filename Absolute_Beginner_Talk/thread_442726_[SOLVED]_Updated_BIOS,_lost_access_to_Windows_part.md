---
title: "[SOLVED] Updated BIOS, lost access to Windows partition"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Stebbins on 2007-05-13
I've been running a dual boot of Windows XP Pro and Ubuntu (Edgy) on my Dell Inspiron E1705 Laptop for about a month now.  Ubuntu has had read access to the files on the Windows partition... until today.

There are 3 NTFS partitions on my laptop: sda1-3.  I can still access sda1 and sda3, but when I try to open sda2 (the partition containing my Windows C:\ drive) I get an error message.  I think this may be because I just updated my BIOS from A00 to A01.  Does anyone know how I can fix this?

---

### Post by starcraft.man on 2007-05-13
> **Stebbins said:**
> I've been running a dual boot of Windows XP Pro and Ubuntu (Edgy) on my Dell Inspiron E1705 Laptop for about a month now.  Ubuntu has had read access to the files on the Windows partition... until today.

There are 3 NTFS partitions on my laptop: sda1-3.  I can still access sda1 and sda3, but when I try to open sda2 (the partition containing my Windows C:\ drive) I get an error message.  I think this may be because I just updated my BIOS from A00 to A01.  Does anyone know how I can fix this?

Well since its doubtful a bios update damaged partition, I guess all ya need to do is remount the NTFS partition. here you go, a nice guide for[ Edgy. ]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

If you want write access to the files, follow the guide lower down.

---

### Post by msandersen on 2007-05-14
If Windows still works, make sure it has been shut down properly (not suspended or put to sleep). And it would help to post the error message.

---

