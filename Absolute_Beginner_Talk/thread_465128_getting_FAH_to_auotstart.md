---
title: "getting FAH to auotstart"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by luigi44 on 2007-06-05
cant get fah to autostart, followed this guide - [http://ubuntuforums.org/showthread.php?t=12071&highlight=fah](http://ubuntuforums.org/showthread.php?t=12071&highlight=fah)

it seems pushd & popd are not being detected - this is the output from terminal:

luigi@ubuntu:~$ sudo /etc/init.d/foldingathome start
Password:
/etc/init.d/foldingathome: 5: pushd: not found
/etc/init.d/foldingathome: 7: popd: not found
luigi@ubuntu:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
luigi@ubuntu:~$ pushd 
bash: pushd: no other directory
luigi@ubuntu:~$ man pushd
No manual entry for pushd
luigi@ubuntu:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
luigi@ubuntu:~$ 

thanks in advance

---

### Post by Seisen on 2007-06-05
Where is your folding@home directory located?

---

### Post by luigi44 on 2007-06-05
/home/luigi/folding

---

### Post by jpkotta on 2007-07-02
[https://help.ubuntu.com/community/FoldingAtHome](https://help.ubuntu.com/community/FoldingAtHome)

---

