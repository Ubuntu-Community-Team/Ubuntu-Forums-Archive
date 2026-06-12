---
title: "How to use ntfs-3g to write to windows partition"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-12
I saw in another post that you can use ntfs-3g to write to a windows partition (is it already installed in feisty? because i can simply mount it by clicking on it in the file browser).  i'm not able to write to it, however, and so i tried doing sudo apt-get install ntfs-3g ntfs-config, but i'm still not able to write.  for instance, i want to be able to drag and drop files from my ubuntu partition onto my windows partition using the file browser - is that possible?

thanks for any help.

---

### Post by Kobalt on 2007-05-12
Try this : [https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by Michaelt74 on 2007-05-12
This may help, look at the 'Mount Windows...section

---

### Post by Michaelt74 on 2007-05-12
Sorry, [http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

### Post by Happy_Man on 2007-05-12
what you want to do is open up a terminal (System --> Accessories --> Terminal) and type:
```
ntfs-config
```

Then, check the box that corresponds to the type of drive you're trying to write to (eg internal or external) and click ok. Your drive should be mounted the next time you log in.

---

