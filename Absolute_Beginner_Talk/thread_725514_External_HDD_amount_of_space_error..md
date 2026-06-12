---
title: "External HDD amount of space error."
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by WarLud on 2008-03-15
I'm using an 100GB external HDD and for some reason Ubuntu keeps seeing less free space than there should be.

On Windows XP I have 30GB used, and 60GB free. However, in Ubuntu, it reads it as 80GB used, 10GB free!!! I don't really know why this happened. Any help would be good. 


EDIT: In addition, when I high-light all the files in Ubuntu and right click>properties, it says they're only 30GB total. And I also checked hidden files. There aren't any there.

---

### Post by HermanAB on 2008-03-15
Yup, I presume you are using the Ext3 file system.  It tends to do that.  One day it will miraculously fix itself again.  

One reason for these funnies is that when the system thinks that a file is in use, then when it is deleted, it will only be marked for deletion but won't really be deleted until the system thinks that the file is no longer in use.  However, I think that what you are seeing is evidence of a deeper bug in Ext3.

---

### Post by WarLud on 2008-03-15
Yes, I am using Ext3. Is there anyway of fixing this without waiting until "it will miraculously fix itself again. "???

---

