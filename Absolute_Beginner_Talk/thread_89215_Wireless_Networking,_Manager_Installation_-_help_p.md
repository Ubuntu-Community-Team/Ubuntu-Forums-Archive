---
title: "Wireless Networking, Manager Installation - help please!"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by kilps on 2005-11-12
Hi there - I just got my Shipit CDs and am trying to get Ubutu to talk to my Windows XP laptop via wireless. I enter the same (I think ....) network details on both machines but still get nowhere.

I thought of using a manager such as [_NetworkManager_]("http://www.gnome.org/projects/NetworkManager/") - but in my ignorance I cannot work out how to install it :oops: ... why can they not be one file like windows? :???: **EDIT: **oh - if anyone knows of a better manager please let me know ...

My eventual aim is to be able to share a dialup connection between the two computers (either one connected) - but for the moment I want to figure out the networking ....

I might install Ubuntu on the laptop some time - but ATM I need the programs on it, so the other computer is a dummy ....

Thanks in advance  :D

---

### Post by Manny C on 2005-11-12
All of the following presupposes that you have a live internet running on the computer with Ubuntu.

Ok...to install programs in Ubuntu, you need to issue a like directive. In particular, if you want to install the program "foo", you simply issue the following directive in "Terminal" or "Konsole":
```
 sudo apt-get install foo 
``` 
Alternatively, and more user friendly, is to install "synaptic" - a program that acts as a package manager. To do this:
```
 sudo apt-get install synaptic 
``` 
Once this is installed, simply select the program from the menu and search for whatever programs you need. A good list of what the linux equivalents are for popular windows programs can be found [here]("http://www.ubuntuforums.org/showthread.php?t=33183").

_**EDIT:**_ To answer your question:
```
 sudo apt-get install network-manager
```

---

### Post by kilps on 2005-11-12
[QUOTE=Manny C]All of the following presupposes that you have a live internet running on the computer with Ubuntu.

Ok...to install programs in Ubuntu, you need to issue a like directive. In particular, if you want to install the program "foo", you simply issue the following directive in "Terminal" or "Konsole":
```
 sudo apt-get install foo 
``` 
Alternatively, and more user friendly, is to install "synaptic" - a program that acts as a package manager. To do this:
```
 sudo apt-get install synaptic 
``` 
Once this is installed, simply select the program from the menu and search for whatever programs you need. A good list of what the linux equivalents are for popular windows programs can be found [here]("http://www.ubuntuforums.org/showthread.php?t=33183").

_**EDIT:**_ To answer your question:
```
 sudo apt-get install network-manager
```[/QUOTE]
Thanks - I'll have to set up the dailup connection then ... I just hope I can get the winmodem to work - but I'll see how it goes ;)

---

