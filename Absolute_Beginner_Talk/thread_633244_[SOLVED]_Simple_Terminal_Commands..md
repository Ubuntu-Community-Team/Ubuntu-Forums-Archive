---
title: "[SOLVED] Simple Terminal Commands."
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by TidusBlade on 2007-12-06
Well, as I am pretty new to the terminal, can anyone please tell me any commands that allow me to change the name of a folder, and the command to move a certain folder to somewhere?
Thanks! :)

---

### Post by mali2297 on 2007-12-06
The command is **mv**. For more information, see
[http://www.linuxcommand.org/lts0050.php](http://www.linuxcommand.org/lts0050.php)

---

### Post by banewman on 2007-12-06
Sure. :)
If you type in terminal -  man mv  - you'll get the manual for moving a file.
e.g.  mv /home/me/Afile /home/me/Bfile renames Afile to Bfile
        mv /home/me/music/Afile /home/me/stuff - moves Afile from music to stuff
man cp for copy
e.g. cp /home/me/music/Afile /home/me/backup/
If it is a system file then you need to type sudo first.
Hope it gets you started and feel free to ask more questions.
:)

---

### Post by subs on 2007-12-06
> **TidusBlade said:**
> Well, as I am pretty new to the terminal, can anyone please tell me any commands that allow me to change the name of a folder, and the command to move a certain folder to somewhere?
Thanks! :)


**Current Working Directory.....**

> pwd


**Chnaging directory.......**

> cd [path_of_destination_directory]


**Listing all files in a dirctory....**

> ls


**To view the manual of any command....**

> man [command_name]


**Make directory**

> mkdir [dir_name_path]


**Remove directory/file**

> rm [file_path]
rmdir [dirpath]    <<<----- Directory mus be empty


Try googling up some more

---

### Post by pjkoczan on 2007-12-06
The command you're looking for is mv. Be careful when using it, because it will overwrite files if you don't give it the -i flag. In fact, look at the manual page for mv before using it (type "man mv" in a terminal).

[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal) has a bunch of useful commands and terminal tricks for the new user, and google will probably yield more results.

Enjoy using the terminal.

---

### Post by TidusBlade on 2007-12-06
Thanks guys! And thanks for the links aswell, hopefully I can know the basics of the terminal soon :)

---

### Post by Dr Small on 2007-12-06
Check this thread out too:
[http://ubuntuforums.org/showthread.php?t=171507&highlight=commands+for+newbies](http://ubuntuforums.org/showthread.php?t=171507&highlight=commands+for+newbies)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by TidusBlade on 2007-12-06
Thanks Small, I will after I finish my things here ;)

---

