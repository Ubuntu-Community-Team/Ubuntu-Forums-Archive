---
title: "Permissions and how to enable my user access ?s"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Mukaeutsu on 2007-09-11
On my HDD i have
   20gb NTFS Windows Part
~32gb FAT32 Shared Files
   15gb ReiserFS Ubuntu
     2gb  Swap

I can read/write in Windows, Shared, and parts of Ubuntu partitions from Ubuntu, but files like /usr/shared/themes/ or /home it will not allow me to even create a single folder

is there a way to make my user be just as able as a root/admin, i am the only user of my computer unattended so i am not worried about what i can/cannot do

thanks for all suggestions in advance!

---

### Post by Nolander on 2007-09-11
well if Ur using a terminal then u need the 'sudo' command. u can use user group setup and put u in the root group but i don't recommend it. when do admin work on Ur computer use the terminal. ```
 sudo <filebrowser> /
```  replace file browser with the obvious. and u will b able to do stuff to protcted folders.

hope i helped,
Nolander

---

### Post by sumguy231 on 2007-09-11
> is there a way to make my user be just as able as a root/admin, i am the only user of my computer unattended so i am not worried about what i can/cannot do

You could do that by enabling the root password and getting gdm to allow you to log in as root, but that is a major security risk. I don't think you understand the ramifications of doing that.

---

### Post by mikewhatever on 2007-09-11
There are numerous security and usability disadvantages to be root or equivalent all the time. You can get temporary root privileges any time you wish to do things. For example, > gksudo nautilus will open nautilus and let you modify files and directories.
Another option is to use the CLI. The following will create a test directory in /usr/shared/themes/ > sudo mkdir test /usr/shared/themes/

---

