---
title: "Grub won't load - and other questions"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by terrera on 2007-02-01
Hi,

I had to format my Windows XP partition and reinstall it. After I completed it the Grub won't work, hence the computer starts directly on Windows.

I using the live CD on the hope that it would find my /root, but it did not mount it and it is asking me to reinstall Ubuntu (Dapper 6.01).

Is there a way that I can make the computer load the grub again without reinstalling Ubuntu? Hope I have made myself clear....


A question that I would like to do is, my /home partition is formatted as Ext3 and therefore windows is not reading it. Is there a way that I can change from Ext3 to FAT32 without loosing my data in this partition?

Finally, is there a way that I can copy some files of mine from Linux to Windows (IE: Ext3 to NTFS)?

Thanks in advance!

Felipe

---

### Post by pseudonym on 2007-02-01
> **terrera said:**
> Hi,

I had to format my Windows XP partition and reinstall it. After I completed it the Grub won't work, hence the computer starts directly on Windows.

I using the live CD on the hope that it would find my /root, but it did not mount it and it is asking me to reinstall Ubuntu (Dapper 6.01).

Is there a way that I can make the computer load the grub again without reinstalling Ubuntu? Hope I have made myself clear....

Hi, [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") should help you.

> **terrera said:**
> A question that I would like to do is, my /home partition is formatted as Ext3 and therefore windows is not reading it. Is there a way that I can change from Ext3 to FAT32 without loosing my data in this partition?

In a word, no. You would need to back up first. Also, I think you have to use a linux filesystem for important directories like /home. FAT32 should only be used for storage or 'shared' partitions (shared between windows and linux).

> **terrera said:**
> Finally, is there a way that I can copy some files of mine from Linux to Windows (IE: Ext3 to NTFS)?

Definitely *not* recommended if you care about your data. best to set up a 'shared' FAT32 partition for this.

HTH

---

### Post by confused57 on 2007-02-01
Windows can read(& write to?) ext3 with the fs-driver:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by terrera on 2007-02-02
Thanks... I decided to reinstall the system

---

