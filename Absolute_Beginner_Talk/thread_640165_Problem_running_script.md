---
title: "Problem running script"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Lotekx on 2007-12-13
Hi,
I am trying to make a bootable usb drive out of the gparted iso file using the set_usb.sh script.  
Here are the very basic instructions i'm following: [http://gparted-livecd.tuxfamily.org/index.php]("http://gparted-livecd.tuxfamily.org/index.php")


However, I am getting some strange errors. Check it:


```
brent@brent-laptop:~$ sudo /home/brent/Desktop/set_usb.sh 
[sudo] password for brent:
[: 16: /tmp/gparted: unexpected operator























$

 ----------------------------------------------------------------------
$                This script is to be run to copy files from GParted-livecd ISO file to usb stick. Run this script from the directory where you downloaded the GParted-livecd ISO file. I assume you have a usb stick formatted as FAT (or FAT32), with at least 55 MO free. You are now going to be asked the path where your usb stick is mounted.
-----------------------------------------------------------------------$

/home/brent/Desktop/set_usb.sh: 27: function: not found
-en 
```





What gives? What am I doing wrong?

Thanks!

---

### Post by yabbadabbadont on 2007-12-13
The default shell since Feisty is Dash.  Dash breaks a lot of scripts.  You can either try switching your default shell to Bash, or edit the script so that it explicitly uses Bash.  I would do the second one first to see if it helps.  To do this change the first line of the script from:
```
#!/bin/sh
```
To:
```
#!/bin/bash
```

If that fixes it, and you intend to run a lot of scripts that you download, then you might want to change your default shell.  To do that you would run:
```
sudo dpkg-reconfigure dash
```
Answer "No" when asked if dash should be the default shell.  Then logout and back in.

---

