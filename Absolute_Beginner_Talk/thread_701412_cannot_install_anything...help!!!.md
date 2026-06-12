---
title: "cannot install anything...help!!!"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-02-19
i wanted to install pcsx2 so i started by following the procedure on [http://ubuntuforums.org/showthread.php?t=399165](http://ubuntuforums.org/showthread.php?t=399165) but then i run on some problems
i think this is because during the installation i was asked for the cd which i never inserted because i didn't have it....
so i tried to reinstall through the terminal and it gives me the following message: 
```

select@select-laptop:~$ sudo apt-get install subversion libjpeg62-dev build-essential libgtk2.0-dev libxxf86vm-dev x11proto-xf86vidmode-dev automake1.9 libbz2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
libjpeg62-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libxxf86vm-dev is already the newest version.
x11proto-xf86vidmode-dev is already the newest version.
automake1.9 is already the newest version.
libbz2-dev is already the newest version.
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  build-essential: Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  libstdc++6-4.1-dev: Depends: g++-4.1 (= 4.1.2-16ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

```

if pcsx2 cannot work ok but i do need install ;)
any ideas?

---

### Post by Sinkingships7 on 2008-02-19
applications -> add/remove

make sure that the box on the top right says "all available applications" and search pcsx in the search box at the top. check and press "apply changes"

---

### Post by philinux on 2008-02-19
Good ole ubuntu it gives you a clue.
You might want to run ‘apt-get -f install’ to correct these:

so run

sudo apt-get -f install

---

### Post by Sinkingships7 on 2008-02-19
also. try just this in your terminal:
```
sudo apt-get install build-essential
```
that will install the tools your computer needs to install from source code.

---

### Post by yabbies on 2008-02-19
> The following packages have unmet dependencies.
  build-essential: Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  libstdc++6-4.1-dev: Depends: g++-4.1 (= 4.1.2-16ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).

you are in dependency hell:
you need to install 
g++
dpkg-dev

go to system>admin>synaptic package
and search for the depends you need and install.

---

### Post by Anicka on 2008-02-19
Try```
sudo apt-get install -f build-essential
```Also make sure that you have the necessary repos enabled. Could you post you source list?```
cat /etc/apt/sources.list
```You can use the GUI to change the source list in system -> administration -> software sources

---

### Post by someoneouthere on 2008-02-19
i just need it to follow all the above and worked

thanks a lot :)

---

