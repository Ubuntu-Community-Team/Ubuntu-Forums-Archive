---
title: "[SOLVED] Install .deb to a location"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-02-09
HI guys
I wanted to know how to install deb pakacges to a specific location install of the home directory. I looked thru the manual but cudnt find it..
I have a .deb file and i want to install it to /media/hda7 and not /home...How do i do it ? 
Thanks

---

### Post by daou on 2007-02-09
.deb files are compiled to install to a certain location. Installing it somewhere other than the predefined location is considered "bad practice." Yes, it's something you would do in Windows, but the first rule of using GNU/Linux OSs is to forget everything Windows taught you (not necessarily a bad thing). Usually, everything you install with a .deb package goes to your /usr folder. A couple config files and user specific files go to your home directory.

This is why partitioning is important. You want to give enough room for programs to go into the /usr folder. But this is hardly ever a problem. Where the standard size of Windows programs easily go into the gigabytes, a GNU/Linux program is a couple of megs.

---

### Post by aberry5555 on 2007-02-09
.deb files work natively in Ubuntu but not via double click (I'm not quite sure why this is as Ubuntu is based on debian but meh :p) 

In order to do this you type in the following code:

```
sudo dpkg -i ***package_file***.deb
```

Lemme break this down a bit for you; as you may or may not know, "sudo" is the superuser command you use to install anything or change any settings, so anything that could affect your system has to be done with "sudo".

"dpkg" is the command used for debian packages and "-i" means to install the package, if you want to uninstall use "-r". Finally, the bold and italic part is the part which you change, depending on the name of the file, though I think that's fairly obvious :p. 

Hope that helps.

***edit***

Woops, didn't read the question properly :S

---

### Post by daou on 2007-02-09
> .deb files work natively in Ubuntu but not via double click

They do work through double click. But when you do that, you get a different frontend to handle the package, instead of Synaptic.

---

### Post by aberry5555 on 2007-02-09
Oh ok, so does that front-end handle them properly? or is it better to do it through terminal

---

### Post by mcduck on 2007-02-09
> **aberry5555 said:**
> Oh ok, so does that front-end handle them properly? or is it better to do it through terminal
It's just a graphical front-end to dpkg, so there's no big differences. I think the GUI may be able to download dependencies from repositories, but I'm not sure about that. Then again, if you have many packages you have downloaded yourself that depend on each other you still need to use 'sudo dpkg -i package1.deb package2.deb' to get them installed at the same time. (or sudo  dpkg -i *.deb ;))

---

### Post by ashmew2 on 2007-02-09
lol guys , even if it is considered a bad practice , is there any possible way i can install it to somewhere other than the default folder ? for example i need to install win4linpro and i have its deb package. It installs to the home directory (where i have noly 1.3 GB left) but i want to provide it with 5 GB at least so it shud install to /media/hda7 , any ideas? 
Thanks

---

### Post by daou on 2007-02-09
If you know which directory it installs to, you could make a symbolic link there. For example, if the program installs to /home/foo you could try making a symbolic link (a directory) that actually takes you to /media/hd7

so in shell speak:

```
ln --symbolic /media/hd7 ~/foo
```

then, if the program doesn't remove it's destination directory before it installs, it will install itself to foo. But the symbolic link takes it to hd7.

Note: make the symbolic link _before_ you install.

---

