---
title: "partition that both winxp and ubuntu can access"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by cbradley on 2008-01-01
hi
 I successfully installed Gutsy on my P5GC-MX computer alongside my winxp.
My question is, having some spare disc capacity could I create   a partition that winxp can write to and ubuntu can read. Could be used for backing up data. I've tried making a vfat                                                         
one but neither os could see it

---

### Post by donatell0 on 2008-01-01
That is odd.  A fat32 partition should be viewable to either OS. Atleast Ubuntu should be able to see it. Use the gparted tool to view all partitions on your computer. You can also paste the output of the command "df -h" here, so that it'll be helpful for someone trying to help you with your problem.

---

### Post by twin_57103 on 2008-01-01
I'm not sure why you can't see the FAT32 partition.  A useful Windows tool is Control Panel...Administrative tools...computer management...disk management.  From there, I can see my ext3 partition (as unknown file system), even though it doesn't appear elsewhere in Windows.  It might help diagnose the problem.  You can also format hard disks from here.

I use an NTFS data partition and have never had any trouble with it.  NTFS-3g is (generally) easy to set up and quite stable.  If you can't get FAT32 to work, you might try formatting to NTFS, at least to see what happens - again, it might help diagnose the problem.

---

### Post by thelatinist on 2008-01-02
Fat32 should be fully accessible by either OS by default.  An NTFS partition can be read by default Gutsy and read and written if you install and mount using ntfs-3g.  You can get read/write access to an ext3 partition in Windows if you install [Ext2 IFS for Windows]("http://www.fs-driver.org/index.html").  Please note that Linux will not honor Windows access rights, and Windows will not honor Linux access rights.  Anyone with access to the shared disk will be able to modify any file on it.

---

### Post by twin_57103 on 2008-01-02
> **thelatinist said:**
>  You can get read/write access to an ext3 partition in Windows if you install [Ext2 IFS for Windows]("http://www.fs-driver.org/index.html"). 

Cool...I'll have to try that.

---

### Post by donatell0 on 2008-01-02
> Please note that Linux will not honor Windows access rights, and Windows will not honor Linux access rights. Anyone with access to the shared disk will be able to modify any file on it.

twin_57103: I think you should be careful about the above! :)

---

### Post by cbradley on 2008-01-03
hi
thanks I've learned a lot,now  I'm going to delete my swap & fat32 partition and resize my ubuntu patittion using my live CD and create them again. Only thing I'm worried about making my ubuntu parttion bigger the extra space I give it - will it need to formattted?

---

