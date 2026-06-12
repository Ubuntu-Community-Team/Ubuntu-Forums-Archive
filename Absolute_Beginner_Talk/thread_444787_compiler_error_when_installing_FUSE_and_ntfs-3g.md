---
title: "compiler error when installing FUSE and ntfs-3g"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-05-15
i am trying to set up my dual boot system (winXP/feisty) so i have full read/write permissions when mounting my windows hdd
i have no internet on ubuntu so i have transfered the latest ntfs-3g package and latest FUSE package to the computer using another, i extracted the files fine, but when i try to run the ./configure command it flashes a load of text, ending in something about the compiler not being able to run executables
i think i need to install the gdk software developers pakage, but have no idea how to do this without internet
i have a edgy live disk and a feisty alternate install disk, is there any way of using these to help??
thanks

---

### Post by Bachstelze on 2007-05-15
Is there any reason why you're compiling ntfs-3g from source and not installing it with the Ubuntu package ?

---

### Post by simon303 on 2007-05-15
> **HymnToLife said:**
> Is there any reason why you're compiling ntfs-3g from source and not installing it with the Ubuntu package ?

i have no internet, and dont want to install from scratch again

---

### Post by Bachstelze on 2007-05-15
If you have no Internet, Ubuntu is not for you. It will be a nightmare to install pretty much anything...

Anyway, you can download the packages from the other computer and install them too.

---

### Post by simon303 on 2007-05-15
im working on the internet problem, my ethernet card is the problem

the other computer is running windows, how would i go about downloading packages on it. then how would i install them on the ubuntu computer?

---

### Post by Bachstelze on 2007-05-15
Get the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com)

Copy them to your Ubuntu box - with an USB stick, CD-RW, whatever - and install them with

```
sudo dpkg -i filename.deb
```

For example, assuming you downloaded the Feisty package for ntfs-3g and put it on your desktop, you wold do

```
sudo dpkg -i ~/Desktop/ntfs-3g_1.328-1_i386.deb
```

---

### Post by simon303 on 2007-05-15
looking in [http://packages.ubuntu.com/feisty/otherosfs/ntfs-3g](http://packages.ubuntu.com/feisty/otherosfs/ntfs-3g) and cannot seem to find the aproppriate package, tried downloading ntfs-3g_1.328.orig.tar.gz but it didnt work when i came to install it

---

### Post by Bachstelze on 2007-05-15
Just use the "Search" field. Type in the name of the package, choose your Ubuntu release, voilà :)

---

### Post by simon303 on 2007-05-16
thanks, its all working now, ntfs-3g is installed and fully functioning

---

