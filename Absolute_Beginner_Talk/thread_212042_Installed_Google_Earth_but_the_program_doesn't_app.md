---
title: "Installed Google Earth but the program doesn't appear on my Applications /Internet m"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-07-09
umm, I Installed Google Earth as per [these instructions]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Google_Earth")... but the program doesn't appear on my Applications /Internet menu (or anywhere in Applications..)!?

:confused:

---

### Post by _simon_ on 2006-07-09
Not to worry, just right click on your Applications menu and select "Edit Menus" then add a new item in the Internet group with the command to start googleearth

If you followed those instructions you linked to exactly then your path should be:

/usr/local/google-earth/googleearth %f

---

### Post by BlackMambo on 2006-07-09
Thx!That worked...however another problem..I started G Earth and it looks shit...!! There's no other way to describe it... it says it can't detect my graphics card and therefore its running in Emulation format...

Now my graphics card is an ATI Radeon 9800 Pro, about 3.5 years old. There does not appear to be a Linux driver for it [here]("http://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")...

Anyone know how I can fix this issue?

---

### Post by _simon_ on 2006-07-09
I think this will help you

[EasyUbuntu](http://easyubuntu.freecontrib.org/get.html)

There is an option to install the ATI drivers.

To get and run EasyUbuntu, from terminal enter the following:

```

wget http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz
tar -zxf easyubuntu-3.021.tar.gz
cd easyubuntu
sudo python easyubuntu.in

```

The ATI bit is on the SYSTEM tab.

---

### Post by BlackMambo on 2006-07-09
Thx - I actually already had that installed. The ATI bit is about adding 3D capability...anyway, it doesn't seem to have made any difference and G Earth needs something else evidently...damn!

---

### Post by user1397 on 2006-07-09
> **BlackMambo said:**
> Thx - I actually already had that installed. The ATI bit is about adding 3D capability...anyway, it doesn't seem to have made any difference and G Earth needs something else evidently...damn!is there actually an error message, or does it just look like shit?

---

### Post by BlackMambo on 2006-07-09
**You are currently running Google Earth in 'OpenGL' with software emulation. In this mode Google Earth will work but it will run very slowly. If you want to run Google Earth more quickly, then we suggest upgrading your graphics card driver**

thats the message.. :)

---

