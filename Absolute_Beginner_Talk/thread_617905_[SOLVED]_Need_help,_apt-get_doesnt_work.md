---
title: "[SOLVED] Need help, apt-get doesnt work"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by elec999 on 2007-11-19
Any application I try to install with app-get wont install.
example 
giant@GiantQ:~$ sudo apt-get install dosbox
[sudo] password for giant:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmikmod2 libsdl-net1.2 libsdl-sound1.2 libsmpeg0
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-xen
The following NEW packages will be installed:
  dosbox libmikmod2 libsdl-net1.2 libsdl-sound1.2 libsmpeg0
0 upgraded, 5 newly installed, 1 to remove and 6 not upgraded.
7 not fully installed or removed.
Need to get 0B/1027kB of archives.
After unpacking 6738kB disk space will be freed.
Do you want to continue [Y/n]? 
Result
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmikmod2 libsdl-net1.2 libsdl-sound1.2 libsmpeg0
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-xen
The following NEW packages will be installed:
  dosbox libmikmod2 libsdl-net1.2 libsdl-sound1.2 libsmpeg0
0 upgraded, 5 newly installed, 1 to remove and 6 not upgraded.
7 not fully installed or removed.
Need to get 0B/1027kB of archives.
After unpacking 6738kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122735 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-xen ...
FATAL: Could not open '/boot/System.map-2.6.22-14-xen': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-xen
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-xen
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
Thanks

---

### Post by Abild on 2007-11-19
Do you use the xen virtualization features provided by the kernel you are running? If not, you should try to boot into another kernel. Unless you have removed the 2.6.22-14-generic package it should still be avaiilible from your boot menu.
So, reboot your computer and (if possible) select the 2.6.22-14-generic kernel and try to install dosbox again.

---

### Post by elec999 on 2007-11-19
> **Abild said:**
> Do you use the xen virtualization features provided by the kernel you are running? If not, you should try to boot into another kernel. Unless you have removed the 2.6.22-14-generic package it should still be avaiilible from your boot menu.
So, reboot your computer and (if possible) select the 2.6.22-14-generic kernel and try to install dosbox again.
I tried the xen and didnt work. I am in generic kernel.
Thanks

---

### Post by elec999 on 2007-11-20
Is there anyway I can force remove this xen. Because I cannot install anything anymore. Ap-get is dead.
Thanks

---

### Post by Anicka on 2007-11-20
There are some commands that you can try to run. Start softly by trying```
sudo apt-get -f install
```and```
sudo dpkg --configure linux-ubuntu-modules-2.6.22-14-xen
```and```
sudo dpkg --purge linux-ubuntu-modules-2.6.22-14-xen
```
If that doesn't help (check by running apt-get again) you should post the messages that you get.

---

### Post by elec999 on 2007-11-20
giant@GiantQ:~$ sudo apt-get -f install
[sudo] password for giant:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-xen
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9851kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122735 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-xen ...
FATAL: Could not open '/boot/System.map-2.6.22-14-xen': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-xen
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-xen
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
giant@GiantQ:~$ sudo dpkg --configure linux-ubuntu-modules-2.6.22-14-xen
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--configure):
 package linux-ubuntu-modules-2.6.22-14-xen is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-xen
giant@GiantQ:~$ sudo dpkg --purge linux-ubuntu-modules-2.6.22-14-xen
(Reading database ... 122735 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-xen ...
FATAL: Could not open '/boot/System.map-2.6.22-14-xen': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-xen
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-xen
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-xen


giant@GiantQ:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-xen
The following packages will be upgraded:
  capplets-data gnome-control-center gnome-panel gnome-panel-data
  libgnome-window-settings1 libpanel-applet2-0
6 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/2478kB of archives.
After unpacking 9765kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122735 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-xen ...
FATAL: Could not open '/boot/System.map-2.6.22-14-xen': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-xen
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-xen
dpkg: error processing linux-ubuntu-modules-2.6.22-14-xen (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-xen
E: Sub-process /usr/bin/dpkg returned an error code (1)
giant@GiantQ:~$

Thanks

---

### Post by schorsch on 2007-11-20
What about:
```
sudo dpkg --remove --force-remove-reinstreq linux-ubuntu-modules-2.6.22-14-xen
```

---

### Post by Anicka on 2007-11-21
That will take away reference to the package (make it invisible to apt-get), however it is to be used with caution as everything with the command force in it. You could try to reinstall "sudo apt-get install -f linux-ubuntu-modules-2.6.22-14-xen" and afterwards "sudo apt-get remove -f linux-ubuntu-modules-2.6.22-14-xen". If that doesn't work than I think schorsch has the winning command.

---

### Post by elec999 on 2007-11-21
> **schorsch said:**
> What about:
```
sudo dpkg --remove --force-remove-reinstreq linux-ubuntu-modules-2.6.22-14-xen
```
This command fixed it.
Thanks

---

### Post by schorsch on 2007-11-21
Could you please mark your thread as solved?

---

