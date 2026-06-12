---
title: "Fins and delete all m4a files in a folder"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-09-21
Hi, I have my music collection in one folder called '/home/rudolf/music' and I have some m4a files in there that I would like to delete. Can I some how via the terminal ask it to find all the files with an extension of .m4a and then ask it to delete them?

Thanks

---

### Post by yabbadabbadont on 2007-09-21
```
rm /home/rudolf/music/*.m4a
```
;)

Edit: Be VERY careful that you do NOT have a space between the '*' and the '.m4a', otherwise ALL your music will be gone.

---

### Post by kasperbs on 2007-09-21
thanks

---

### Post by kasperbs on 2007-09-22
Can I somehow make it search recursive. At the moment it doesn't find anything because all the files are in subfolders

---

### Post by yabbadabbadont on 2007-09-22
```
find /home/rudolf/music/ -type f -name "*.m4a" -exec rm {} \;
```
Ask and ye shall receive.  ;)

---

