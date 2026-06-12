---
title: "How do I create a Shared Folder on a dual boot system?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by curiousnoob on 2008-01-13
Is it possible to create a shared folder on a dual boot system (Gutsy and XP) without having to create a new partition?  
Basically I want a folder on both my Windows and Ubuntu desktop that share the same contents and  I can pass files back and forth easily.

---

### Post by teamkiller87 on 2008-01-13
Format the Windows partition using NTFS so Linux could write on it and all the folders become so-called "shared".

---

### Post by edm1 on 2008-01-13
> **teamkiller87 said:**
> Format the Windows partition using NTFS so Linux could write on it and all the folders become so-called "shared".

I dont think formatting the drive would be wise.

I suppose you could make a folder on your windows desktop then install the ntfs drivers in ubuntu to allow you to read/write in the folder. Then edit /etc/fstab so that the folder is automatically mounted at startup.

To install the ntfs driver (it might already be installed but this wont hurt)

```
sudo apt-get install ntfs-3g
```

**Or** you could do it the other way round and make the folder in ubuntu then install the [ext3 driver]("http://www.fs-driver.org/") in windows.

---

### Post by Dodelijk on 2008-01-13
You can actually gain access to your partitions with the aid of the following: 

To 'see' windows partitions from Ubuntu read section 2 of this : [http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html](http://linuxondesktop.blogspot.com/2007/02/13-things-to-do-immediately-after.html)

To 'see' Lunix partitions from Xp then use this: Yep emd1 that's the one. 

curiousnoob please see above...

---

### Post by Fleece Flamingo on 2008-01-13
Create a separate Fat32 partition aside from a smaller home partition and use it to as a shared folder.

---

### Post by curiousnoob on 2008-01-13
It seems that I already have everything I need to access the Windows partition.  
I created a folder on the Windows Desktop and then in Ubuntu I created a link to that on the Ubuntu Desktop.  
I moved a file in Ubuntu into the new folder and switched to Windows.  There file was in the folder on the Desktop but there was also a second system file with the same name.  
When I went back to Ubuntu the link no longer worked.

---

