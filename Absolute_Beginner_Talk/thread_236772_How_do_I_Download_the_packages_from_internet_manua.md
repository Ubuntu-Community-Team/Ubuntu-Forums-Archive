---
title: "How do I Download the packages from internet manually and install them?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by martinmanzana on 2006-08-15
I got a laptop with ubuntu server installed on it. This means I got no GUI. As far as I know the basic packages to set up a basic GUI are not in my computer. I installed ubuntu from a server iso (That was a bad idea) and I am lacking a lot of essential packages. Some of you will insist in updating repositories, but since I have no connection to internet from my laptop that's no use. The idea is to get the x-windows-system up and running with fluxbox, since my computer has low resoureces(64Mb of RAM) For this I have download the following packages from internet into my desktop computer:

[I]
xserver-xorg
xterm
fluxbox
[/I]

*What other packages should I download?* Someone said I may need a menu package and a display manager package. *Which should I download?*

Once I have all the need packages, I can save them on a floppy or a cd and mount them on my laptop. The question is:

*Where should I copy these packages, so that when I open aptitude it will find them and install them?*

---

### Post by cstudent on 2006-08-15
Assuming you are using Dapper, this may help you out:

[http://packages.ubuntu.com/dapper/x11/fluxbox](http://packages.ubuntu.com/dapper/x11/fluxbox)

---

### Post by martinmanzana on 2006-08-15
Thanks. Thats the location I download the packages I listed from. What I need to know now is how to install the packages from the tar balls. I am more interested in knowing how to how to build the xterm and xserver-xorg from the tar balls.

Thanks

---

### Post by cstudent on 2006-08-15
You can download the .deb files using wget:

```

wget http://archive.ubuntu.com/ubuntu/pool/universe/f/fluxbox/fluxbox_0.9.14-2_i386.deb

```

Then just install using sudo dpkg -i package_name.

---

### Post by givré on 2006-08-15
Bulding xserver-xorg from just a tarball will be a pain. And even with a .deb, you will have a lot of dependency problem.
I suggest you to simply install fluxbox with a simple:
```
sudo apt-get install fluxbox
```
If your sources.list is correct, then it will install fluxbox & all it dependency.

---

### Post by cstudent on 2006-08-15
> **givré said:**
> Bulding xserver-xorg from just a tarball will be a pain. And even with a .deb, you will have a lot of dependency problem.
I suggest you to simply install fluxbox with a simple:
```
sudo apt-get install fluxbox
```
If your sources.list is correct, then it will install fluxbox & all it dependency.

He said his laptop had no internet connection. He's trying to download from one computer and move the files to the laptop.

---

### Post by benuski on 2006-08-15
It may just be easier to burn an Ubuntu desktop cd from your computer that has the internet, and just use that to reinstall Ubuntu on your laptop, if thats possible.

---

### Post by givré on 2006-08-15
> **cstudent said:**
> He said his laptop had no internet connection. He's trying to download from one computer and move the files to the laptop.
Oh yeah, my bad :cool: 
So i think benuski advice is the best. You can't know how hard it could be to install a x-window system from scratch if you don't have the knowledge for.
Or you could download all deb package separatly by looking at the dependency for each package, and dependency for each dependency... For that [http://packages.ubuntu.com/](http://packages.ubuntu.com/) will be your friend. Good luck :grin:

---

### Post by aeiah on 2006-08-15
and to install .deb packages, you can either double click it (if you have that installer program that ive forgotten the name of) or you can navigate to where you downloaded it to within a terminal and do:

sudo dpkg -i filename.deb

---

### Post by givré on 2006-08-15
Better solution. Download the cdrom, and add the cd to your sources.list (there is a command for that, apt-cdrom i think) so you will be able to install x-window-system-core & all it dependency. But not yet fluxbox (since it's in universe <->not in the cdrom)

EDIT:no i think installing from a desktop CD is definitly the best solution. A server CD is nothing without an internet connection...

---

