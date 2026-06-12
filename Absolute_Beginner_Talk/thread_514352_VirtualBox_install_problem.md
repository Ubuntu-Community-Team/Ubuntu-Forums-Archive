---
title: "VirtualBox install problem"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by jamieh on 2007-07-31
I am at the part here I have to accept the license agreement, but how do I accept it? Clicking OK and pressing Enter does nothing.

---

### Post by wormser on 2007-07-31
I have never installed it, but if it is in a shell you will have to use the keyboard.  Try pressing tab to highlight the ok button then press enter.

---

### Post by aysiu on 2007-07-31
Use the mouse to click inside the terminal window and then press Tab to navigate and Enter to select.

---

### Post by jamieh on 2007-07-31
Okay, I am past the EULA screen, now I get another error, here is my Terminal session:

--------------------------------------------------------------------------
ubuntu@ubuntu:~$ cd /ubuntu/Desktop 
bash: cd: /ubuntu/Desktop: No such file or directory 
ubuntu@ubuntu:~$ cd /home/ubuntu/Desktop 
ubuntu@ubuntu:~/Desktop$ sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb 
Selecting previously deselected package virtualbox. 
(Reading database ... 91545 files and directories currently installed.) 
Unpacking virtualbox (from virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb) ... 
dpkg: dependency problems prevent configuration of virtualbox: 
 virtualbox depends on libqt3-mt (>= 3:3.3.8really3.3.7); however: 
  Package libqt3-mt is not installed. 
 virtualbox depends on libxalan110; however: 
  Package libxalan110 is not installed. 
 virtualbox depends on libxerces27; however: 
  Package libxerces27 is not installed. 
dpkg: error processing virtualbox (--install): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 virtualbox 
ubuntu@ubuntu:~/Desktop$
-----------------------------------------------------------------------------------------

---

### Post by aysiu on 2007-07-31
Try ```
sudo apt-get -f install
``` right afterwards.

---

### Post by jamieh on 2007-07-31
The PC I am installing this to has no internet connection.

---

### Post by aysiu on 2007-07-31
> **jamieh said:**
> The PC I am installing this to has no internet connection.
Then download them from the Ubuntu Packages website:
[http://packages.ubuntu.com/feisty/libs/libqt3-mt](http://packages.ubuntu.com/feisty/libs/libqt3-mt)
[http://packages.ubuntu.com/feisty/libs/libxalan110](http://packages.ubuntu.com/feisty/libs/libxalan110)
[http://packages.ubuntu.com/feisty/libs/libxerces27](http://packages.ubuntu.com/feisty/libs/libxerces27)

Copy those .deb files to the desktop of the non-connected computer and type ```
cd ~/Desktop
sudo dpkg -i *.deb
``` Then do ```
sudo apt-get -f install
```

---

### Post by jamieh on 2007-07-31
New problem: It just won't start.
I get this message:

Callee RC:                0x80040154

---

