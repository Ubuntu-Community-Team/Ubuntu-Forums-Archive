---
title: "Setting Permissions"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Dave B on 2007-05-22
i have installed UBUNTU on my machine that has 3 drives/partitions on it.

I cant set permissions on the 2 partitions to make them so that i can write to them.

is it something that i did in the install or might it be because they are NTFS partitions?

Any help in this would be appreciated

Dave B

---

### Post by taurus on 2007-05-22
If you want to write to ntfs filesystem, you need to install ntfs-3g instead of using ntfs since ntfs only gives you a read-only option.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by Sparkster185 on 2007-05-22
I run KDE, so I don't know about GNOME, but when I open Add/Remove Programs, there was one listed to manage NTFS partitions.  I would imagine you could install it, since I use the same repositories as you. It works like a charm.

---

