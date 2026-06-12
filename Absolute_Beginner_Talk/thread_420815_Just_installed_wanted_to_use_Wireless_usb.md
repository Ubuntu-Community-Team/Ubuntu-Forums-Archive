---
title: "Just installed wanted to use Wireless usb"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by tyner100 on 2007-04-24
Ive looked around and found this 

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)


i want to use a dlink  WUA-2340


i am a complete ubuntu NOVICE:confused: 

please talk to me like im 4.

I beg you.

=)


thanks,
    Tyner

---

### Post by tyner100 on 2007-04-24
dingle

---

### Post by Bachstelze on 2007-04-24
Plug your adapter in, open a terminal, type

```
lsusb
```

and paste what you get.

---

### Post by tyner100 on 2007-04-24
Bus 006 Device 002: ID 07d1:3a08 D-Link System 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 05dc:a576 Lexar Media, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0a5c:2120 Broadcom Corp. 
Bus 004 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Bachstelze on 2007-04-24
Hmm, this adapted does not appear in the list of devices known to work in the ndiswrapper Wiji. Try using ndiswrapper with the drivers provided on the CD of your card and see if that works.

---

### Post by tyner100 on 2007-04-24
not sure if it makes a difference, but its a usb receiver not a card.:)


[http://support.dlink.com/products/view.asp?productid=WUA%2D2340](http://support.dlink.com/products/view.asp?productid=WUA%2D2340)

---

### Post by Bachstelze on 2007-04-24
Nope, that doesn't make a difference, just install the Windows drivers using ndiswrappe.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by sunexplodes on 2007-04-24
Grab the newest driver from here: [http://support.dlink.com/products/view.asp?productid=WUA-2340](http://support.dlink.com/products/view.asp?productid=WUA-2340) , unzip it and it should have a folder called DRIVERS in it, which will contain NetA5AGU.inf among other files. move the driver folder to your desktop and then open a terminal, and "cd /home/YOU/Drivers"

then, follow these instructions:
```
apt-get install ndiswrapper-common ndiswrapper-utils-1.9
ndiswrapper -i NetA5AGU.inf
ndisrapper -l
```

Now, if it says "Driver present, device present" or some variation of that, head to the next step. If it says that but has a devid (07d1:3a08) in the string, skip the next step.

```
ndiswrapper -d 07d1:3a08 neta5agu
```

Almost done.

```
ndiswrapper -m
modprobe ndiswrapper
gedit /etc/modules
```

Just add the word ndiswrapper at the bottom of this file, save and close it, then reboot. Your device SHOULD work now, although I have a similar USB device that runs on the NetA5AGU driver, and I have to unplug it during boot, and plug it back in after logging on, in Feisty.

---

### Post by tyner100 on 2007-04-24
> tyner@tyner-desktop:~$ apt-get install ndiswrapper-common ndiswrapper-utils-1.9
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tyner@tyner-desktop:~$ 
tyner@tyner-desktop:~$ ndiswrapper -i NetA5AGU.inf
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found
tyner@tyner-desktop:~$ 
tyner@tyner-desktop:~$ ndisrapper -lsudo apt-get install ndiswrapper-common
bash: ndisrapper: command not found
tyner@tyner-desktop:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
tyner@tyner-desktop:~$ 




have any idea?

---

### Post by tyner100 on 2007-04-24
dingle >.>

---

### Post by tyner100 on 2007-04-24
im in need folks >.> help me out.

i dont seem to have ndiswrapper, and cant figure out the install for the life of me, i planed on showing my friends this sweet operating system, but cant figure it out for the life of me >.<  


HELP ME  


XD


tyner

---

### Post by Bachstelze on 2007-04-24
Which Ubuntu are you running ?

---

### Post by sunexplodes on 2007-04-24
weird that it isn't in your repositories.

install these deb files:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.38-1ubuntu1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.38-1ubuntu1_all.deb)

---

### Post by tyner100 on 2007-04-24
Installed, 

> 
tyner@tyner-desktop:~$ /home/tyner/Desktop/Drivers
bash: /home/tyner/Desktop/Drivers: is a directory
tyner@tyner-desktop:~$ apt-get install ndiswrapper-common ndiswrapper-utils-1.9
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tyner@tyner-desktop:~$ ndiswrapper -i NetA5AGU.inf
couldn't create /etc/ndiswrapper/neta5agu: Permission denied at /usr/sbin/ndiswrapper-1.9 line 146.
tyner@tyner-desktop:~$ ndisrapper -l

meh. meh. meh.

<3 thanks for helping

hope to hear back soon

---

### Post by tyner100 on 2007-04-24
Wah >.> i keep getting errors, can some one remote into mine and see what the hell I'm doing wrong?

---

### Post by tyner100 on 2007-04-24
Someone please respond >.<

---

### Post by tyner100 on 2007-04-24
anyone up for helping?

---

### Post by sunexplodes on 2007-04-25
Sorry, I should have mentioned it in my earlier instructions, you need to use Sudo to set up NDISWrapper.

---

### Post by sunexplodes on 2007-04-25
Oh, and you can ignore the apt-get instructions that i mentioned in an earlier post, as you used the deb files to install it instead.

---

### Post by tyner100 on 2007-04-25
Would you mind trying to make it a little more simple.

i really know nothing about this, and i am so lost.

if not i'll just stick with a wired connection.


KTHXBYE

tyner

---

### Post by Bachstelze on 2007-04-25
I can remote into yours to do it if you want, PM me about it :)

---

### Post by Bachstelze on 2007-04-25
Just to let everyone (and Google) know, the adapter with USB-id 07d1:3a08 was successfully installed with ndiwswrapper using the NetA5AGU.inf drive downloadable from [here](http://support.dlink.com/products/view.asp?productid=WUA%2D2340).

---

### Post by sunexplodes on 2007-04-25
follow these instructions:
```

cd /path/to/NetA5AGU
ndiswrapper -i NetA5AGU.inf
ndisrapper -l
```

Now, if it says "Driver present, device present" or some variation of that, head to the next step. If it says that but has a devid (07d1:3a08) in the string, skip the next step.

```
ndiswrapper -d 07d1:3a08 neta5agu
```

Almost done.

```
ndiswrapper -m
modprobe ndiswrapper
gedit /etc/modules
```

Just add the word ndiswrapper at the bottom of this file, save and close it, then reboot. Your device SHOULD work now, although I have a similar USB device that runs on the NetA5AGU driver, and I have to unplug it during boot, and plug it back in after logging on, in Feisty.

---

