---
title: "Take me by the hand PLEASE, installing a Program!"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by poloman2 on 2005-11-20
Hello,
I just gave up trying to install inkscape, 
this is what i did...
first i downloaded the package from debian.org, it has .deb extention. Then I copied into /home/user/Desktop/ . the file  had a long ass name so i changed to simply inscape.deb. then I openend the application to intall programs (package manager) and follow the instrucctions in the help menu ( reload and all that stuff), but still cant get it to install....

Can any body give a hand with this??? i know that all I need is ONE successfull installation to do the rest on my own...

Thanks in advance,

---

### Post by nsa_767 on 2005-11-20
Use Synaptic and search for inkscape, it is in there.

I'm not using Gnome so I can't tell where in the menus it is. You can always open up a terminal and type in:

*sudo synaptic*

It will ask you for your password, type it in and you should be OK.

---

### Post by Brunellus on 2005-11-20
System>Administration>Synaptic Package Manager

First, enable the universe and multiverse repositories in synaptic according to these directions:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)

when you've finished that hit refresh.  New package lists will be downloaded.

Then, search for inkscape.

Mark it to be installed, hit apply.  Synaptic/apt will take care of all your dependencies for you.

Enjoy inkscape.  It's a lot of fun; I've been playing with it a bit lately.

---

### Post by nsa_767 on 2005-11-20
Just for future reference, Synaptic/Apt-get is your first option for installing apps. If you want something, first check if it isn't in Synaptic.

If not, then try getting a .deb off of the net and using 

*dpkg -i packagename.deb*

But be careful, it is not advisable to install non-ubuntu packages.

---

### Post by aysiu on 2005-11-20
If you want a more in-depth explanation of installing software in Ubuntu, go [here](http://www.psychocats.net/linux/installingsoftware.php)

---

