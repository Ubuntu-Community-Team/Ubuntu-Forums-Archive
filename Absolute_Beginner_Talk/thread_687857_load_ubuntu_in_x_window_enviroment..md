---
title: "load ubuntu in x window enviroment."
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ubuhan on 2008-02-04
How can I load x window under UBUNTU server platform?

---

### Post by taurus on 2008-02-04
Server has no X.  Therefore, you first need to install it before you can use it.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Blutack on 2008-02-04
Earlier answer was better.

---

### Post by ubuhan on 2008-02-04
I tried these command but does not work...
Hope someone can give me clear direction with each step.

Error message said " Couldn't find package ubuntu-desktop"

---

### Post by emarkd on 2008-02-04
"does not work" is a bit vague.  Can you post the error message(s) so we've got a direction to go?

---

### Post by Dr Small on 2008-02-04
If you only want Xorg (which sounds sensible to me, considering you are on a server) run this:
```
sudo apt-get install xorg
```

---

### Post by ubuhan on 2008-02-05
run this command "sudo apt-get install xorg"

here is the result from screeen>

Reading package lists....Done
Building dependency tree
Reading state information.. Done
E: Counldn't find package xorg.


Is my path search wrong? if so, how can I change it?

Thanks..

---

### Post by Nythain on 2008-02-05
you need to enable all the repos in your /etc/apt/sources.list
```

sudo nano /etc/apt/sources.list

```
remove the # from all the lines starting with deb and src
then
control + x to exit, y to save, enter to save as sources.list
then
```

sudo apt-get update
sudo aptitude install <package name>

```

---

### Post by ubuhan on 2008-02-05
The source list have command that need my PC to be connect to internet.  Right now, my PC network is not config and not connect to internet.  I want to update from my CD-rom and install package from CD-rom.

Thanks for you reply, I was able to understand the issue more and more.

---

### Post by maybeway36 on 2008-02-05
I do'nt knowif X11 is on the server CD. If you put in the Ubuntu, Kubuntu, or Xubuntu CD and do
```
sudo apt-cdrom add
```
you can install it from there.

---

### Post by aysiu on 2008-02-05
> **ubuhan said:**
> The source list have command that need my PC to be connect to internet.  Right now, my PC network is not config and not connect to internet.  I want to update from my CD-rom and install package from CD-rom.

Thanks for you reply, I was able to understand the issue more and more.
The CD you'll need will be an Alternate CD (**not** a Desktop CD): ```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by ubuhan on 2008-02-05
"I don't know if x window is on the server version" 
I don't know too. but when I use Aptitude to install x window package.
it show that x window package was install.

However, when I startx at command line : here is error messages:

xauth: creating new authority file /home/han/.serverauth.6698
xauth: /home/han/.Xauthority not writeable, change will be ignored
xauth: error in locking authority file /home/han/.Xauthority
xauth: error....save as above
xauth: error... save text as above
X: cannot stat /etc/x11/x ( No such file or directory), aborting.
xinit: Server error.
xauth:  error in locking authority file /home/han/.Xauthority

Thanks,

Han

---

### Post by aysiu on 2008-02-05
X is not on the server version.

---

