---
title: "Where to put this packages"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by JnMrno on 2005-12-14
hi
Im not able to connect to internet from my ubuntu computer, because of that when I start the synaptic it tryes to download package information and repositories that leads it to an error since there is no connection to download something. So what I did was download those things from this pc and pass it to that pc, but I don't know where to put all those packages and repositories for the synaptic to detect it or simply how to install them, of course if that is what is necesary.
I also need the dhcp3-server, where to get it, where to place it or how to install it ???
Hope to make sense
thanks

---

### Post by drummer on 2005-12-14
Well.. if you need to download packages that appear in synaptic but from another computer, go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and you can search for and download the packages you need. Also take note of each packages' dependancies. Once they are copied to your computer you have to install then with dpkg instead of through synaptic or apt. To do this, open up a terminal and navigate to the folder that holds the packages you copied and install then with dpkg thus:```
cd /folder/with/packages
sudo dpkg -i package.deb
```

---

### Post by aysiu on 2005-12-14
This may help:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by JnMrno on 2005-12-14
ok, i just tried that, but there's an error because the package is .gz not .deb..:???:

---

### Post by JnMrno on 2005-12-14
what to do then ?

---

### Post by drummer on 2005-12-14
.tar.gz is a tarball (like a zip) of the program source. I'd recommend going to packages.ubuntu.com and downloading a .deb which can be installed with dpkg or using asiyu's method. That would probably be easier, but if you want, to install a package from source, you will have to compile it first. If you want to try compiling, first install build-essential from synaptic (it's on the Ubuntu CD so won't need an internet connection) then go to the directory with the .tar.gz and do:```
tar xzvf <program>.tar.gz
cd <program>
./configure
make
sudo make install
```

---

### Post by JnMrno on 2005-12-14
ok, i'll look up.
they are not .tar.gz, they are simply .gz
and cannot do the cd thing because the laptop that runs ubuntu doesn't have a burner:( 
but thanks anyways

---

