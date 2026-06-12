---
title: "Broken"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by RobyX on 2006-04-25
I was pretty excited that I've finnaly figured out how to install packages, until this

[IMG]http://img92.imageshack.us/img92/5904/screenshot5qf.png[/IMG]

The exact command I've used to install this (My file was located on the desktop and I renamed it to "amsn.deb")

```
roby@Roby:~$ cd ~/Desktop
roby@Roby:~/Desktop$ sudo dpkg -i amsn.deb
Password:
Selecting previously deselected package amsn.
(Reading database ... 73291 files and directories currently installed.)
Unpacking amsn (from amsn.deb) ...
dpkg: dependency problems prevent configuration of amsn:
 amsn depends on tcltls; however:
  Package tcltls is not installed.
dpkg: error processing amsn (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 amsn

```

This .deb was downloaded from the official website for aMSN.

---

### Post by mjm115 on 2006-04-25
aMSN is in the universe repository.  If you enable it in Synaptic, you should be able to install it along with all dependencies.

---

### Post by RobyX on 2006-04-25
I dont know what you mean. I just started using linux last night ](*,)

---

### Post by jazzmuzik on 2006-04-25
The repositories are the list of places from which you download program files, generally .deb files, which are the program packages.

Run Synaptic (System, Administration, Synaptic)

Select Settings, Repositories and enable the repositories with the word "universe". Then press Reload and information about the enabled repositores will be downloaded. Now look for amsn in the list and try and install it.

---

### Post by catlett on 2006-04-25
[https://wiki.kubuntu.org/AddingRepositoriesHowto](https://wiki.kubuntu.org/AddingRepositoriesHowto)
Follow this link and follow the Ubuntu version. 
What he means is there are repositories with software in them. The universe repository is not available but you can enable Synaptic to retrieve from there. 
Once you follow the guide you need to update ```
sudo apt-get update 
```then you can run the earlier command and synaptic will get the amsn package from the universe repository.

---

### Post by RobyX on 2006-04-25
Nevermind I used this 

[https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3368cdad8c270beda46be0c003e12550637b8203](https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3368cdad8c270beda46be0c003e12550637b8203)

And then went package>force version 
on the "amsn" and it wasent broken anymore.

Edit: Thanks for the help this is my first program I installed in linux now.

---

### Post by catlett on 2006-04-25
You should still be excited. Up and running installs in one night, figuring out a problem in 30 minutes..You're on your way.=D>

---

