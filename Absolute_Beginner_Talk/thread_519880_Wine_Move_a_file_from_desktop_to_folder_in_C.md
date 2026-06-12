---
title: "Wine: Move a file from desktop to folder in C:\"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-08-07
Hi

I got a file on my desktop:

Z:\home\wikzo\Desktop\ordbog\EngelskMedium.adb 

How do I move it to my fake C drive made by Wine?

I want to move the file to this folder:
c:\Program Files\Gads Bogskab

---

### Post by Hospadar on 2007-08-07
wine creates it's c drive in a folder in your home directory, so anything that you want to put in the wine c drive you'll have to put there.  for example:
```
 cp /home/wikzo/Desktop/ordbog/EngelskMedium.adb "/home/wikzo/.wine/drive_c/Program Files/Gads Bogskab"
```
you can also navigate to the wine directory manually by going to your home folder in you file browser (nautilis or konkerer) and going to view->show hidden folders and then going to the ".wine" directory, and then to the "drive_c" directory

---

### Post by Wikzo on 2007-08-07
Thank you very much :)

---

### Post by Wikzo on 2007-08-07
New question:

I got a little Windows program. Works fine in Ubuntu with Wine, but now I want to delete the program. It contains no uninstaller. Can I just delete the file folder in .Wine?

---

