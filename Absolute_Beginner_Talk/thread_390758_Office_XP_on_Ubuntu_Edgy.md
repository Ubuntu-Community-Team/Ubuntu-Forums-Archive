---
title: "Office XP on Ubuntu Edgy"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by mistrymp on 2007-03-22
Hello, I own a compaq presario notebook, 2172US. I currently have edgy installed on it. I also have wine installed on it. And using that I managed to get MS Office XP working. I had to write scripts that open the individual .exe file for the various office products as otherwise i would need to type wine before everything. I have posted the contents of the script below, its pretty simple. My problem is when I  double click a .doc or .xls file it opens it with openoffice. Now I tries changing the file association so that when i double click on the documents it would try to run it using the respective MS office script files I wrote. Now the program does run when I double click on the file but it wont open the file. Is there anyway I can modify the script so that it will open any .xls or .doc files with the appropriate programs. Thank you.

#script to start Microsoft Excel

wine "/home/mihir/.wine/drive_c/Program Files/Microsoft Office/Office10/EXCEL.EXE"

---

### Post by bwingbob on 2007-03-22
Try something like this,

```
wine "/home/mihir/.wine/drive_c/Program Files/Microsoft Office/Office10/EXCEL.EXE" $1
```

You might try [CodeWeavers/]("http://www.codeweavers.com/") I bought their product CrossOver Plugin several years ago and it worked very well. I highly recommend.

---

### Post by mistrymp on 2007-03-27
Thanks I appreciate your help, that suggestion worked.

---

### Post by bwingbob on 2007-03-27
You're welcome.

Good Luck

---

