---
title: "Qlix Anybody?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by spyder99 on 2008-04-14
I spent a few hours this weekend trying to get my Sansa Connect to work in Gutsy. I have installed the latest Libmtp and TagLib versions but I can't figure out how to install Qlix. Will Qlix work in Ubuntu?

---

### Post by y-lee on 2008-04-14
I never heard of Qlix till now but it should work. You have to download the source code, [Qlix-0.1.1a.tar.bz2]("http://prdownload.berlios.de/qlix/Qlix-0.1.1a.tar.bz2"), and then extract it somewhere and compile it.  I don't know what dependencies this program has but you definitely need the build-essential package and from what i gather also libqt4-dev-tools. be sure these are installed before you try to compile it. 

According to the INSTALL file that is found in Qlix-0.1.1a.tar.bz2

> To create a useable Makefile for your system configuration:
$qmake -o Makefile Qlix.pro

Then just type:
$make


Post back if you have any problems.

---

### Post by caffein on 2008-07-01
Hello, I am the author of Qlix, and I've managed to get together some deb files for Qlix 0.2. 
You can find my personal package archive here:
[https://launchpad.net/~caffein/+archive](https://launchpad.net/~caffein/+archive)

For instant gratification:

> $ sudo echo "deb [http://ppa.launchpad.net/caffein/ubuntu](http://ppa.launchpad.net/caffein/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list
$ sudo apt-get update
$ sudo apt-get install qlix

enjoy :)

---

### Post by caffein on 2008-07-23
Well looks like  I messed up with the debug information while creating the packages. I have since fixed it and for anybody googling this they'd be advised to use the debug packages. Here are the key-combos ;)
> 
echo deb [http://ppa.launchpad.net/caffein/ubuntu](http://ppa.launchpad.net/caffein/ubuntu) hardy main | sudo tee -a /etc/apt/sources.list
sudo apt-get update
sudo apt-get install qlix qlix-dbg


---

