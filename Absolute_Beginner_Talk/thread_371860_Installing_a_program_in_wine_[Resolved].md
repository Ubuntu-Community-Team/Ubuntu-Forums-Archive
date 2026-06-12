---
title: "Installing a program in wine [Resolved]"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-02-27
I am using Xubuntu and have wine installed. I put in a windows app in the cdrom1 and open the mounted drive and double click the "setup.exe" icon. It tells me I do not have the rights to run the exe. I then at a terminal I type in 
```
gksudo thunar
```

I get the warning that I an running it as root. Then I try it again and get the same message. I even tried to change the permissions on folder and was denied.

Help please, it is a app the I need for work.

Hamm

---

### Post by taurus on 2007-02-27
```
wine /media/cdrom0/setup.exe
```

---

### Post by Hamm on 2007-02-27
Thank you very much......sorry for being such a n00b  :lolflag: 

Hamm

---

