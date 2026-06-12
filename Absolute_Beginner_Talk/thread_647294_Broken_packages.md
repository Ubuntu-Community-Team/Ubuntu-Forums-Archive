---
title: "Broken packages"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by steelmole on 2007-12-22
I can't install anything else due to something called broken packages.  I tried using synaptic to fix broken packages.  I try the command line and I get this:
```
laurie@laurie-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmodplug0c2 libmysqlclient15off fftw3 libxcb-xv0 libtunepimp5 ruby1.8
  libxcb1 python-qt3 ruby libkonq4 python-sip4 kdebase-bin libifp4
  libdbus-qt-1-1c2 kdesktop kdebase-kio-plugins libpq5 libruby1.8
  libxcb-shape0 libxcb-shm0 mysql-common libswt3.2-gtk-jni libnjb5 libofa0
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't install anything, it's really getting quite annoying now.

---

### Post by SOULRiDER on 2007-12-22
Is your /boot partition full (if you have one)
Try these commands
```
sudo dpgk --configure -a
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by philinux on 2007-12-22
Like it tells you use

> sudo apt-get autoremove

:)

---

### Post by steelmole on 2007-12-22
I tried the first line :
```
laurie@laurie-desktop:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
```

---

### Post by steelmole on 2007-12-22
> **philinux said:**
> Like it tells you use



:)

I tried that:

```
laurie@laurie-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by philinux on 2007-12-22
I googled this > /usr/sbin/mkinitramfs: 13: getopt: not found

and found this.

[http://ubuntuforums.org/showthread.php?t=550085](http://ubuntuforums.org/showthread.php?t=550085)

---

### Post by steelmole on 2007-12-22
I can't really see what to do from that.  I tried ```
sudo dpkg -i --force-all /var/cache/apt/archives linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb

``` but it didn't seem to find the file or anything.  I don't really understand.

---

### Post by philinux on 2007-12-22
Did you run the second command too.

What were the messages from the first.

---

### Post by steelmole on 2007-12-22
I wasn't sure how to adapt the second command to my situation.

Here's what I got from the first one:
```
laurie@laurie-desktop:~$ sudo dpkg -i --force-all /var/cache/apt/archives linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb
[sudo] password for laurie:
dpkg-split: error reading /var/cache/apt/archives: Is a directory
dpkg: error processing /var/cache/apt/archives (--install):
 subprocess dpkg-split returned error exit status 2
dpkg: error processing linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives
 linux-image-2.6.22-14-generic_2.6.22-14.47_amd64.deb

```

---

### Post by steelmole on 2007-12-23
Bump

---

### Post by steelmole on 2007-12-23
Bump again, this really is a majorly annoying problem because I can't install anything or update my system.

---

### Post by philinux on 2007-12-23
you didn't use the commands from the link you use a 64bit version.


The thread said

sudo dpkg -i --force-all /var/cache/apt/archives/ udev_113-0ubuntu14_i386.deb

and 

sudo apt-get install util-linux

---

### Post by steelmole on 2007-12-23
Right, because that's not the broken package surely? Here's what I get using the command from that thread verbatim:

```
laurie@laurie-desktop:~$ sudo dpkg -i --force-all /var/cache/apt/archives/ udev_113-0ubuntu14_i386.deb
[sudo] password for laurie:
dpkg-split: error reading /var/cache/apt/archives/: Is a directory
dpkg: error processing /var/cache/apt/archives/ (--install):
 subprocess dpkg-split returned error exit status 2
dpkg: error processing udev_113-0ubuntu14_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/
 udev_113-0ubuntu14_i386.deb

```

The second one seemed to work, and now I think everything is working again.  My apologies for my insolence.

---

### Post by philinux on 2007-12-23
We are all trying to help and most important to learn.

Merry Xmas glad it got sorted.

---

### Post by WileyCoyote on 2007-12-23
> **steelmole said:**
> I can't install anything else due to something called broken packages.  I tried using synaptic to fix broken packages.  I try the command line and I get this:
```
laurie@laurie-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmodplug0c2 libmysqlclient15off fftw3 libxcb-xv0 libtunepimp5 ruby1.8
  libxcb1 python-qt3 ruby libkonq4 python-sip4 kdebase-bin libifp4
  libdbus-qt-1-1c2 kdesktop kdebase-kio-plugins libpq5 libruby1.8
  libxcb-shape0 libxcb-shm0 mysql-common libswt3.2-gtk-jni libnjb5 libofa0
  libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I can't install anything, it's really getting quite annoying now.

I had a SIMILAR problem, although maybe not identical.

What fixed it for me was the following:


*sudo apt-get install util-linux*

---

### Post by brn80 on 2008-03-08
> **WileyCoyote said:**
> I had a SIMILAR problem, although maybe not identical.

What fixed it for me was the following:


*sudo apt-get install util-linux*
 
Thanks for that, had the same problem with a similar output. The above command fixed it. Although it didn't let do the udev stuff, I then did the autoremove, then I could update fine !

---

