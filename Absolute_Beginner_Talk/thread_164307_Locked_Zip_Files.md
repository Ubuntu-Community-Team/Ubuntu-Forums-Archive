---
title: "Locked Zip Files"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Wagz on 2006-04-22
I downloaded a file to the desktop and extracted it to the desktop and discovered the unzipped files had a padlock on the top right-hand corner of the icon. Of course, I was unable to run the exe file.  Is this a security feature and is there something I need to do to be able to run this executable?  Using 5.10, btw, and eager to get started with my first Linux experience.


Apologies if this has been reported about before, couldn't find in the forum search.

---

### Post by jrib on 2006-04-22
The lock means you don't have permissions to edit the file.  A .exe file is generally for windows, so unless you run it through wine, it won't do much.  What are you trying to do?

---

### Post by Wagz on 2006-04-22
[QUOTE=_jason]The lock means you don't have permissions to edit the file.  A .exe file is generally for windows, so unless you run it through wine, it won't do much.  What are you trying to do?[/QUOTE]
I was downloading the driver for the Linksys USB adapter driver prior to using ndiwrapper (sic?) so that I can connect to the Internet using my wireless USB adapter.  I was under the impression that I needed to install the driver before doing anything else.

---

### Post by jrib on 2006-04-22
I have never used ndiswrapper, but I believe you only need to extract the .inf files (try opening it with archive manager?).  Maybe someone else that has done it, can be more helpful

---

### Post by dbmnk on 2007-04-22
bump

I'm having the same issue with locked zip-files and folders

carnt even move the files about. its drivers

what the reason and solution for this?

---

### Post by Seisen on 2007-04-22
You can't move the files because you are not a root user, your are just a normal user. You two options, use root or you can do this in the terminal.

```
gksudo nautilus
``` it will give you super user privileges until you close nautilus. It's better than using root account because you only have temp. privileges.

---

