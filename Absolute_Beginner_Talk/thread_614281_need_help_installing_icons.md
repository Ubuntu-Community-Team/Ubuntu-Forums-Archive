---
title: "need help installing icons"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by maxim1 on 2007-11-15
Need help trying to install icons they are zipped and have a b2z extension I have tried using 
theme manager but it want see it. I extract the archive and try and copy the folder to the icon folder but the command i use will not work any suggestions. command used below 

 sudo cp /home/colin/Downloads/Buuf /usr/share/icons

---

### Post by Paul820 on 2007-11-15
The icons folder is hidden. Open your home folder, press Ctrl+h to show hidden files, scroll down until you see the folder called **.icons** and put your extracted folder with the icons in, in there.

---

### Post by maxim1 on 2007-11-18
THanks

---

### Post by mdpalow on 2007-11-18
> **maxim1 said:**
> Need help trying to install icons they are zipped and have a b2z extension I have tried using 
theme manager but it want see it. I extract the archive and try and copy the folder to the icon folder but the command i use will not work any suggestions. command used below 

 sudo cp /home/colin/Downloads/Buuf /usr/share/icons

If the folder is hidden, then you probably didn't input the correct name since hidden folders have a '.' in front of them. You probably should have used:

sudo cp /home/colin/Downloads/Buuf /usr/share/.icons

---

