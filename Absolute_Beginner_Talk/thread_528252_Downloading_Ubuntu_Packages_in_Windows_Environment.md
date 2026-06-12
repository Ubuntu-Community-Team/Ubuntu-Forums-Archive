---
title: "Downloading Ubuntu Packages in Windows Environment"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Marcelo Riss on 2007-08-17
Hi !

I'm a beginner using Ubuntu and are facing the following situation.

My ubuntu machine is offline. It means that I'm not able to use the apt-get command line utility to download the packages. I have a windows machine connected and need to manually download .deb packages from ubuntu repositories so that a can manually install them in a later step. My question is: Is there any way to download an specific .deb package and all its dependencies in a windows environment? Currently I'm using the site [http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/), finding the packages I want and visually trying to guess what dependencies will be needed for the package installation (I don't know what packages are already installed at ubuntu machine). The windows machine is at my work and the ubuntu is at home.

Thanks in advance.

Marcelo Riss

---

### Post by wolfen69 on 2007-08-17
[http://www.getdeb.net/](http://www.getdeb.net/) is a good place to get packages. they install with only a click of the mouse.

---

### Post by por100pre1 on 2007-08-17
Download and burn an [Ubuntu DVD]("http://nginyang.uvt.nl/") in your Windows PC. Pop it in your Ubuntu PC and you'll be able to use it as a local repository to install many (but not all) Ubuntu packages. Hope this helps. :)

---

### Post by wosret on 2007-08-17
To get a list of the currently installed packages on your Ubuntu machine, run this from the console:
```
dpkg-query -W > package_list.txt
```
Now the file package_list.txt has the names and version numbers of every package installed on your system, sorted in alphabetical order.  On your Windows machine, you can open that file and search for the names of the dependencies of each package.  Be sure to open the list in WordPad, since Notepad doesn't correctly display files with UNIX line endings.  Also, after you install your new packages, don't forget to update your package_list.txt (just run the first command again).

Hope this helps!

---

### Post by SunnyRabbiera on 2007-08-17
edit nevermind...

---

