---
title: "Grrr. Can someone tell me what I am doing wrong? (installing network drivers)"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by shyopstv on 2006-04-03
I have ndiswrapper (at least I think I do... I used that synaptic thing to get it) and am trying to instal the drivers for my wireless network i type

ndiswrapper -i FILENAME.INF

Replacing FILENAME with the filename of the dirver obviously and it comes up with:

Installing FILENAME
Unable to create directory .../ndiswrpper/FILENAME please make sure that your account is root

Or words to that effect


Can someone please help?

---

### Post by meborc on 2006-04-03
try running the command like this:

**sudo ndiswrapper -i FILENAME.INF**

i have 0 exp with ndiswrapper, but it seems you just needed a sudo at the beginning... for more inf on sudo and root read - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by clareb on 2006-04-03
I'm no expert at this, but do you have 'windows wireless drivers' under System>Administration?

---

### Post by Papa-san on 2006-04-03
[QUOTE=clareb]I'm no expert at this, but do you have 'windows wireless drivers' under System>Administration?[/QUOTE]
This was added to mine after I ran Automatix and then added the 'ndisgtk' laptop wireless configuration tool...  

As a nOOb, I have found automatix very useful. Once you install it, which takes some time, go back in and select the packages you want to install. That should make your life easier!

(However with my Dell Laptop, I had wireless driver issues anyways, but most of that problem was due to the organic component of my computer... the one between the keyboard and the chair!)

---

### Post by shyopstv on 2006-04-03
After putting in the sudo command, I got a little tiny baby-step closer to installing the drivers. This time I got:

CP: Cannt stat "AEWLUBS2.INF" No such file or directory.

when i put in ndiswrapper-l it says that it is an invalid driver but I can't remove it because it says it hasn't been installed and I can't try installing it again because it says that it has been installed ](*,) I also have a folder in the ndiswrapper directory called "AEWLUBS2" that is empty and I cannot delete becasue apparantly I don't have permission :???: 

I don't have 'Windows Wireless Drivers' so I'll try that Automatix thing. The only problem is that I can't get onto the Internet using Ubuntu because of this problem

---

### Post by clareb on 2006-04-03
Someone can correct me if I'm wrong but if you don't have windows wireless drivers you've not installed ndisgtk, ndiswrapper-source and ndiswrapper-utils in the synaptic package manager, try going into that and seeing if they're installed (the box next to them will be filled in green). lemme know.

---

### Post by shyopstv on 2006-04-03
I have ndiswrapper-utils but the other two don't appear in Synaptic Package Manager. Is there anything else you need to download before you can install those?

---

### Post by darkwarrior0404 on 2006-04-03
I'm not really sure on most of whats going on, but when I've had problems with some things, I'm told that I do need to be root by typing sudo su


> darkwarrior0404@ubuntu:~$ sudo su
Password:
root@ubuntu:/home/darkwarrior0404#

> darkwarrior0404@ubuntu:~$ sudo su
Password:
root@ubuntu:/home/darkwarrior0404# passwd
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
root@ubuntu:/home/darkwarrior0404#


^^^ How to set your root password

> [http://www.ubuntuforums.org/archive/index.php/t-77211.html](http://www.ubuntuforums.org/archive/index.php/t-77211.html)

explains how to use root, but I'm not really sure what else it could be but from what I've read it doesnt automatically turn on root until you set psswd, well hope that little bit of info helped even if it dont with this maybe it'll help with a future problem of someones.

---

### Post by clareb on 2006-04-03
shyopstv - did you enable universe and multiverse in the repositories? You go into settings>repositories in the synaptic package manager, go through each entry, click 'add' and put ticks in the universe + multiverse boxes, tedious, but necessary. Then try and mark the other package for installation. Everything you need should be there.

---

### Post by shyopstv on 2006-04-03
I tried to that but it says "could not download all repositery indexes" which I assume is because I cannot connect tothe Internet using Ubuntu to download anything

*starting to get irritated with silly Internet connection*

---

### Post by clareb on 2006-04-03
Sorry, I was able to connect to the net with my ethernet connection when I was sorting my wireless, if there's no other way for you to connect in ubuntu then someone else will have to help you with how to download and transfer the right repositories from your other OS. I have read threads about that on the forum but fortunately I didn't have to do it myself. Don't give up though, if I managed to get wireless up and running anyone can. 
It might help you to know that when I first installed ubuntu, it took about a week to figure wireless out, but I did a totally fresh install of breezy yesterday (I mucked some stuff up that I won't go into here) and I managed to get wireless up and running in half an hour. It's a steep learning curve but you'll pick it up really fast, and everyone here's really helpful. Good luck.

---

### Post by shyopstv on 2006-04-03
Sorry to be annoying but I think I might be almost there! Either that or it is a complete dud and I am never going to get my network working with Ubuntu

I have installed the drivers for the network and have also got the two files clareb mentioned installed so now 'Windows Wireless Drivers' appears. When I go on that is shows my driver and says that the hardware is there however my USB adapter is still showing no signs of life and when I click on "configure network" the only options are dial-up and ethernet - no wireless and I can't figure out how to add a new one. Also the help file for this bit is useless - it seems to be using an older version of the netwroking tool which looks very different to what I am using

I am sitting near a window and am getting very annoyed at my computer now....

---

### Post by clareb on 2006-04-03
Hey again, this happened to me the first time I tried to get wireless working, I ended up using Linuxant's driverloader, I've no idea if that'll work for your bit of hardware, though. If you want to check it out, just google for it, it'll be easy to find.
Funny thing is, when I reinstalled ubuntu yesterday, I managed to get things working with ndiswrapper. If in doubt, I reboot - it's surprising what suddenly starts working after rebooting. I don't think I'm being much help, my advice is start a new thread with an update of what's going on, I posted loads of times, feel free to check.. Don't give up, you'll eventually get the help you need. And don't throw the computer out of the window, no matter how tempted you get, you'll regret it in the morning..:mrgreen:

---

### Post by carlosqueso on 2006-04-03
Try opening a terminal and typing ```
sudo modprobe ndiswrapper
``` I don't know if that'll work, but it's at the very least worth a try.

---

