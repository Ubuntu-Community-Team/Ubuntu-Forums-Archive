---
title: "need help installing package from a regular folder"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by ~vel on 2006-07-24
ok, so i have the wireless card listed here

[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111?highlight=%28WifiDocs%2FDevice%29)

and it says i neeed ndiswrapper as a prereq, so i went here

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

followed the instructions to uncompress it. then once i get to where it says

Go to the source-directory and run 'make distclean' and 'make'. As root, run 'make install'. This should compile and install both the kernel module and the userspace utilities. If you don't need USB support in ndiswrapper, with recent versions, you can compile with 'make DISABLE_USB=1' and install with 'make DISABLE_USB=1 install'.

i haven't a clue how to do that. i tried the commands in terminal and it didnt work (obviously i tried the wrong place). also, this is my first time even seeing linux infront of me at any computer (er, runing) and that being said, i am a complete noob to it. so if there's anything more i need (i've seen some stuff refering to a package called firestarter but i haven't looked into that yet due to my current dilemma). also thank you for anyone who even posts here, i'm really excited to get ubuntu runing smoothly on my computer. (kind of pathetic that i'm 15 eh?)

---

### Post by tzulberti on 2006-07-24
To do that, frist you should have installed the make command(sudo apt-get install make).
Then, you should open a terminal and use   the cd to move to the folder where the file was extracted. Then write "sudo" before using a command as root (for example: sudo make install").

You should look for a deb package, since it is much more easy to install.

---

### Post by aysiu on 2006-07-24
The compiling tools are available on both the Desktop CD and Alternate CD: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

