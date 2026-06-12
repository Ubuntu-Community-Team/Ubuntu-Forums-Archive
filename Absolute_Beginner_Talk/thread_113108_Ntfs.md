---
title: "Ntfs?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2006-01-05
[http://www.ntfs-linux.com/](http://www.ntfs-linux.com/) 

I just found this.  Anyone have experience?

---

### Post by jbmalone on 2006-01-05
Has no one used or heard anything about this?

---

### Post by TeeAhr1 on 2006-01-05
I have not heard of that specific product, but I was vaguely aware that such a thing existed.  Why do you ask?

(Also, I read that the new kernel version has NTFS support...)

---

### Post by najames on 2006-01-05
I'm not familiar with the product, nor what your intentions of using it are.  

If you want to use Windows and Linux on the computer you can create a dual boot setup.  Linux can read NTFS.  If you want to share you could also set up a Fat32 (?)  partition for both to write to.  Been a while since I have done this.

I have several PCs here, some with WinXP, most with Linux.  I have Samba installed on them by default with Suse 10, can't remember how Ubuntu is set up.  Suse's KDE setup uses Konqueror and I can click on the network and select the WinXP computer and access any shared drive with read/write.   Recently, I wrote our Xmas letter on Linux and my wife wanted the doc on XP so she could use some greeting card stationary.  I just used drag and drop to copy it to the shared XP drive with Konqueror and she could edit it.  

Another thought is some sort of virtual machine setup, although I am currently ignorant on this topic reading very soon VMWare, or something similar.  A guy at work was claiming VMWare is the greatest thing since sliced bread.

Too much to do, so little time, painting house, home repair work, building PCs, trying to learn new tricks after programming all day.  ** sigh **

---

### Post by jbmalone on 2006-01-06
I was mainly considering it for NTFS write supports.  I haven't tried in a while, so I don't know if the kernal I just updated has it or not.

---

### Post by Jammy_Stuff on 2006-01-06
I would recommend having a FAT32 partition for shared documents. Alternatively, set up Windows in VMware ([http://www.ubuntuforums.org/showpost.php?p=472105&postcount=32](http://www.ubuntuforums.org/showpost.php?p=472105&postcount=32)) and when you open the VM in VMware Player, right click ethernet and click host only networking, then you should be able to use Samba to swap files from you hard disk to the virtual one.

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=jbmalone][http://www.ntfs-linux.com/](http://www.ntfs-linux.com/) 

I just found this.  Anyone have experience?[/QUOTE]

At this time there is no complete solution in Linux that gives you write support on a NTFS drive that is worth risking your data for...this new kernel is a start towards fixing that.

Its better to convert your Windows drive to FAT. Its not THAT bad...

---

### Post by jbmalone on 2006-01-06
I just don't have a back up of this data because it is about 50GB worth, and I wanted a solution to help me.

---

