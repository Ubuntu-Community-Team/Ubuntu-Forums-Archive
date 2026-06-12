---
title: "[SOLVED] Can't install build-essential or linux-headers"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Zigon on 2007-08-02
```
zigon@zigon-desktop:~$ sudo apt-get install build-essential linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```

---

### Post by aysiu on 2007-08-02
Can you post the output of these commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by Zigon on 2007-08-02
> **aysiu said:**
> Can you post the output of these commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```

zigon@zigon-desktop:~$ sudo apt-get update
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_CA
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_CA
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_CA
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Fetched 190B in 1s (142B/s)
Reading package lists... Done
zigon@zigon-desktop:~$ cat /etc/apt/sources.list
cat: /etc/apt/sources.list: No such file or directory

---

### Post by aysiu on 2007-08-02
Well, you don't have an /etc/apt/sources.list. That could be the problem!

Paste this command into the terminal: ```
sudo nano /etc/apt/sources.list
``` This will create a sources.list file and open it in the text editor called Nano. Then, paste this in: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
``` Save (Control-X, Y, Enter) and finally paste in this command: ```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by Zigon on 2007-08-02
TADA, thanks for your help. Although I still don't think I'll be able to use the "make" command. Everytime I try to run that I get
```
zigon@zigon-desktop:~/Desktop/ndiswrapper-1.47$ sudo make
make -C driver
make[1]: Entering directory `/home/zigon/Desktop/ndiswrapper-1.47/driver'
Can't find kernel build files in /lib/modules/2.6.20-16-386/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/zigon/Desktop/ndiswrapper-1.47/driver'
make: *** [all] Error 2

```

sudo make install returns the same output. 3'd day with ubuntu installed and trying to set my wireless and everything else up is driving me insane.:mad:

---

### Post by aysiu on 2007-08-02
Try this: ```
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by Zigon on 2007-08-02
That worked =D Thanks soo much for your help.

---

### Post by Frak on 2007-08-02
Just a heads up, if you get a repo to add to the sources.list, only add it to the bottom. Don't overwrite everything else. I done this the first time I used Ubuntu also.

---

