---
title: "Lost and Found folder"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-03-19
Another dumb question - what's the Lost and Found folder for?

---

### Post by jbayone on 2007-03-19
" this is a directory where Linux keeps the files that it restores after a system crash or when a partition hasn't been unmounted before a system shutdown. Thus, it can recover files that otherwise would have been lost."  From this guide to Linux directories - [http://www.goitexpert.com/entry.cfm?entry=A-guide-to-Linux-directory-structure--Part-One]("http://www.goitexpert.com/entry.cfm?entry=A-guide-to-Linux-directory-structure--Part-One")

---

### Post by experttease on 2008-07-19
I just formatted a partition to etx3 and I get this lost+found folder I can't delete. I believe the file was a failed Partition Image err, image. Any idea of how I can delete it? I've reformatted the partition twice but it's still there.

---

### Post by aaronb on 2008-07-19
A lost+found folder on a ext3 is not bad news. You do not need to delete this folder is it will only contain files in it if fsck fails for some reason.

---

