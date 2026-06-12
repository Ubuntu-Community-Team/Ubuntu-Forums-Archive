---
title: "forgot one thing"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by Ob1 on 2006-09-13
How do i open/run a .sh file?

---

### Post by Crayoneater on 2006-09-13
you can type, in a terminal:
sh file_name.sh

you might have to run with sudo though:
sudo sh file_name.sh

---

### Post by andb on 2006-09-13
you may also have to make it executible. Type
```
ls -l
```
to see the atributes. It should look like:
```
-rwxr-xr-- 1 andrew andrew  691 2006-09-12 11:53 startup.sh
-rw-r--r-- 1 andrew andrew  696 2006-09-12 11:54 startup2.sh
```
The first file, startup, will execute, the second wont, as its mising the little "x" which shows that its executable. To change you need to set the executable bit.

either
sudo chmod u+x FILENAME
or
sudo chmod 744 FILENAME[/code]
Its best to make it executable only by the owner, so others cant run it. You may need to specify the whole path, or change into the directory then type ./FILENAME
This is so that if you had a file in your current directory which had the same name as a command, the command would be called instead of the file in the directory.

Only run a script as sudo if its needed, for example when installing video drivers. Otherwise its best to keep a policy of using the least possible level of permission to do a task, which help make sure that you dont crash something or mess something up. For example, many games, like darwinia, install into your home directory. So no need to use sudo.

---

