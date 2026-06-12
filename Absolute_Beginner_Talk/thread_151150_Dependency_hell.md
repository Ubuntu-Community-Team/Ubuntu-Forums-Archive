---
title: "Dependency hell"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-03-27
In order to add new features to my Ubuntu, certain events force me to download the packages manually from packages.ubuntu.com. So if I want to install, let's say, Scorched3D game, I go to [http://packages.ubuntu.com/breezy/allpackages](http://packages.ubuntu.com/breezy/allpackages) and find the scorched3d package. However, there are 13 other packages that I need to have in order to properly run scorched3d. Kind of frustrating. Now **how do I know if and what packages are installed on my system or not?**

[SIZE="1"]<thought>Maybe someone could add labels to packages, such as :"This package is installed by default in the default installation of Ubuntu 5.10" or "This package is NOT installed by default in the default installation of Ubuntu 5.10". This could be of great help for many users in my situation.</thought>[/SIZE]

---

### Post by Brunellus on 2006-03-27
what are "certain events,"?  Do you not have any internet connectivity?  Have you not enabled the universe and multiverse repositories in apt?

---

### Post by meborc on 2006-03-27
go to synaptic package manager (from the menu) and search for them... if there is a green box infront of the pack, it is installed...

---

### Post by invalid on 2006-03-27
I am not sure why you have to manually download the files, unless you are trying to install a .deb which is not in the repositories. In any case, I would suggest using a package manager to install files.```
apt-get
```which is also available with a graphical frontend such as Synaptic.

To see a list of currently installed debian packages, type```
dpkg -l
```

---

### Post by meborc on 2006-03-27
i guess you didn't understand... he CAN'T, for some reason or another, use apt-get... it's perfectly OK...

---

### Post by zugu on 2006-03-27
Machine #1: home PC; runs Ubuntu; has no internet access
Machine #2: work PC; runs WinXP; has internet access
USB drive #1: server as a media for transferring files between the machines.

I want to use the work PC to download the files, the USB drive to transfer them, and the home PC to install them, of course :)

So by using Synaptic I can see what is installed and what is not.

Assuming I that some packages required by another one are not installed, in what order will I install those packages? Because I think that randomly installing them will mess up the OS.

---

### Post by AndrewCaul on 2006-03-27
[QUOTE=zugu]Assuming I that some packages required by another one are not installed, in what order will I install those packages? Because I think that randomly installing them will mess up the OS.[/QUOTE]
I think APT installs the dependencies first, and then the packages that depend on those. I hope that makes a bit of sense. :-? 

So you should try installing the packages with no uninstalled dependencies first. I know you can use Synaptic to view the dependencies for packages, but I'm not sure how to use the terminal to do it.

---

### Post by Sirin on 2006-03-27
[QUOTE=meborc]i guess you didn't understand... he CAN'T, for some reason or another, use apt-get... it's perfectly OK...[/QUOTE]

Heh, even if he could, he would'nt be able to play it anyway. Scorched3D's admins ended the support for the version that Ubuntu Breezy is using. They have a new version out now. ;)

---

