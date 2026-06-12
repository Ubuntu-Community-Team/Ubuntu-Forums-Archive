---
title: "How to install my Linmodem on Ubuntu"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by Solidad on 2006-05-23
i am having a hard time figuring out on how to install this driver.

[DFM-562IS]("http://www.dlink-intl.com/Technical/download.nsf/dwn?openframeset")

i found a driver but the isntructions are somewhat hard to understand. in order for me to fully use the ubuntu i have to make this work.

---

### Post by zluka on 2006-05-23
did you try this?

[https://wiki.ubuntu.com/DialupModemHowto]("https://wiki.ubuntu.com/DialupModemHowto")

---

### Post by dmizer on 2006-05-23
no idea about making it work in the live version.  i've never used it ... but i suspect it will cause problems.

the one you need is the source (there is an rpm in the package which may or may not work if aliened to a debian so i'll leave that for a last ditch because alien packages sometimes cause instability).

so once you have unzipped the package downloaded from that page, the only file you really need is the one labled hsfinmodem-4.06.0.6.03.tar.gz

extract the contents of that file via archive manager (right click > open with arcive manager) ... now you will have a new folder named hsfinmodem-4.06.0.6.03 ... the directions for installing your modem can be found in the file labled "install" ... your directions are under method c.  by this time you have already performed step number 1 in method c.
so ... in the shell, change your directory to the hsfinmodem directory we created earlier (in my case ... cd /Desktop/hsfinmodem-4.06.0.6.03) and type:
```
sudo make install
hsfconfig
```
post back if you run into a snag

---

### Post by Solidad on 2006-05-23
whats with the "sudo" is this only available on ubuntu. i dont usualy see this on other tutorials?

---

### Post by Solidad on 2006-05-23
it took me a lot of time. but i end up dead end. when i type sudo make install i get this msg.

[IMG]http://i21.photobucket.com/albums/b289/Solidad2x/send.jpg[/IMG]

---

### Post by dmizer on 2006-05-23
[QUOTE=Solidad]whats with the "sudo" is this only available on ubuntu. i dont usualy see this on other tutorials?[/QUOTE]
heh ... purely habit.  i'm not so much on a roll today apparently.

i tried to do it on my machine, but i get errors too ... it's trying to make folders, humm.

okay ... lets try alien.  extract hsfinmodem-4.06.0.6.03.rpm from the file 562IS_Linux.zip, and change to the directory you extracted it to.

then:
```
sudo apt-get update
sudo apt-get install alien
sudo alien -i 
```

---

### Post by dmizer on 2006-05-23
sudo is available on just about all debian based distros.  i believe even on many non debian based.  it is just a way of temporarily assigning root privelages to a command without having to sign into a root account.

and i'm not completely sure, but your having problems with sudo is possibly a function of running with the live cd.  which as i've said before ... i really don't know if it's configurable or not.

---

### Post by Solidad on 2006-05-23
i am now running the HD version of Ubuntu. 

after i get my modem to work. how do i connect?

---

### Post by Solidad on 2006-05-24
bump

---

### Post by Solidad on 2006-05-24
i tried installing the (.rpm) and able to type hsfconfig but i got this msg that i dont get. 

```
solidad@solidad:~/Desktop/Modem/usr/sbin$ sudo hsfconfig


Linux HSF softmodem drivers, version 4.06.06.03

grep: /proc/ksyms: No such file or directory
/usr/bin/hsfsysid:
line 99: [: too many arguments


No pre-built HSF modules are available for your exact kernel:
                Linux-2.6.12-9-386-i686-Debian-testing/unstable



Assuming that a C compiler and proper kernel header files are present
on your system, we will now attempt to re-compile the modules.




Where is the directory of C header files that match your running kernel?
[/usr/src/linux]




WARNING: missing file /usr/src/linux/include/linux/autoconf.h
The cause of this problem is usually a missing or misconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).



First, ensure that the proper kernel source and compiler packages
from your distribution vendor and/or the community are installed.

The Linux kernel can then be reconfigured by running "make menuconfig"


under the kernel source directory (usually /usr/src/linux).

Verify that the proper options for your system are selected,

and that CONFIG_SMP ("Symmetric multi-processing support" 

under
"Processor type and features") is disabled, as this driver is


presently designed to work on single-processor machines.



Then compile and install your new kernel (for more information about
this procedure, see the README file under the kernel source directory),


reboot the system using the new kernel, and re-run "hsfconfig".

```

---

