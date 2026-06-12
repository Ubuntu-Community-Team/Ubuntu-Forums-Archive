---
title: "Ubuntu GUI"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by fouhay on 2006-08-17
Hi

never thought I'd have to ask a question that seems so simple. I've looked all over and cannot find a reference to it

How do start X11? :confused: 

Aptitude says it's installed, but server boots to CLI

tried these commands

x
xstart
x11
startx

and many other variations

Am I headed in the right direction?

Thanks in advance for any responses

---

### Post by Jagot on 2006-08-17
Did you install the server version of Ubuntu?

---

### Post by 23meg on 2006-08-17
*startx* should do it. But if you did a normal install and there's no GUI, your X is somehow misconfigured. Are you getting any errors when you type *startx*?

---

### Post by IYY on 2006-08-17
If your system doesn't automatically boot to the GUI, it is safe to assume that either you didn't install it (that's what a server install is) or something is wrong in the configuration. Usually, we launch the X server with

```
sudo gdm
```

This runs the login manager GDM.

---

### Post by David Corrales on 2006-08-17
If you installed a metapackage like ubuntu-desktop then it should be accesible via startx. You can also try running gdm.

---

### Post by fouhay on 2006-08-17
Sorry, should have mentioned that yes, it is a server install.

for 
sudo gdm and startx 

I just get "command not found".

This is what confuses me as X11 is installed and as far as I can tell from the posts I've read, this is all that is required.

previously tried

sudo apt-get install ubuntu-desktop,

but the message "Couldn't find package" was returned

there was a couple of errors for sudo apt-get update

---

### Post by bodhi.zazen on 2006-08-17
I'm a little rusty on a server install.

First consider starting with aptitude rather then apt-get.
apt-get install aptitude (if you do this change apt-get below to aptitude)
Next, is apt-get properly configured and repositories enabled? ubuntu-desktop should work.


If you just need X I think you need to install x server (not just x common)

(Assuming apt-get)

apt-get install xserver-xorg

Desktop install varies. For Gnome:
apt-get install ubuntu-desktop

KDE: apt-get install Kbuntu-desktop

Xfce: apt-get install xubuntu-desktop

---

### Post by smee56 on 2006-08-17
hi i do not know how to get my gui working 
i can get the command line and i try F8 &9 but my screen dies 
i have also tried startx etc. but nothing seems to work.
i am not connected to the internet with ubuntu so downloading is hopeless. 
please help if you have got yours working

---

### Post by unisol on 2006-08-17
assumming you have the desktop cdrom sudo apt-cdrom add, this will add cdrom as a repo sudo apt-get install linux-386 this will install the desktop kernel
sudo apt-get install ubuntu-desktop if it still dont work try sudo dpkg -phigh xserver-xorg good luck hope this will help you

---

### Post by aysiu on 2006-08-17
Actually, the Desktop CD won't help you, as its repositories do not contain all the packages needed for a desktop installation.

You would need the Alternate CD, in which case you'd do ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ubuntu-desktop linux-386
sudo /etc/init.d/gdm start
```

---

