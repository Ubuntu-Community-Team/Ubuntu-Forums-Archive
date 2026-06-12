---
title: "How to copy a MP3 from linux to a windows folder"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by nikosl on 2007-06-16
Hi i have some mp3s in my desktop in linux and i want to copy and paste them to another hard disk where i have windows xp installed. I can copy them but when i go to the folder i want there is no "paste" option.
What can i do?

---

### Post by Bachstelze on 2007-06-16
You most probably don't have write access to your Windows drive. Is it FAT or NTFS ?

---

### Post by raul_ on 2007-06-16
You should use a tool called ntfs3g

[http://http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html]("http://http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

---

### Post by bigken on 2007-06-16
download and install[ this ]("http://www.fs-driver.org/")

then you can read your linux partition in windows

---

### Post by raul_ on 2007-06-16
> **bigken said:**
> download and install[ this ]("http://www.fs-driver.org/")

then you can read your linux partition in windows

I think he wanted the opposite of that :mrgreen: still, it's very handy if you want to access your Linux files in Windows

---

### Post by bigken on 2007-06-16
try this in a terminal 


sudo apt-get install ntfs-config

---

### Post by nikosl on 2007-06-16
Thank you guys!!!!!!!!!!!!!!
I was looking for bigken's solution!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Now everything is ok!!

---

