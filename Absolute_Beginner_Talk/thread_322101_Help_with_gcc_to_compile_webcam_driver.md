---
title: "Help with gcc to compile webcam driver"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by Paul_world10 on 2006-12-20
Hello , I am running Dapper Drake 6.06LTS on my PC. I have a Logitech usb communicator webcamera that I wish to install. I have downloaded a camdriver program that goes along the lines of {gspcav1-20061216.tar.gz} .  when I run gcc by inputing the make , make install or make -n I get this error. I would definately appreciate your help. Thanks

paul@desktopbox:~/CamDriver/gspcav$ dir
amsn-0.96-2.tcl84.x86.package  Etoms         Makefile   Sunplus       Vimicro
changelog                      gspca_build   Mars-Semi  Sunplus-jpeg
Conexant                       gspca_core.c  Pixart     Transvision
decoder                        gspca.h       Sonix      utils
paul@desktopbox:~/CamDriver/gspcav$ sudo make -n
Password:
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/paul/CamDriver/gspcav CC=cc modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
paul@desktopbox:~/CamDriver/gspcav$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/media/video/gspca.ko
install -c -m 0644 gspca.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `gspca.ko': No such file or directory
make: *** [install] Error 1
paul@desktopbox:~/CamDriver/gspcav$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/paul/CamDriver/gspcav CC=cc modules
make: *** /lib/modules/2.6.15-27-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
paul@desktopbox:~/CamDriver/gspcav$

---

### Post by macogw on 2006-12-20
Did you read the README?  You probably have to type:
./configure
before you do "make"

---

### Post by Paul_world10 on 2006-12-20
Nothing is said in the readme file about entering ./configure before  {make} or whatnot .  I guess I am in over my head , I had better read more.

---

### Post by po0f on 2006-12-20
Paul_world10,

You need to install the headers for whatever kernel you are currently running to compile kernel modules.  Try installing linux-headers-`uname -r`:
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install linux-headers-`uname -r`[/FONT]
```

[EDIT]

Run those commands from a terminal (Applications->Accessories->Terminal).

---

### Post by macogw on 2006-12-20
Do you have build-essential installed?
```
sudo apt-get install build-essential
```
Usually, installation from a tarball means cd'ing to the directory and typing
```

./configure
make
make install
make clean
```

---

### Post by po0f on 2006-12-20
macogw,

build-essential is installed (no "error: make: command not found" errors).  To compile kernel modules, all you need is build-essential and the headers for whatever kernel you are compiling modules for.

---

### Post by Paul_world10 on 2006-12-20
Thank you both for your help with my header and compile problem. When I 

installed the Kernal headers I am able to now run   make  just fine. Basically this seems  

 that this is the way Linux compiles .tar.gz {tarball and gunzip} files, am I correct? 


         If I can ask another question about compiling or whatnot please.  What if someone 
runs the make , make -n , or make install command then does that command compile the 
binary into the kernal?   So what if one wanted to uncompile the program or remove the binary out of the Kernal?  After a period of time does it affect the kernal by having excess binary ?  Any links would be appreciated and again thank you for your help.

---

### Post by po0f on 2006-12-20
Paul_world10,

[Installing software in Ubuntu](http://www.psychocats.net/ubuntu/installingsoftware).

What you did is compile a kernel *module*, it is not a part of the kernel unless you `modprobe <module>` it.  To uninstall it, hopefully the author of the Makefile you are using was considerate enough to add an "uninstall" rule.  If not, just run `sudo make install` again, and take note of what files it installs where, and just go and delete them when you don't want to use the module anymore.

---

