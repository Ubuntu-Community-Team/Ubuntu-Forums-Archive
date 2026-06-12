---
title: "[SOLVED] Virtual box and gutsy, a NO NO"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-11-02
I have Gutsy installed on my box. But, i installed Vbox and i get the OSE version, that does not support USB, i want the other version that i had on my box when i had fiesty, that one supported USB. 

How can i get that one?

---

### Post by ubukool on 2007-11-02
Hi,

Just download and install the latest version from the virtualbox website like I did:

[http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb](http://www.virtualbox.org/download/1.5.2/virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb)

:)

---

### Post by ritterrav on 2007-11-02
R u allowed to use USB devices? with that latest one. IS it OSe or the other one?

---

### Post by ritterrav on 2007-11-02
```
rav@rav-desktop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
rav@rav-desktop:~$ sudo apt-get install virtualbox
[sudo] password for rav:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rav@rav-desktop:~$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
rav@rav-desktop:~$ 




```

it says OSE not the regular one. so what do i do?

---

### Post by ubukool on 2007-11-02
The package in the Ubuntu repositories is the OSE version.  I'd uninstall that one and download the version on the link that I posted before, which is not the OSE version and install that instead.

This is the difference between the standard (closed) version and the OSE version:

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

Good luck

---

### Post by rcdeacon on 2007-11-02
The virtualbox downloaded from their site (NOT the ose version in the repos) WILL work with usb devices. You have to do a couple of "tweaks" but it will work and I use it routinely.

---

### Post by ubukool on 2007-11-02
hi,

As rcdeacon says, you need to do a couple of 'tweaks' which I've just found out about.  The first is you need to go into System-->Administration---->Users and Groups, click on 'manage groups' and add a group called usbfs.  You then tick the box for your user ID to add yourself to this group.

Next, follow the instructions in this:

[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/151585)

You'll also have to implement this change from the virtualbox users manual where you have to change your /etc/fstab file to change the permissions for the usbfs group to allow access by users:

9.4.6. USB not working

If USB is not working on your Linux host, make sure that the current user has permission to access the USB filesystem (usbfs), which VirtualBox relies on to retrieve valid information about your host's USB devices.

The permissions for usbfs can be changed by editing the /etc/fstab file.

For example, most Linux distributions have a user group called usb or similar, of which the current user must be a member. To give all users of that group access to usbfs, make sure the following line is present:

# 85 is the USB group
none /proc/bus/usb usbfs devgid=85,devmode=664 0 0

Replace 85 with the group ID that matches your system (search /etc/group for "usb" or similar).

Alternatively, if you don't mind the security hole, give all users access to USB by changing "664" to "666".


and hopefully it should work!

good luck

:)

---

