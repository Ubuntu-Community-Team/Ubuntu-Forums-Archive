---
title: "Problem with tar.gz"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by darby on 2005-07-26
Trying to install Moneydance.
I have unzipped the downloaded file and it is in /home/username/ I then cd to /home/username/moneydance and enter ./configure but get bash no such file or directory.

What am I missing please?

---

### Post by Xian on 2005-07-26
Not all packages are installed using the configure procedure.
In the source folder there should be a readme and/or install text file.
Read those for more information.

The package probably comes with its own installer.

---

### Post by sophtpaw on 2005-07-26
[QUOTE=Xian]Not all packages are installed using the configure procedure.
In the source folder there should be a readme and/or install text file.
Read those for more information.

The package probably comes with its own installer.[/QUOTE]


try sudo dpkg -i ~/package nameblahblah.deb

---

### Post by az on 2005-07-26
ls
cat README|less


In other words, read the ReadMe.

---

### Post by darby on 2005-07-26
Thanks to all who replied.

Moneydance has an internal .exe file.

---

