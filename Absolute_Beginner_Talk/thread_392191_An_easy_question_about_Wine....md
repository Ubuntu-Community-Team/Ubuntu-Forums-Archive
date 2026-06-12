---
title: "An easy question about Wine..."
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2007-03-24
I just installed a piece of software, which I think was installed into the fake C: drive on the computer.  Now...where is this fake drive actually located?  I need to open up the Program Files folder to find this software installed and execute it using wine in the terminal.

Thanks

---

### Post by eljalill on 2007-03-24
it is on ~ .wine/drive_c 
you could also use locate in a terminal to find your .exe file, in case you have one that is not in drive_c

---

### Post by halitech on 2007-03-24
the WINE folder is actually hidden so you would need to show hidden folders. it's /Home/user/.wine/drive_c/Program Files/rest of location

the folders are case sensative so make sure you type it exactly as listed

---

### Post by Patrick K on 2007-03-24
Type winefile in the terminal to open wine's file browser. Click on the C drive icon then the program files folder. You'll find the app installed there.

---

### Post by diablo75 on 2007-03-24
Great help, thanks.

---

