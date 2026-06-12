---
title: "Help Please!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Tootles on 2007-09-08
Ok I download WinRar as a tar.gz file, and i extracted the the file to desktop
folder name is called rar
how do i run the actual program
i want to extract a rar file with it

---

### Post by diatribe on 2007-09-08
the name of the executables are unrar and rar, respectively, in the rar directory

---

### Post by Tootles on 2007-09-08
sergey@sergey-desktop:~$ d ~/Desktop/rar
bash: d: command not found
sergey@sergey-desktop:~$ cd ~/Desktop/rar
sergey@sergey-desktop:~/Desktop/rar$ ls
default.sfx  Makefile   rarfiles.lst  readme.txt    whatsnew.txt
file_id.diz  order.htm  rar_static    technote.txt
license.txt  rar        rar.txt       unrar
sergey@sergey-desktop:~/Desktop/rar$
sergey@sergey-desktop:~/Desktop/rar$ makefile
bash: makefile: command not found
sergey@sergey-desktop:~/Desktop/rar$ default.sfx
bash: default.sfx: command not found
sergey@sergey-desktop:~/Desktop/rar$ cd ~/Desktop/rar
sergey@sergey-desktop:~/Desktop/rar$ ls
default.sfx  Makefile   rarfiles.lst  readme.txt    whatsnew.txt
file_id.diz  order.htm  rar_static    technote.txt
license.txt  rar        rar.txt       unrar
sergey@sergey-desktop:~/Desktop/rar$ default.sfx
bash: default.sfx: command not found
sergey@sergey-desktop:~/Desktop/rar$
WHAT DO I DO NEXT?

---

### Post by diatribe on 2007-09-08
./unrar path_to_file.rar will unrar your file

---

### Post by Amazona aestiva on 2007-09-08
If the downloaded package is a source code, this might install winrar:

However I advise to use RARTools to extract or compress files!

1.Open terminal and type:
```
cd ~/Desktop/rar
```
2.Type this to install Winrar:
```
./configure
```
3.Type:
```
make
```
4.Type:
```
sudo checkinstall
```

---

### Post by Tootles on 2007-09-08
what can u post the first command again?

---

### Post by bodhi.zazen on 2007-09-08
You do realize you can user rar and Archive manager without Winrar ?

sudo apt-get install rar urar

Then right click on a .rar and extract :)

To answer your question though, you need to make && make install, but you need build essentials first

So, 

```
cd ~/Desktop/rar
sudo apt-get install build-essential
make
sudo make install
```

@Amazona aestiva : You do not need to configure if there is already a makefile

---

### Post by Tootles on 2007-09-08
sergey@sergey-desktop:~/Desktop/rar$ cd ~/Desktop/rar
sergey@sergey-desktop:~/Desktop/rar$ sudo apt-get install build essential
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build
sergey@sergey-desktop:~/Desktop/rar$ make
mkdir -p /usr/local/bin
mkdir -p /usr/local/lib
cp rar unrar /usr/local/bin
cp: cannot create regular file `/usr/local/bin/rar': Permission denied
cp: cannot create regular file `/usr/local/bin/unrar': Permission denied
make: *** [install] Error 1
sergey@sergey-desktop:~/Desktop/rar$ make install
mkdir -p /usr/local/bin
mkdir -p /usr/local/lib
cp rar unrar /usr/local/bin
cp: cannot create regular file `/usr/local/bin/rar': Permission denied
cp: cannot create regular file `/usr/local/bin/unrar': Permission denied
make: *** [install] Error 1
sergey@sergey-desktop:~/Desktop/rar$

---

### Post by bodhi.zazen on 2007-09-08
Ooops, me bad

It is build-essential

sudo apt-get install build-essential

AND

you need sudo with make install

sudo make install

---

### Post by diatribe on 2007-09-08
it actually looks like he has to use sudo with make also

---

### Post by Tootles on 2007-09-08
ok, theres nothing in the files.. great

---

### Post by diatribe on 2007-09-08
in what files?

---

