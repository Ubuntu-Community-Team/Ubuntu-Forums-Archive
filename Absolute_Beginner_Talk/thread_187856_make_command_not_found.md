---
title: "make command not found?????"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by rubrboots on 2006-06-03
I am trying to install a driver, that requires me to untar, make, and make install. But when I type ```
make
``` it says ```
command not found
```. How do I make in dapper?

---

### Post by cbudden on 2006-06-03
sudo apt-get install build-essential

---

### Post by rubrboots on 2006-06-03
I am trying to install a wifi so I dont have internet. The above command failed. Is there another way?

---

### Post by angkor on 2006-06-03
Maybe this works:

Download these .debs from [here]("http://packages.ubuntu.com/"):

```
apt-cache depends build-essential
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
  Depends: dpkg-dev
```

using a machine that does have internet (the one your using to get to this forum).

If you transfer them to your ubuntu box you can double-click them to install them. I hope it works cause I've never done it this way myself.

---

### Post by 5-HT on 2006-06-03
Apart from downloading the dependencies from a computer with net access, build-essential is on the alternate install CD if you have it.

---

### Post by patrick295767 on 2006-06-03
Hi, 

You might pick up what you need ... 
Greetz'
  
```


apt-get update
################ make install !! ##############"
## this 3  lines for amsn 0.95 & also for vmware workstation
apt-get -f -y install make
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

---

### Post by jdong on 2006-06-03
Just out of curiousity, what wifi card/driver would this be?

We've tried very hard in Dapper to have out-of-the-box support for every wireless chipset that has Linux drivers of some sort.

---

