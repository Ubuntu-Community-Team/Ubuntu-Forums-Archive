---
title: "how to copy from desktop to other places [Resolved]"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by drpas2k on 2007-05-10
How to copy/cut saved video from  desktop to other places including windows partion. I have NTFS partions. When I tried I am not getting Paste on right click

Duel boot.Single hard drive .thanks

---

### Post by Ek0nomik on 2007-05-10
You don't currently have write support for your NTFS drive.  NTFS drives come with Read support, but not Write by default in Linux.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

These should get you well on the way.  I just got my NTFS drive working with Read/Write support a few days ago.  Took me about 5 minutes, it's quite easy!

After you enable Write support though, be sure to reboot your computer so the changes can take effect.

Cheers.  :)

---

### Post by mikewhatever on 2007-05-10
By default, Ubuntu does not have ntfs write support, so you can't copy to ntfs. If using Feisty, the driver for (ntfs-3g) is in the repositories and can be installed.

---

### Post by Najand on 2007-05-10
Well, people use ntfs3g these days, but it is not usually adviced, because the Micro$oft has never released any information about NTFS and it is not fully supported by ntfse3g and might cause trouble with your Windows partition, sometimes... Better to use FAT32 that both windows and linux and can read and write.

---

### Post by Ek0nomik on 2007-05-10
I thought NTFS-3G is considered Stable these days?

That's what I read at least...

If he is downloading DVD's, he will want NTFS so he can have the 4GB+ files.  If you don't need 4GB+ files, I suppose you could switch to FAT32, but if it isn't an option, NTFS-3G should work fine.

---

### Post by drpas2k on 2007-05-11
Thanks a lot Ek0nomik.   It is so easy.Now I am able to copy and paste

---

