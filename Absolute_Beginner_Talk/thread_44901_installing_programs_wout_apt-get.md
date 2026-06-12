---
title: "installing programs w/out apt-get"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by someone447 on 2005-06-28
how would I install a tar.gz file or anything like that.  I want to be able to download and install manually.

---

### Post by SGC on 2005-06-28
It differs from program to another , but basically 

- extracte the tar.gz ( tar zxfv PACKAGE.tar.gz )
- switch to where you extracte the files from the terminal (using **cd** command)

Then use the following commands:

[b]./configure
make
sudo make install[/b]

If you miss one of the program's dependency , you will get an error message after **./configure** , sometimes the error message contains the name of the dependency, install it and then try **./configure** again.

Installed programs by this methode is not easy to remove unless you keep the extracted files and then uses this command: **sudo make uninstall** 

So you need to install a program called checkinstall (sudo apt-get checkinstall) and then replace sudo make with **checkinstall -D make install**. Checkinstall will create a .dep package and will install it.

---

### Post by poofyhairguy on 2005-06-28
[QUOTE=someone447]how would I install a tar.gz file or anything like that.  I want to be able to download and install manually.[/QUOTE]


you need apt-get first. This command:

> sudo apt-get install build-essential

then compile what you will.

---

