---
title: "how can I run/install rpm packs ?"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-17
there are alot of .rpm packages on the net
but I always getting errors while trying to open them
why ? and how can I install them on ubuntu 6.06 ?

---

### Post by SSamiK on 2006-06-17
Ubuntu dont support rpm's out of the box, as deb is the packages manly used. 
Installation of rpm's are however not a big problem. 

Just convert the rpm's to deb's with alien


First, install alien:
(all commands in terminal)

sudo apt-get install alien 

Then to convert:

sudo alien package_file.rpm 
(possible case sensitive file ext.. "package_file.RPM" may not work, but renaming to "package_file.rpm" may solve the problem...  ;-) )
 
And you should have a deb you can install by typing:
sudo dpkg -i package_name.deb
(or just click on it...)

---

### Post by nitricacid on 2006-06-17
RPM is the exact same to a ZIPped file.
You can extract RPMs and then you can manually place the contents into the currect System folders using either the terminal (sudo mv <files>) or Nautilus by typing ```
sudo nautilus
``` into a terminal.

I install all my rpm files by just extracting them and manually placing the files to their corrisponding file names.

---

### Post by Jagot on 2006-06-17
[http://monkeyblog.org/ubuntu/installing/#rpm](http://monkeyblog.org/ubuntu/installing/#rpm)

---

