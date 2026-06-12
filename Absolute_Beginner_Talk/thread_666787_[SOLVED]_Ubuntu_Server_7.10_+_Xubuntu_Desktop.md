---
title: "[SOLVED] Ubuntu Server 7.10 + Xubuntu Desktop"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by dmhtong on 2008-01-13
I installed Ubuntu Server 7.10 with the Xubuntu  Desktop software selection package. When I start up Ubuntu, I am taken to the login prompt in the shell environment. Once I login, how do I:
1. check if Xubuntu is installed, or any of the other software selection packages I chose?
2. start the Xubuntu desktop environment?

Sorry for the noob question.  :confused:

---

### Post by JoshuaRL on 2008-01-13
Alright try this:

```

sudo apt-cache search xubuntu-desktop

```

That should see if you have that installed on your system.  If you do, try this to start it:

```

startx

```

And if either it isn't installed, startx doesn't work, or you just want to be sure, try:

```

sudo apt-get install xubuntu-server

```

That's a metapackage that will download and install all the other packages you need to make the ubuntu xfce work.  Hope that helps!

---

### Post by dmhtong on 2008-01-13
Josh, thanks for your prompt response.

```
Typed: sudo apt-cache search xubuntu-desktop
Returned: xubuntu-desktop - Xubuntu desktop system
```

```
Typed: startx
Returned: The program 'startx' is currently not installed. You can install it by typing: sudo apt-get install xinit

```

Quetion: why is this component not installed? Did I miss a software selection package during my Ubuntu Server install procedure?

```
Typed: sudo apt-get install xubuntu-server
Returned:
reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package xubuntu-server
```

```
Typed: sudo apt-get install xinit
Returned:
Attempted install with fails
FATAL: Error inserting battery (/lib/modules/2.6.22.14-14-generic/kernel/drivers/acpi/battery.ko): No such device
...
...
```

```
Typed: startx
Returned:
xauth: creating new authority file /home/dtong/.serverauth.4033
xauth: creating new authority file /home/dtong/.Xauthority
xauth: creating new authority file /home/dtong/.Xauthority
X: cannot stat /etc/X11/X (No such file or directory), aborting.
xinit: Server error

```

Any other suggestions?

Additional information:
System - MacBook Pro 2.16Ghz Intel Core 2 Duo 3 GB 667 MHz DDR2 SDRAM Mac OS X Version 10.4.11
Ubuntu installed on Parallels Desktop for Mac Build 3214 (21 June 2007)
- OS Type: Solaris
- OS Version: SOlaris 10 (apparently this was the required config for Ubuntu to detect the CD drive in Parallels
- RAM allocation: 512MB
- 3 partitions: / (root - 10GB) and /home (15GB) and swap area (256MB)

Ubuntu information:
- Selected software packages installed: LAMP, DNS Server, Mail Server, Open SSH Server, PostGres SQL DB, Print Server, SAMBA file server, Xubuntu desktop
- Before restarting after OS install, opened shell in installer environment and typed the following commands in order to get around the error message "PANIC: CPU too old for this kernel":
```
unmount /dev/scd0
chroot /target /bin/bash
mount /dev/scd0 /media/cdrom
aptitude install linux-generic
aptitude remove linux-server linux-image-server linux-image-2.6.22-14-server
exit
shutdown -h now

```

Thanks in advance.

---

### Post by JoshuaRL on 2008-01-13
Dude I'm such a dork.  Try this:

```

sudo apt-get install xubuntu-desktop

```

Yeah, there is no such package named "xubuntu-server."  I typed wrong, sorry.  See if that works.

---

### Post by dmhtong on 2008-01-13
Josh, that worked great!

One final question though. During my Ubuntu install where I selected the Xubuntu Desktop software package, how come that didn't install the Xubuntu Desktop package? Will this be a similar case for LAMP, the mail server and my other selected software packages I chose during the Ubuntu install - will I have to manually install them again?

Thanks in advance:)

---

### Post by JoshuaRL on 2008-01-13
No I don't think so.  When you install a server system it is headless, IE no GUI.  So any programs should be there and accessable if I understand it right.  It makes for a ridiculously quick system if you're running a server from the CLI, and still a fast system if you run a desktop.  So it starts okay?

---

### Post by dmhtong on 2008-01-13
Josh, yes, it starts fine.

But I still don't understand why the install was "headless" even though I in the server installation I chose the "Xubuntu Desktop" option to be installed under the "Select Software" section?

---

### Post by JoshuaRL on 2008-01-13
Not sure, I haven't actually installed any server systems.  But I think that's what differeniates the server version from the regular one.  That allows you to decide what kind of or if you even want a GUI.

Thanks for all the thanks man!  You're cool.

---

