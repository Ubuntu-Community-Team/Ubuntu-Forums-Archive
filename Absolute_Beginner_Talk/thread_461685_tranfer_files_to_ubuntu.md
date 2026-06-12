---
title: "tranfer files to ubuntu?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by ldyjonesbug on 2007-06-01
When downloading ubuntu is it possible keep my previous documents and tranfer them to the new operating system, such as itunes and and other files that I may need for the future?  If so, how?

---

### Post by jaybuntu on 2007-06-02
That's certainly possible.  When I installed Ubuntu I resized the primary partition on my drive from 40 GB to 20 GB then I used the freed 20 GB to install Ubuntu.  You can specify this during the install.  Alternately, you could install Ubuntu onto a separate hard drive.  Either way, when you boot Ubuntu it should automatically mount any NTFS for FAT volumes that it finds then you can simply use the file manager to access your existing files.  I also understand the 7.04 has a wizard for importing some files but I originally installed 6.10 then upgraded so I personally don't have any experience with that.

---

### Post by wataboutbob on 2007-06-02
Yes it is possible.

Just make sure that when you install Ubuntu, you choose to make partition either manually or ask it to use the largest remaining free block. Best way forward though would be to choose to make partition manually and give Ubuntu a 7 or 8 GB partition at the end of your HDD. 

Once installed, Ubuntu will automatically mount any NTFS or FAT32 partition that you may have and you can read/write (for NTFS drives, you will have to install ntfs-3g to enable to write) to them.

---

