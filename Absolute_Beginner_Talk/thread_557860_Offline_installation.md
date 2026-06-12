---
title: "Offline installation"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by apparle on 2007-09-23
I am new user to linux and I use Kubuntu Feisty fawn 7.04 i386
I donot have net at my place and use it at my college (old WinXP)
When I wanna install something I download it then it shows a missing library then I download it.
Next time another library. and this goes on.
Can any software make a list of all the libraries required for a package which are not installed on my PC in text document

---

### Post by banewman on 2007-09-23
I use synaptic package manager to handle all installs and it solves any dependency issues before installation. How are you doing your installs ?
If you are trying to install from xp then the dependencies won't be addressed - as you have found out. Is the issue that you can't use your college 
internet access with ubuntu ?

---

### Post by por100pre1 on 2007-09-23
In [http://packages.ubuntu.com/](http://packages.ubuntu.com/) when you browse a package (lets see [k3b]("http://packages.ubuntu.com/feisty/otherosfs/k3b") for example), you get a list of dependencies. Be sure to get all dependencies for your software, specially those marked red and green. Try downloading the [Ubuntu DVD]("http://nginyang.uvt.nl/") too, and use it as a local repository in your Ubuntu PC.

---

### Post by mcduck on 2007-09-23
Actually apt-get has option to just output a list of packages it _would_ install. This is easy way to get all the dependencies.

```
sudo apt-get install --print-uris package1 package2
```

The downside is that if the machine is never connected to repositories it won't know what are the latest package versions available, and also you can't get it to work with universe and multiverse repositories without connecting to internet at least once to donwload the repository indexes.

> 
--print-uris
    Instead of fetching the files to install their URIs are printed. Each URI will have the path, the destination file name, the size and the expected md5 hash. Note that the file name to write to will not always match the file name on the remote site! This also works with the source and update commands. When used with the update command the MD5 and size are not included, and it is up to the user to decompress any compressed files. Configuration Item: APT::Get::Print-URIs.


---

### Post by apparle on 2007-09-27
> **banewman said:**
> I use synaptic package manager to handle all installs and it solves any dependency issues before installation. How are you doing your installs ?
If you are trying to install from xp then the dependencies won't be addressed - as you have found out. Is the issue that you can't use your college 
internet access with ubuntu ?
The computers in my college have windows XP
whereas my desktop has Kubuntu

---

### Post by apparle on 2007-09-27
> **por100pre1 said:**
> In [http://packages.ubuntu.com/](http://packages.ubuntu.com/) when you browse a package (lets see [k3b]("http://packages.ubuntu.com/feisty/otherosfs/k3b") for example), you get a list of dependencies. Be sure to get all dependencies for your software, specially those marked red and green. Try downloading the [Ubuntu DVD]("http://nginyang.uvt.nl/") too, and use it as a local repository in your Ubuntu PC.
I know if I get all the dependencies then the package will work.
but I want to download only those dependencies which I dont have

I cannot connect to net! not even once

---

