---
title: "tar.gz"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-05-27
Can someone please step me through a tar.gz install please. I am having trouble installing it. It is xine.

Thanks very much, tom

---

### Post by barbarian on 2006-05-27
hi,
*man tar*

---

### Post by sam hassell on 2006-05-27
i use "tar xfvz filenamehere".

---

### Post by tommy1987 on 2006-05-27
ok i did that and it looked like it extracted files, what do i type next please? sorry im a n00b!

---

### Post by Sutekh on 2006-05-27
[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

Specifically Section 4. Installing from source

---

### Post by tkjacobsen on 2006-05-27
try to take a look at the README or INSTALL.

usually you have to```
./configure
make
sudo make install
```

if you miss some dependencies configure will tell you, and you can just install them using synaptic and try to ./configure again

---

### Post by chettyk on 2006-05-27
If you are new to Linux and don't know how to use tar, I suggest you don't go that route at this stage. It should be possible to install xine through Synaptic (System > Administration > Synaptic Package Manager) or through apt-get (using a terminal). You will probable have to enable additional repositories, though. 

I suggest you run a search on xine on this forum's search facility. I am sure there will be a thread that deals with how to install xine. 

As for adding additional repositories, take a look at:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Sef on 2006-05-27
This one is good too.

[http://monkeyblog.org/ubuntu/installing.html]("http://monkeyblog.org/ubuntu/installing.html")

---

### Post by barbarian on 2006-05-27
here also nice source:

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by barbarian on 2006-05-27
:)

---

### Post by chettyk on 2006-05-27
This thread **how do i install xine** may be what you are looking for:
[http://ubuntuforums.org/showthread.php?t=117139](http://ubuntuforums.org/showthread.php?t=117139)

---

### Post by patrick295767 on 2006-05-27
0/ you'll / can  need this : 
```

apt-get update
################ make install !! ##############"
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make mc
apt-get -f -y install build-essential
apt-get -f -y install tcl8.4 
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev

## for building, make ... checkinstall
apt-get install -f -y kdevelop kdevelop3-dev build-essential checkinstall

##### amsn  installation
apt-get -f -y install gcc 
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential tcl8.4-dev tk8.4-dev imlib11-dev esound-clients
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
apt-get -f -y install linux-headers-$(uname -r)
apt-get -f -y install build-essential 
```
 
in case you 'll need more (vmware):
```


## voor vmware
apt-get -f -y install make
apt-get -f -y install build-essential
apt-get -f -y install gcc-3.4
apt-get -f -y install build-essential 
apt-get -f -y install zenity
apt-get -f -y install linux-tree
apt-get -f -y install g++-3.4
cat /proc/version
ls /usr/bin/gcc*
rm -rf /usr/src/linux
apt-get -f -y install linux-headers-$(uname -r)
ls /usr/bin/gcc*
ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
rm /usr/bin/gcc
ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
rm /usr/bin/gccbug
ln -s /usr/bin/gccbug-3.4 /usr/bin/gccbug
CC=/usr/bin/gcc-3.4
export CC
apt-get -f -y install
apt-get -f -y install

######## installing qt3
apt-get -f -y install qt3-dev-tools
apt-get -f -y install qt3-apps-dev
apt-get -f -y install libqt3-headers
apt-get -f -y install qca-dev
apt-get -f -y install libqt3c102-mt
export QTDIR=/usr/share/qt3

##########end ###### make install !! ##############"


```

1/ unpack your sources, it with mc 

2/ go where u unpack the folder

3/ ./configure
make 
make install
  
Enjoy the sources !!
  
Should be working now !! :KS :KS :KS :KS

---

