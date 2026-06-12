---
title: "pwi converter installation"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by nichanson on 2007-04-01
Hi
I would like to get this converter working for my pc as I need to convert some pocket word documents. I have downloaded the file but have no idea what to do. If someone can explain to me how to install this tar I'll most appreciate it (as simple as possible). 

[http://adrian.dimulescu.free.fr/article.php3?id_article=10](http://adrian.dimulescu.free.fr/article.php3?id_article=10)

---

### Post by nixclusive on 2007-04-01
Hello there, this looks like a 'Installation from source' scenario. Open the terminal and change the directory to whereever you have downloaded the file. Execute the following command to untar the archive:
```
tar zxvf pwi2html-0.2.tar.gz
```
Now a directory called pwi2html-0.2 should be created. Enter the directory and execute the command:```
./configure && make
```

This should build you an executable binary of the software. Execute the binary by entering: ```
./pwi
```

You may or may not have all the dependencies required by the program. In that case, you will need to install some of the -dev packages for the build. Good Luck..

---

