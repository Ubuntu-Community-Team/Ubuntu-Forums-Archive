---
title: "/home partition disk space did not increase after the content is deleted"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by qdvubun on 2006-07-14
I copy and past a game folder on my windows partition to /home/.. partition, and after selecting the folder and delete it, the disk space on my /home partition did not go back up, anyone know why??
thanks

---

### Post by cotcot on 2006-07-14
That is because what you deleted goes to a trash folder in your home directory. This trash folder is a hidden file. Click view --> show hidden files  and you will find a directory ".Trash". If you empty the Trash you will see your available space increase. Empty trash is right click on the most left down icon on your screen.

---

### Post by 5-HT on 2006-07-14
Did the directory get moved to ~/.Trash instead of being removed?
If not, is there any chance the directory may have been a symbolic link to the target on the Windows partition?

---

### Post by qdvubun on 2006-07-14
my mistake, I didn't empty the trash yet.
thanks

---

