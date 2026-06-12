---
title: "Stata installation"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2006-08-08
I am not sure this is the correct forum for this but I need some help with STATA 9 (a statistical package) installation.

I am trying to install Intercooled Stata 9 on a Dell Inspiron E1405. My OS is Linux (Ubuntu 6.06). I follow the instructions but get stuck in the very first step. 

The instruction says that I must be logged in as the root to install the package. Since I have not created a root user account, I use "sudo su -" at the terminal prompt to use the machine with root privileges for the current session.

Then the installation procedure asks me to create a directory; so I type "mkdir /usr/local/stata" to create the directory.

Then I plunk the Stata 9 CD into the cdrom drive.

Then I check that the path to the cdrom on my machine is "/cdrom" and not "/mnt/cdrom" as is usually the case.

So I type "/cdrom/install" to run the installation script on the CD and get stumped! I get the following message:
```
-su: /cdrom/install: Permission denied

```

Am I missing some simple step somewhere? Do I need to change permissions somewhere? 
Any help will be greatly appreciated.

---

### Post by Cone on 2006-08-16
Hm.  I dunno.
Try "sudo /cdrom/install" maybe, or
"$ cd /cdrom/
 $ sudo ./install".

Generally (as far as I've learned) it's best to use sudo on the individual commands rather than running the whole session as root, plus it'll only ask you for the password for the first command if you don't take a huge amount of time to do the tasks in the terminal, so it's not that inconvenient either.

Hope this helps,
~Cone

---

### Post by stormoog on 2007-08-14
The manual recommends copying the whole cd to a temporary directory and installing it from there.


I solved all my other problems as well after following these guidelines:
[http://www.stata.com/statalist/archive/2007-07/msg00116.html](http://www.stata.com/statalist/archive/2007-07/msg00116.html)

---

### Post by trorion on 2007-09-28
unmount your CD and re-mount it so that you can use it properly.

1- find your cd mount point by ```
mount
```
mine is a usb drive so I find ```
/dev/scd0 on /media/cdrom0
``` (the cdrom0 tells me it's my cdrom, yours will probably say /dev/cdrom# on /media/cdrom#)
2- I do 
```
sudo umount /dev/scd0
sudo mount -o exec -t iso9660 /dev/scd0 /media/cdrom0       note: (mounts the cdrom so that you can properly read it; you will probably do /dev/cdrom instead of /dev/scd0)
sudo /media/cdrom0/install
```

Unfortunately their "windows" license seems to not work on my linux box.  hate that.

---

