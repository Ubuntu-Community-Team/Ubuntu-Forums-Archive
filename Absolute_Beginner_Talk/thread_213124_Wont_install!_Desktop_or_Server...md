---
title: "Wont install! Desktop or Server..???"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by DAKz on 2006-07-10
OK Guys heres what I got and here's what happened, 1ghz Dell with 512Mb Ram 120gb HDD Nforce 5500 with 256mb video RAM, think thats the basics, Anyhow I downloaded 6.06 live CD, created a partition and went to install it after getting used to the Desktop, went through the 6 steps to setup, it started and locked up at 15%, OK bad download, downloaded again, burned to disk, went through it all again, same results, 2 bad downloads at the same place...naw. Downloaded the server version installed it, after some graphic adjustments, installed it it rebooted into a DOS mode, no Fun there, reformated the partition, ran live again went to install and stopped at 15%, OK may there's a really big file right there, so I went to bed, next morning still 15%. Any ideas?

---

### Post by Maggot on 2006-07-10
Not sure with the Desktop install but when you boot from the CD (or start the install) is there an option to disable ACPI?

---

### Post by nalmeth on 2006-07-10
If you can find any boot options, I believe the option should be 

linux=noacpi

If there is a boot options page, look there too for disabling acpi

---

### Post by catlett on 2006-07-10
You can get a full Dapper install with the server install. Run the server install again. When you get to the DOS login , login and then issue this comand ```
sudo apt-get install ubuntu-desktop
```Reboot and you will have Dapper Drake.
All the Ubuntu's (Ubuntu, Kubuntu, Xubuntu and Edubuntu) all start with the server base. It is the desktop that makes them diferent. They are Gnome, KDE and XFCE.
Each can be installed after the server install by issuing the install desktop command . It is the same for all of them, it is just the prefix that changes
```
sudo apt-get install [COLOR="Red"]?[/COLOR]buntu-desktop
```

---

