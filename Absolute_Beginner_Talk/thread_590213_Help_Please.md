---
title: "Help Please"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by minacross on 2007-10-24
I know it's stuped, but after I installed ubuntu 7.10 I can't get to it's GUI. Only the startup screen with a prompt after this line:
root@mina-desktop:~#
would you help me please :(

---

### Post by Dr Small on 2007-10-24
If you do not have to login, then it looks like it is booting in recovery mode...
Strange.

---

### Post by overdrank on 2007-10-24
> **minacross said:**
> I know it's stuped, but after I installed ubuntu 7.10 I can't get to it's GUI. Only the startup screen with a prompt after this line:
root@mina-desktop:~#
would you help me please :(

HI and try the command ```
startx 
``` and see if you get any errors.

---

### Post by jonathanmotes on 2007-10-24
> If you do not have to login, then it looks like it is booting in recovery mode...
Strange.

Yes, you are in recovery mode, because the "#" indicates that you are running as root (which is only allowed in recovery mode by default). You probably accidentally selected the wrong option in the grub menu that comes up when you first boot your computer. If this is the case, it is best to not run the GUI with "startx" because root gives you privileges to accidentally mess things up! (just enter the command below and select the first menu item in the grub menu after it reboots).```
reboot
```

---

### Post by minacross on 2007-10-25
it works :) How? :confused::lolflag:
so, which one of these will work on Ubuntu 7.10? 
avast! Linux Home Edition (RPM package)
avast! Linux Home Edition (DEB package)
avast! Linux Home Edition (TAR GZ package)

Edit: And how to install it? :oops:

---

### Post by Anicka on 2007-10-25
> **minacross said:**
> it works :) How? :confused::lolflag:
so, which one of these will work on Ubuntu 7.10? 
avast! Linux Home Edition (RPM package)
avast! Linux Home Edition (DEB package)
avast! Linux Home Edition (TAR GZ package)

Edit: And how to install it? :oops:

.deb works in Ubuntu. Download it and either type in the terminal "sudo dpkg -i name_of_package" or double click on it from nautilus.

---

### Post by slibuntu on 2007-10-25
> **minacross said:**
> it works :) How? :confused::lolflag:
so, which one of these will work on Ubuntu 7.10? 
avast! Linux Home Edition (RPM package)
avast! Linux Home Edition (DEB package)
avast! Linux Home Edition (TAR GZ package)

Edit: And how to install it? :oops:

On a side note, and at the risk of starting a debate, you don't really need an anti-virus program unless you are interfacing on a network with Windows PC's, since none but 2 or 3 of all the computer viruses ever created will affect Linux users. But if you just want to be uber safe, fire ahead! :)

---

### Post by minacross on 2007-10-25
I keep receiving this error:
mina@mina-desktop:~$ sudo dpkg -i desktop/avast.deb
dpkg: error processing desktop/avast.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 desktop/avast.deb

---

### Post by slibuntu on 2007-10-25
You don't have to do it thru a command line, if you double click the icon the debian unpackager will do the hard part for you!

---

### Post by Duck2006 on 2007-10-25
> **jonathanmotes said:**
> Yes, you are in recovery mode, because the "#" indicates that you are running as root (which is only allowed in recovery mode by default). You probably accidentally selected the wrong option in the grub menu that comes up when you first boot your computer. If this is the case, it is best to not run the GUI with "startx" because root gives you privileges to accidentally mess things up! (just enter the command below and select the first menu item in the grub menu after it reboots).```
reboot
```

sudo reboot

---

### Post by slibuntu on 2007-10-25
> **Duck2006 said:**
> sudo reboot

Why would he need sudo given he's logged in as root already?!

---

### Post by Duck2006 on 2007-10-25
He may be logged in as root but you still have to sudo reboot to reboot.

---

### Post by Shazaam on 2007-10-25
> **Duck2006 said:**
> He may be logged in as root but you still have to sudo reboot to reboot.

At the root promt you don't need sudo, just enter reboot. Works every time for me. :)
I don't have any special root privleges set up, just default Ubuntu.

---

