---
title: "Ubuntu crashes after fglrx is installed"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by futron on 2007-02-25
Help, I installed fglrx on 6.10 ubuntu, and after I rebooted the system, a screen with menus composed of ASCII characters informed me that the windows system had failed, after which the bash shell shows up. How can I revert to the opensource ati drivers without reinstalling everything? HELP

---

### Post by NT4usB on 2007-02-25
ed: first off, you can try this from the shell:
```
sudo dpkg-reconfigure xserver-xorg
```
and maybe change the driver from there... I haven't done it in a while so I don't recall the steps.


you can edit xorg.conf and change the driver from 'fglrx' or whetever to vesa. then x should start and enable you to fix it.

login to the shell.
type:
```
cd /etc/X11/ 
```(note the capital 'X')
type:
```
sudo vi xorg.conf
```
arrow down to the "Device" section. Look for the Driver line
arrow over to the first letter of the word in the Driver line in quotes: "**_f_**glrx"
type **x** to delete the letters
type **i** (to insert.) 
type: vesa (should be between the quotes)
hit escape to cancel command
type:
```
:wq
``` to save and close
type:
```
sudo /etc/init.d/gdm restart
```
and it should restart with the vesa driver.
ed: You can try using radeon or ati as the driver to see if maybe it will start with those but vesa is for sure....

ymmv.

---

### Post by kittyhawk63 on 2007-02-25
You can go here and re-install ATI driver. Follow the simple instructions. You can also click on the included link to take you to a web page for further options.

[http://www.ubuntuforums.org/showthread.php?t=370556](http://www.ubuntuforums.org/showthread.php?t=370556)    :)

---

