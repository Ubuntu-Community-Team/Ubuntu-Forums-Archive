---
title: "Files are locked"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Jordan Meeter on 2006-10-05
I just copied some files and folders off a CD onto my computer (/home/jordan/photos) to be exact. For some reason, all of the files have a lock symbol in the upper right-hand corner of them. How can I unlock the files?

Thanks,
Jordan

---

### Post by henriquemaia on 2006-10-05
Just select all the files. Right click on them and choose properties. Go to **Permissions**. Check the **Write** box for **Owner**.

---

### Post by wieman01 on 2006-10-05
Do this from command line:
> sudo chown jordan /home/jordan/photos/*
> sudo chgrp jordan /home/jordan/photos/*
Enter your user password when prompted.

---

### Post by Jordan Meeter on 2006-10-05
Both of them?

I did both and the files are still locked...

---

### Post by wieman01 on 2006-10-05
Just copy and paste the whole command... 
> sudo chown jordan /home/jordan/photos/*
Yours is incomplete. Once you have done this, simply follow Henriquemaia's advice.

---

