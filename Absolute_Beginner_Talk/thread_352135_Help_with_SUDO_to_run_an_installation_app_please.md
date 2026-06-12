---
title: "Help with SUDO to run an installation app please"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by wolf_t on 2007-02-02
Hi

I'm new to Ubuntu and Linux and have been trying to install a printer app.

The installation readme says:-

Installation: Extract the archive, change to the new created directory and start "./setup" (root login required):
tar -xzf turboprint-1.95-2.tgz
cd turboprint-1.95-2
./setup
Ubuntu:
sudo ./setup 

I logged into a terminal as root and tried to run the setup file.

This was the output:-
root@ineke-desktop:/usr/lib/turboprint# sudo ./setup
sudo: ./setup: command not found


Any pointers as to where I'm going wrong?

Thanks

---

### Post by LostShootingStar on 2007-02-02
why are you logging in as root, AND using sudo? if you are already root, you dont need sudo. its one or the other...sudo is highly recomended. though, it looks like it cant find the file ./setup at all. make sure your in the right directory..

---

### Post by wolf_t on 2007-02-02
Just following the installation readme, verbatim.

If I try to run the ./setup command as root I get the following:-

root@ineke-desktop:/usr/lib/turboprint# ./setup
bash: ./setup: Permission denied

---

### Post by aysiu on 2007-02-02
Why don't you try this instead? ```
wget -c http://www.turboprint.info/turboprint_1.95-2_i386.deb
sudo dpkg -i turboprint_1.95-2_i386.deb
```

---

### Post by wolf_t on 2007-02-02
Thanks for the link. 
If all else fails I guess I could install from there but my curiosity has been aroused and I'd like to follow this through and learn a bit more.

Any more thoughts as to why the setup won't run?

---

### Post by aysiu on 2007-02-02
Well as LostShootingStar said, you don't ever need to log in as root in Ubuntu.

*sudo* temporarily gives you root privileges for that one command. So ```
sudo ./setup
``` in Ubuntu is pretty much the same as ```
su
./setup
exit
``` in any other Linux distribution.

---

### Post by wolf_t on 2007-02-02
I have tried this running the setup routine using SUDO while not logged in as root but still get the bash error:
bash: ./setup: Permission denied

---

### Post by aysiu on 2007-02-02
> **wolf_t said:**
> I have tried this running the setup routine using SUDO while not logged in as root but still get the bash error:
bash: ./setup: Permission denied
Hm. That's weird. What's the output of this command? ```
ls -al
```

---

### Post by wolf_t on 2007-02-02
total 756
drwxr-xr-x  13 ineke ineke   4096 2007-01-15 17:41 .
drwxr-xr-x 137 root  root   32768 2007-02-03 09:38 ..
drwxr-xr-x   2 ineke ineke   4096 2007-01-15 17:57 bin
-rw-r--r--   1 ineke ineke   1002 2007-01-15 17:57 BUGREPORT
-rw-r--r--   1 ineke ineke  14902 2007-01-15 17:57 CHANGES
drwxr-xr-x   2 ineke ineke   4096 2007-01-15 17:57 colors
drwxr-xr-x   2 ineke ineke   4096 2007-01-15 17:57 deb
drwxr-xr-x   4 ineke ineke   4096 2007-01-15 17:57 doc
drwxr-xr-x   3 ineke ineke   4096 2007-01-15 17:57 dump
-rw-r--r--   1 ineke ineke   5570 2007-01-15 17:57 INSTALLATION
drwxr-xr-x   2 ineke ineke   4096 2007-01-15 17:57 lib
drwxr-xr-x   2 ineke ineke   4096 2007-01-15 17:57 locale
drwxr-xr-x   3 ineke ineke   4096 2007-01-15 17:57 maketpdeb.tmp
drwxr-xr-x   2 ineke ineke  12288 2007-01-15 17:57 printers
drwxr-xr-x   2 ineke ineke   4096 2007-01-15 17:57 profiles
-rw-r--r--   1 ineke ineke   3578 2007-01-15 17:57 README
drwxr-xr-x   2 ineke ineke   4096 2007-01-15 17:57 rpm
-rw-r--r--   1 ineke ineke   5883 2007-01-15 17:57 setup
-rw-r--r--   1 ineke ineke    542 2007-01-15 17:57 system.cfg
-rw-r--r--   1 ineke ineke  48250 2007-01-15 17:57 testmargins-a4.ps
-rw-r--r--   1 ineke ineke  48264 2007-01-15 17:57 testmargins-letter.ps
-rw-r--r--   1 ineke ineke 261015 2007-01-15 17:57 testpage-a4.ps
-rw-r--r--   1 ineke ineke 261019 2007-01-15 17:57 testpage-letter.ps
-rw-r--r--   1 ineke ineke   1323 2007-01-15 17:57 uninstall

---

### Post by st00ner on 2007-02-03
try:
sudo sh setup

---

### Post by wolf_t on 2007-02-03
TurboPrint Installation
=======================
setup: 41: bin/tpsetup: Permission denied

Installation language (e)nglish or (d)eutsch? e

No keyfile present in installation directory.
Installing TurboPrint Free Edition.
Thanks, stOOner got a little bit further...


Installation for CUPS printing system (TP_CUPS=1)
Configuration files will go to.. /etc/turboprint
Shared files will go to......... /usr/share/turboprint
Executable files will go to..... /usr/bin
Logfiles files will go to....... /var/log
Documentation will go to........ /usr/share/turboprint/doc
Browser for documentation....... konqueror

(edit system.cfg to change installation paths)

Begin installation now (y/n)? y
setup: 197: lib/install-static: Permission denied
setup: 202: lib/install-post: Permission denied
setup: 206: lib/install-info: Permission denied

HTML documentation can be found in /html /usr/share/turboprint/doc/html
Do you want to read the manual now (y/n)? n

---

### Post by w6kkt on 2007-02-03
In order for  Turboprint setup to work the  turboprint "key file" needs to be in the turboprint 1-1.95-2 file that was created when you unzipped the turboprint tar file.  Program will not work without the "key".  You should have received the "key" file from Turboprint.  

Regards,

Jesse, (w6kkt)

---

