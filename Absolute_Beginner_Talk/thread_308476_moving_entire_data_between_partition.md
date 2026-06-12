---
title: "moving entire data between partition"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-28
How to move the entire data from partition /dev/sdb5 (NTFS) into /dev/sdb6 (ext3)?

---

### Post by Bachstelze on 2006-11-28
You cannot. Moving implies deleting and it is still unsafe to do so on NTFS.

You could still do it from Windows usint an ext2/3 driver though but if you want to move the whole stuff on it, why not just copy it and then delete the partition ?

---

### Post by oliviacond on 2006-11-28
I tried to copy it(haven't press 'Apply), but the Gparted will automatically change the ext3 into NTFS. I want to select 'Format to ext3' but I afraid it will erase the file after the 'Copy' process.

---

### Post by Bachstelze on 2006-11-28
Of course it will. First, you need to copy the data from your NTFS somewhere else so you can format it to whatever FS you want.

---

### Post by oliviacond on 2006-11-28
I'm confuse. If I move NTFS's data to other FS, the new FS will be a new NTFS and then I change the old NTFS into new ext3 and then how am I able to move the new NTFS file back to the newly formatted new ext3(before it was old NTFS), if I copy it the newly formatted new ext3 will become NTFS also. It's still pose the same problem.So, how to move NTFS's data into ext3 and kill the NTFS?(step by step)

---

### Post by oliviacond on 2006-11-28
Ok, I found the solution. Move the NTFS's data into /home temporaly and then format the NTFS into ext3 and move the data back. I'm so silly.

---

### Post by timcredible on 2006-11-28
in general, grsync is great for moving lots of stuff like that - make sure to run it as root and check to keep permissions, or you can run into odd things with file permission problems.

---

