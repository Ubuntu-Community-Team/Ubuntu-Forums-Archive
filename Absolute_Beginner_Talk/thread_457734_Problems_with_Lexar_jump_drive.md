---
title: "Problems with Lexar jump drive"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-05-28
I just bought a Lexar 4GB Hi Speed USB JumpDrive and was told that it would be Linux Compatible. The problem is that I cannot write to it. I have tried many times to change the permissions but it says "Couldn't change the permissions of Lexar because it is on a read only disk." This jumpdrive works perfectly with Microsoft Windows but not Ubuntu unfortunately. I would greatly appreciate any help you can give about being able to write to it. If it is a lost cause and I will not be able to change the permissions, please tell me. Thank you.

---

### Post by Ek0nomik on 2007-05-29
Is it formatted as NTFS?

If so, you need to either reformat it to FAT32 (or something else I suppose if you prefer, but FAT32 would be good for a Windows and Linux combination, as both can read it natively), or you can install NTFS support in Linux.

If you want to install support on Linux, open a terminal:

```
sudo aptitude install ntfs-3g
```

Then you will see some options in your launcher to enable write support on NTFS drives.  You will probably need to reboot for the changes to take effect though.

Good luck.  :)

---

### Post by hoakz on 2007-05-29
Is NTFS write support under linux stable these days?

---

