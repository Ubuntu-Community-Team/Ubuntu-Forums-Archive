---
title: "Problem running display-dhammapada"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by jonathan.lees on 2007-06-03
Hi,

I am running feisty latest 2.6.20-16 and installed display-dhammapada via aptitude. It installs but when I execute it I get the following error:

/build/buildd/display-dhammapada-0.23/debian/display-dhammapada/usr/share/doc/display-dhammapada/dhammapada-english-transl.txt:
/build/buildd/display-dhammapada-0.23/debian/display-dhammapada/usr/share/display-dhammapada/dhammapada-english-transl.txt:
dhammapada-english-transl.txt
dp:     -- cannot open any of the files. 

The file dhammapada-english-trans.txt is there is in both the above directories.

thanks in advance for any help.

---

### Post by annda on 2007-06-03
check the [permissions]("https://help.ubuntu.com/community/FilePermissions") of the files to see if you are allowed to read them, or run the program with sudo

---

### Post by jonathan.lees on 2007-06-03
thanks, fixed by changing permission of the txt files.

---

