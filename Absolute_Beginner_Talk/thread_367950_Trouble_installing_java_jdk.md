---
title: "Trouble installing java jdk"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by mr tim esquire on 2007-02-22
Hi there please help me
im trying to install JDK6 on my ubuntu ibook.  Ive downloaded the .bin file from sun, checked its fully dowloaded.  I chanded permissions *a+x* and then *sudo ./jdk-6-linux-i586.bin* but i get the error 

Unpacking...
Checksumming...
Extracting...
./jdk-6-linux-i586-rpm.bin: line 343: ./install.sfx.15694: cannot execute binary file

Ive also tried installing from the rpm.bin file but i get the same error here too

I have been having problems installing all sorts of files, maby i dont have some required package

help much appreciated 
tim

---

### Post by phossal on 2007-02-22
Try using *sudo*. The six-step method for installing the .bin is laid out in a lot of places. Follow the link in my signature for details.

---

### Post by mr tim esquire on 2007-02-22
thanks for the reply i have tried the way sugested in the how tos e.g

cd ~/Desktop
chmod +x jdk-6*.bin
sudo sh *.bin

but i always get the error at this point
 can you think of any reason this might be?
thanks friend

---

### Post by mr tim esquire on 2007-02-22
i tried the above cammand on my other machine and it worked fine! so the problem must be here...

I thought id try installing the JDK another way and folling the advice on helpful post:-
[http://www.ubuntuforums.org/showthread.php?t=358980&highlight=problems+installing+java+jdk](http://www.ubuntuforums.org/showthread.php?t=358980&highlight=problems+installing+java+jdk)

i tried the code 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports multiverse

but i get
deb: command not found

Im really having lots of problems with my install of ubuntu on this ibook
i havnt managed to compile or install any source code and this java install was so easy on my other machine

is there any way of resetting ubuntu packages to 'factory defaults'? without reinstalling. Incase some thing else ive installed is interfering

thanks very much for the help
tim

---

### Post by aktiwers on 2007-02-22
That is not a command.. its something you need to put in your sourcelist.

You can install automatix2. It will really help you out to start with. 
It will autoinstall a lot of stuff for you, jdk included:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by phossal on 2007-02-22
I know nothing of the ibook. Error messages due to architecture conflict? My experience is that the .bin file installation directly from SUN is the least likely way to run into conflicts with your *Ubuntu*, but it doesn't prevent architecture conflicts obviously.

---

### Post by mr tim esquire on 2007-02-24
oops... You need the ppc version which is offered by IBM
[https://help.ubuntu.com/community/Java?highlight=%28java%29#head-81c3789bc76872336f69a7af90d1759ef38eeb64](https://help.ubuntu.com/community/Java?highlight=%28java%29#head-81c3789bc76872336f69a7af90d1759ef38eeb64)

---

