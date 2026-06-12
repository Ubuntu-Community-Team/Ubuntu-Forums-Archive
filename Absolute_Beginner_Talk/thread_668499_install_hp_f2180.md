---
title: "install hp f2180"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by rugby82 on 2008-01-15
hallo boy....i have try to install an hp f2180 deskjet on ubuntu dapper but system  do not have driver for this printer!!!!can you help me

---

### Post by bumanie on 2008-01-15
go to HP site, they support linux and have drivers. They also have a self extracting install package, that should take care of everything including, dependecies.

---

### Post by dstew on 2008-01-15
There is a Dapper Synaptic package, hplip (0.9.7-4ubuntu1), that should contain the driver you need.

---

### Post by rugby82 on 2008-01-15
do not found!!!!!!!!!!!!!!!!!!!!!

---

### Post by dstew on 2008-01-15
Open Synaptic, choose Search, and enter hplip.

---

### Post by bumanie on 2008-01-15
Go to this site [http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)
You should be able to install your printer from the tools there.
Not sure whether the present hplip installer will work with dapper, you may have to find an earlier version). Try the present one first., during the install process it should ask you to confirm which version of ubuntu you are using. Good luck

---

### Post by rugby82 on 2008-01-15
i have download this file and i have installed hplip but nothing.....when i try to add a printer  there isn't any file pdd of my hp f 2180!!!!!! therefore i can't install the printer!:confused:

---

### Post by dstew on 2008-01-15
If that exact model doesn't show up in the list of printers, you can try another HP inkjet series printer. If you see the generic HP Inkjet Series try that. If you see hpijs, that is another possibility.

---

### Post by rugby82 on 2008-01-15
thank you i try

---

### Post by bumanie on 2008-01-16
Download the hplip self-extracting archive to your desktop. In terminal type 
cd ~/Desktop  and hit enter
then in terminal type 
sh hplip-2.7.12.run
and the installer should start.

---

