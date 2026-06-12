---
title: "Make command not found (Solved)"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by clix on 2005-11-04
Hi guys, need some help, im a uber noob whit linux, i just wanted to get my wireless working, and needed to install ndiswrapper, but when i trie, i get the error make command not found, also when i want to change my sources.list i cant overwrite this in the GUI, because i dont have the permissions, how can i change that?

thnx in advance..

---

### Post by invalid on 2005-11-04
[QUOTE=clix]Hi guys, need some help, im a uber noob whit linux, i just wanted to get my wireless working, and needed to install ndiswrapper, but when i trie, i get the error make command not found[/QUOTE] 
```
sudo apt-get install build-essential
```

[QUOTE=clix]also when i want to change my sources.list i cant overwrite this in the GUI, because i dont have the permissions, how can i change that?[/QUOTE]
```
sudo gedit /etc/apt/sources/list
```

Cheers,
Cb

---

### Post by clix on 2005-11-04
[QUOTE=invalid]```
sudo apt-get install build-essential
```

Oke thnx a lot, but the next problem  accurs, when i do

sudo apt-get install build-essential
i get the next error..

E: Invalid operation build-essential

---

### Post by invalid on 2005-11-04
[QUOTE=clix][QUOTE=invalid]```
sudo apt-get install build-essential
```

Oke thnx a lot, but the next problem  accurs, when i do

sudo apt-get install build-essential
i get the next error..

E: Invalid operation build-essential[/QUOTE]

Are you sure you typed this exactly? It looks like you left out the "install" flag by mistake.

Cheers,
Cb

---

### Post by clix on 2005-11-04
Yes sorry my Update Manager wass still open, thats why he didnt respond, which sources.list i can use best ?

I found a few on the internet but which one is safe to use ?

Thnx a lot man, youve really helped me out here!

---

### Post by invalid on 2005-11-04
[QUOTE=clix]Yes sorry my Update Manager wass still open, thats why he didnt respond, which sources.list i can use best ?

I found a few on the internet but which one is safe to use ?

Thnx a lot man, youve really helped me out here![/QUOTE]

Here is a common list (provided you are using Breezy Badger)

```
#deb cdrom:[Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse
```

Cheers,
Cb

---

### Post by clix on 2005-11-04
Next question if you dont mind, also i cant find any1thing for that on the internet,

clix@ubuntu:~/downloads/ndiswrapper-1.5$ apt-get install gcc

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory

Do you also hava a answer for this ?

---

### Post by invalid on 2005-11-04
[QUOTE=clix]Next question if you dont mind, also i cant find any1thing for that on the internet,

clix@ubuntu:~/downloads/ndiswrapper-1.5$ apt-get install gcc

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory

Do you also hava a answer for this ?[/QUOTE]

```
sudo apt-get install gcc
```
You must be a superuser to run apt-get.

Cheers,
Cb

---

### Post by clix on 2005-11-04
Oke thn, already done that, however, this is the complete error i get.

make -C driver
make[1]: Entering directory `/home/clix/downloads/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/clix/downloads/ndiswrapper-1.5/driver \
        DRIVER_VERSION=1.5
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/clix/downloads/ndiswrapper-1.5/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/clix/downloads/ndiswrapper-1.5/driver/hal.o] Error 127
make[2]: *** [_module_/home/clix/downloads/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/clix/downloads/ndiswrapper-1.5/driver'
make: *** [all] Error 2
clix@ubuntu:~/downloads/ndiswrapper-1.5$

---

### Post by invalid on 2005-11-04
[QUOTE=clix]Oke thn, already done that, however, this is the complete error i get.

make -C driver
make[1]: Entering directory `/home/clix/downloads/ndiswrapper-1.5/driver'
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/clix/downloads/ndiswrapper-1.5/driver \
        DRIVER_VERSION=1.5
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/clix/downloads/ndiswrapper-1.5/driver/hal.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/clix/downloads/ndiswrapper-1.5/driver/hal.o] Error 127
make[2]: *** [_module_/home/clix/downloads/ndiswrapper-1.5/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/clix/downloads/ndiswrapper-1.5/driver'
make: *** [all] Error 2
clix@ubuntu:~/downloads/ndiswrapper-1.5$[/QUOTE]

```
sudo apt-get install gcc-3.4
```

Cheers,
Cb

---

### Post by clix on 2005-11-04
Thnx a lot man!

U rock dude really, know i have the next problem..

clix@ubuntu:~/downloads$ sudo ndiswrapper -l
Installed ndis drivers:
bcmql5  invalid driver!
bcmwl5  invalid driver!

Ive isntalled the windows drivers for my hp zv notebook 5231 broadcam 8011b but, i did this through this howto on a dutch site, you have a answer for this maybe ?

---

### Post by invalid on 2005-11-04
[QUOTE=clix]Thnx a lot man!

U rock dude really, know i have the next problem..

clix@ubuntu:~/downloads$ sudo ndiswrapper -l
Installed ndis drivers:
bcmql5  invalid driver!
bcmwl5  invalid driver!

Ive isntalled the windows drivers for my hp zv notebook 5231 broadcam 8011b but, i did this through this howto on a dutch site, you have a answer for this maybe ?[/QUOTE]

This is something I am not familiar with, unfortunatly.. you might try posting a new thread, and someone might be able to assist.

Cheers,
Cb

---

