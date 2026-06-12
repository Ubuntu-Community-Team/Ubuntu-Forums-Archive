---
title: "2 things"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Psyclown on 2007-04-27
One, im running wine and i would like to get into my C drive.. or C drive ish thing and im wondering where wine keeps all those files (Program files and the like) 

and two, i  cant double click on an exe and when i try to run it in a terminal window...well..

danny@danny-desktop:~$ /home/danny/Desktop/MBD/ATI2/Setup.exe
bash: /home/danny/Desktop/MBD/ATI2/Setup.exe: Permission denied

anybody know anything on that one?

and three i guess, i just tried to install itunes via wine, it worked.. or it looked like it did.. and now i cant accss it through anything.. i tried searching for the exe, nothing, i tried going to Apps>Wine>Programs. nothing? any ideas there? any help would be nice

---

### Post by easyease on 2007-04-27
wine isnt a real map of your windows drive, you need to mount your windos drive properly. is it FAT32 OR NTFS?

---

### Post by josephus on 2007-04-27
- the c drive is under ~/.wine/drive_c

- if want to run windows executables from the command line:  wine <filename>

- you might find itunes under in the Program Files directory under ~/.wine/drive_c

---

### Post by Psyclown on 2007-04-27
well its defenitly not in the system... i just throughly (sp?) with through my entire file system and nothing lik drive_c on it nor was there any folders called win that had a drive c in it. my HDD is whatever it makes it when you delete everything off it and let unbuntu do its work.. im guessing the not fat32 one... cause ya when i install itunes it goes off into some random directory and i have no idea how to access it. so am i going to have to partition a windows part of my hard drive? any help would be awsome.

---

### Post by NICU on 2007-04-27
Like Josephus said - the c drive is under ~/.wine/drive_c

There are a lot of hidden files in your home directory that don't show up by default in the GUI file manager.  Go to your home directory in a terminal and type ```
ls -al
``` You'll see all the nice hidden files/directories that are stashed away for you.

---

### Post by az on 2007-04-27
Wine puts stuff in its directory in your home drive.  All your app's configuration are in dotfiles (/home/you/.mozilla or /home/you/.programconfig)  Files starting with a period are hidden.  Show hidden files and then go into your home directory's .wine subdirectory and your wine's drive c will be there.

---

### Post by Duck2006 on 2007-04-27
In your /home/you/ if you can't see the /.folders  then press ctrl + h and you sould see then

---

