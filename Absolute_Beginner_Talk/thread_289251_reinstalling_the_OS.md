---
title: "reinstalling the OS"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-10-30
I copied my Home directory to an external hard drive. I'm intending to replace it with the home directory from the reinstall. Would the program settings from those sub directories inside the home directory apply?

---

### Post by xXx 0wn3d xXx on 2006-10-30
> **Somenoob said:**
> I copied my Home directory to an external hard drive. I'm intending to replace it with the home directory from the reinstall. Would the program settings from those sub directories inside the home directory apply?

You will need to apply the settings to your fstab. It is the layout for static filesystems. Make sure it is connected and then try:
add this to your fstab. You may need to edit this line.

/dev/hda# /home ext3 defaults 0 1
                  
Put filesystem type in where ext3 is. (xfs, jfs, ext3, etc)
Put your drive number in /dev/hda# (/dev/hda4, /dev/sda3)

the reboot. Everything should work then and if not move your /home elsewhere for the time being. And then mount it.

---

