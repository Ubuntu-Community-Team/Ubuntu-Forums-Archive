---
title: "Installing a packet, how?"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by Asael Nathlin on 2006-04-14
As the topic said. Well, this is my situation. I have just installed Ubuntu Breezy 5.10 on my desktop in a dual boot with windows. It works great and all, except for my LAN card under ubuntu. In order to get it running, i have downloaded the correct drivers with my laptop in a tar.gz packet.

Now here is where the problems start. I have no idea how to get those drivers in ubuntu and to get my card running. Sofar i have tried to install it via the command line (sudo apt-get sis190191_linux.tar.gz) but that is only opening the packet, leaving me without a clue on what to do with it. And i may have also busted the Synaptic packetmanager a bit by adding another location for the Ubuntu updates and modding the location into the location of the packet.

Can anybody help me with installing my LAN card drivers?

---

### Post by rmjokers on 2006-04-14
A .tar.gz file in linux is like a zip file in windows.  You need to extract the contents before you can do anything with the file.  This can either be done using nautilus (just double-click in file browser to open or right-click to extract) or from the command line:

tar xvzf YOUR_FILE

There should be instructions in the package or from the website where you found the drivers on how to install it at that point.

---

### Post by Ferri on 2006-04-14
Once you have extracted the file, there's usually some README file of something like this. The most of times you'll have to go through this sequence, from command line, in the folder you have extracted:
```
./configure
make
sudo make install
```
Or
```
./configure && make && sudo make install
```
The configure script may give you some errors because you may not have all the packages you need; usually you can install the using apt-get.

---

