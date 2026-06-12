---
title: "how to install software without internet connection"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by threeonethree on 2007-07-08
hey .. i have a friend with an ati card who would like to install beryl on his system.. after reading a lot , i found out that he needs to install beryl-xgl and other things to make it work .. but the problem is that he just has a 64 kbps connection. it takes  ALOT of time to download stuff on his pc cus it only gives about 3 KBPS speed when downloading. and sudo apt-get update takes a lot of time too ..

i have a 2mbps connection .. i would like to know is there a way by which i can download these packages and other things that he needs for him and then go to his home with the stuff so he can install? .. please tell how

---

### Post by pyros on 2007-07-08
> **threeonethree said:**
> hey .. i have a friend with an ati card who would like to install beryl on his system.. after reading a lot , i found out that he needs to install beryl-xgl and other things to make it work .. but the problem is that he just has a 64 kbps connection. it takes  ALOT of time to download stuff on his pc cus it only gives about 3 KBPS speed when downloading. and sudo apt-get update takes a lot of time too ..

i have a 2mbps connection .. i would like to know is there a way by which i can download these packages and other things that he needs for him and then go to his home with the stuff so he can install? .. please tell how

I am assuming that you are running ubuntu? well, either way, I've always done this by looking at the dependencies and saving them to disk. Then he can just double-click on the .deb files and the gdebi-gtk installer will let you install it. If you missed anything, it can be downloaded, but at least you have the bulk of it.

I don't know how to get it to look at your disk for the dependencies (without creating a mirror disc, anyway) so the last one you want to install is the beryl-xgl

---

### Post by threeonethree on 2007-07-08
yes i have ubuntu feisty fawn. thanks for ur help .. can u tell me how can i download those dependencies/.deb files ?? because when i try sudo apt-get install xserver-xgl on my system it says


kartik@ubuntu:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1767kB/1843kB of archives.
After unpacking 4825kB of additional disk space will be used.
Do you want to continue [Y/n]? 


but that will install it on my pc too .. how can i DOWNLOAD those packages to a directory ?? and once i take them to my friends pc, do i just need to double click on each of them to install ? or do i need to put them in a specific directory and type apt-get install bla bla and it will install?

---

### Post by pyros on 2007-07-08
```
sudo apt-get build-dep -d beryl-xgl
``` should download the files you need to install beryl-xgl on your system. The "-d" part tells apt to download the files without installing them. that should also give you a list of what .deb files you need to install it. take that list and go look in ```
/var/cache/apt/archives/
```. that;s where apt will save the .deb files.

Hope that helps

---

### Post by masterd on 2007-07-08
:)

---

