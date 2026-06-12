---
title: "Quick question about partitioning"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by drewhiggs on 2007-10-24
I am using the alternate cd and I am at the partition screen.  I choose manual partition and now I need some guidance.

Here are my partitions as I have them right now.  

#1 primary    92.0 GB      ntfs
#2 primary     7.1 GB    f  ext3         /
#6 logical      12.9 GB   f   ext3        /home
#5 logical    921.2 MB   f   swap       swap
#3 primary     7.1 GB    f   ntfs

#1 and #3 are for windows.  #2 and #5 were created automatically with the alternate cd.  My question is :  do I need #1 (windows vista install) to be /windows or leave it as is?

Thanks for your help.  Also if you need to know I have 1GB of memory

---

### Post by taurus on 2007-10-24
You want to mount #1 as /media/windows and perhaps #5 as /media/share.  Remember NOT to format them, #1 & #5, or all your data will be bye-bye.

---

### Post by rsambuca on 2007-10-24
You can basically mount it to whatever folder name you want.  If you mount it to /media/... then it will show up on your desktop by default in Ubuntu.

---

### Post by drewhiggs on 2007-10-24
Great.  Thanks for the quick replies.  I will post back with the results.

---

