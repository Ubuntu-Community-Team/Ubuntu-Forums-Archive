---
title: "how to write to my windows partition"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-05-26
It says i dont have permission, is there a way?

---

### Post by starcraft.man on 2007-05-26
> **mojo123 said:**
> It says i dont have permission, is there a way?

search for ntfs-3g drivers on the forums, there are guides to tell you how to configure. Its real easy. I must be brief I am falling asleep, gnight ><.

---

### Post by dave-5B on 2007-05-26
install ntfs-config (via synaptic or sudo aptitude install...)'

---

### Post by DerArzt on 2007-05-26
sudo chown -R $USER /media/<Folder_That_Windows_Drive_Is_Mounted_To>

*I assumed that you have ntfs 3g installed already, if not this won't work, but if ntfs-3g is installed and you dont have permission, it will.

---

### Post by aysiu on 2007-05-26
Follow this tutorial:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

