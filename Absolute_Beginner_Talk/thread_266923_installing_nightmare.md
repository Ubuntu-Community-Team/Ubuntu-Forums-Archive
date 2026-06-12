---
title: "installing nightmare"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-27
i downloaded the flash player plugin.
the extraction utility said i dont have privilage to install to /
is this because im using oem? default?
anyway the guide on website told me to run this at the terminal

/flashplayer-installer

im guessing this is wrong coz it extracted a directory anyway
shouldnt i have exacuted this instead

/install_flash/flashplayer-installer

the "install_flash" is the folder "flashplayer-installer" was extracted to.
anyway like i said i couldnt install to / so i extracted to desktop.
this is (my guess at what i should type) what i enter to the terminal

oem@******:~$ //home/oem/desktop/install_flash/flashplayer-installer
bash: //home/oem/desktop/install_flash/flashplayer-installer: No such file or directory

also i have tryed just double clicking on this file to no avail.
maybe its the oem problem???

---

### Post by odinfromvalhalla on 2006-09-27
try running the installer as root:

sudo ./flashplayer-installer

---

### Post by joshuapurcell on 2006-09-27
I'm not sure what the cause of your problem would be, but I would suggest using Automatix to install the Flash player since it is by far the easiest way of doing it:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Post if this doesn't help, if you have any questions, or if you want to try something else.

---

### Post by uk_sphinx on 2006-09-28
i guess il give it ago.automatrix i mean.
i wanted to learn the other way though.
seems like im getting an easy answer to a method i should learn.
i darnt put a new user in place like it tells me to after install.
last time i deleted oem and created a new user, it wouldnt let me log in as root (by default) and the new user had an error not letting me in coz it didnt create home file or somthing
i had to reinstall coz i could only load up the command line.
you do realize my user name is oem (tempory) right?
actually, how am i supposed to use automatrix if i cant even install it?
when i download it i can only extract it to desktop again coz of bloody privileges.


loving all these problems though
good challenge

---

