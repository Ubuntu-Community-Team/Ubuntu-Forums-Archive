---
title: "Drive Icon on Desktop"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by funnyguyfunnyguy on 2006-06-14
I used to have an NTFS partition (Documents and Settings) auto-mount when I logged in to gnome. I have since formatted that drive as XFS and changed its default mounting point; however, the drive icon is still present on my desktop every time I log in to gnome. How do I go about removing the drive icon from my desktop?

---

### Post by TristanMike on 2006-06-14
The Configuration Editor should be able to remove it. Start it by selecting Applications-->System Tools-->Configuration Editor, but if you don't have that, you can either add it via the Alacarte Menu Editor (Applications-->Accessories-->Alacarte Menu Editor) or by typing ```
gconf-editor
```in a terminal. In gconf go to "apps-->nautilus-->desktop" and scroll all the way to the bottom where it says "volumes_visible" and uncheck it.

---

### Post by funnyguyfunnyguy on 2006-06-14
Thanks for that help. It actually looks like I formatted my old drive, which was labeled under Windows XP "Documents and Settings." However, formatting the drive did not erase the drive label. How do I rename the drive?

---

### Post by harishg on 2006-06-15
I think you edited the config file for making the drive load at startup.I would suggest you to open the /etc/fstab file and removing the line you added to automount the ntfs partition.

[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)

---

