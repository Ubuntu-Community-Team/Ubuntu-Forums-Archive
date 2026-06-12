---
title: "folding proteins"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by surferben182 on 2005-11-08
i am trying to install the folding proteins client (FAH504) onto my system and im confused about how to do it.  on the FAH website, it says "To launch: To use this program, make sure that you can execute it (chmod +x FAH5-Linux.exe) and then run it ./FAH5-Linux.exe" and i dont understand what do do with that.  the install file (.exe) is located on my desktop

thanks a bunch for the help

---

### Post by jasay on 2005-11-08
I've never tried that program, but it sounds like you do exactly what it said.  Open a terminal, change to the desktop directory```
cd Desktop
``` and change the permissions of the file so that you can execute it ```
chmod +x FAH5-Linux.exe
``` Finally, run the program by typing```
./FAH5-Linux.exe
```  If that doesn't work and complains about permissions you might try running as root ```
sudo sh ./FAH5-Linux.exe
```

---

