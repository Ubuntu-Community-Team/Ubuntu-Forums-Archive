---
title: "Modules-assistant"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by Gnoobuntu on 2007-02-22
I'm trying to install the drivers for my ATI video card found [HERE]("http://www.ubuntuforums.org/showthread.php?t=329128&highlight=dma+buffer+ATI") and the instructions are telling me to use these commands to rebuild the kernel:

module-assistant prepare
module-assistant update
module-assistant build fglrx
module-assistant install fglrx

My computer is telling me that those commands are not found.

How do I go about installing them or getting them to work please?

---

### Post by carlosfocker on 2007-02-22
you might want to try this guide [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) but highly recommend Alberto Milone's guide [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Gnoobuntu on 2007-02-22
> **carlosfocker said:**
> you might want to try this guide [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) but highly recommend Alberto Milone's guide [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

Carlos,

Thanks for your reply, but that guide also has the same commands that my install of Ubuntu dosen't seem to recognise.

Steve

---

### Post by mahy on 2007-02-22
It means you have to install module-assistant first. ;) Like this:

sudo apt-get install module-assistant

Cheers!

---

### Post by annda on 2007-02-22
are you sure you installed module-assistant as mentioned in the guide? did you get any error messages? look in synaptic to see if it has been successfully installed.

if it has, maybe try to install it again.

---

### Post by carlosfocker on 2007-02-22
The first guide does specify to install module-assistant under method 2.  Why can you use Method 1 it much easier.  Also Alberto's guide is also much easier than method 2 in the first guide

---

### Post by Gnoobuntu on 2007-02-28
steve@Ubuntu610:~$ sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package module-assistant is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package module-assistant has no installation candidate
steve@Ubuntu610:~$ 


Still can't find the module-assistant

---

### Post by carlosfocker on 2007-02-28
Did you enable  "restricted" Repository?

To do this in GNOME, go to your System Menu > Administration > Software Sources. Place a check next to "Proprietary drivers for devices (restricted)," click Close, click Reload, and let the application update the package list.

If you use KDE, go to K > System > Adept Manager Manage Packages. Enter your password. Go to Adept > Manage Repositories. Right Click everything that starts with deb or deb-src and select enable. Select fetch updates and you are good to go!

---

### Post by nickoli_02 on 2007-02-28
> **carlosfocker said:**
> Did you enable  "restricted" Repository?

To do this in GNOME, go to your System Menu > Administration > Software Sources. Place a check next to "Proprietary drivers for devices (restricted)," click Close, click Reload, and let the application update the package list.

If you use KDE, go to K > System > Adept Manager Manage Packages. Enter your password. Go to Adept > Manage Repositories. Right Click everything that starts with deb or deb-src and select enable. Select fetch updates and you are good to go!

You can also just simply open a terminal and type:

```
sudo nano /etc/apt/sources.list
```

and remove the #'s in front of the lines with url's.

---

### Post by Gnoobuntu on 2007-03-01
Thanks kindly! That did the trick.

Gnoo....

---

