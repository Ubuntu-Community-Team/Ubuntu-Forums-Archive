---
title: "How to install VMware"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Mubat on 2007-09-14
I try to install VMware I checked Build Environment 
> 
root@ITCS:/home/itc/vmware-server-distrib# aptitude install linux-headers-`uname -r` build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a libqt3-mt librpcsecgss3 
The following packages have been kept back:
  dbus dbus-1-utils firefox firefox-gnome-support gimp gimp-data gimp-python libdbus-1-3 libgimp2.0 
  libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libjasper-1.701-1 libkrb53 libnspr4 libnss3 libpoppler1 
  libpoppler1-glib libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 linux-headers-2.6.20-16 
  linux-image-2.6.20-16-generic mesa-utils poppler-utils python-launchpad-bugs rsync tar tzdata vim-common 
  vim-tiny 
0 packages upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

> 
root@ITCS:/home/itc# aptitude install xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  kdelibs-data kdelibs4c2a libqt3-mt librpcsecgss3 
The following packages have been kept back:
  dbus dbus-1-utils firefox firefox-gnome-support gimp gimp-data 
  gimp-python libdbus-1-3 libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx 
  libglu1-mesa libjasper-1.701-1 libkrb53 libnspr4 libnss3 libpoppler1 
  libpoppler1-glib libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 
  linux-headers-2.6.20-16 linux-image-2.6.20-16-generic mesa-utils 
  poppler-utils python-launchpad-bugs rsync tar tzdata vim-common vim-tiny 
0 packages upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


but I got this msg

>  
itc@ITCS:~/vmware-server-distrib$ sudo vmware-install.pl
sudo: vmware-install.pl: command not found


> 
root@ITCS:/home/itc/vmware-server-distrib# vmware-install.pl
bash: vmware-install.pl: command not found

What is a problem here?
What is difference su and sudo? Please

---

### Post by chuckyp on 2007-09-14
Makes sure that vmware-install.pl is marked as executable then 
```

root@ITCS:/home/itc/vmware-server-distrib# ./vmware-install.pl

```

The ./ tells it to execute here since /home/itc/vmware-server-distrub isn't in your path.

Also you may want to check out virtualbox which i'm begining to like more and more over vmware.

---

### Post by hyper_ch on 2007-09-14
Add the Canoncial Commercial Repos to your sources list and you will find vmware server in the repos then.

---

### Post by anaconda on 2007-09-14
I have always installed vmware by downloading the installer from:
[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)
and then just extracting it and running the installer.

This way you will always get the newest version. Another reason is that I havn't had much success in installing vmware from the repositories. I guess it works better from the repositories now..


Ääääh.. just noticed that you are running the command wrongly.. it seems you already have downloaded the vmware server.

when you want to run an executable from a directory that in NOT in your path you have to put ./ in front of the filename.
eg.
cd ~/vmware-server-distrib
sudo ./vmware-install.pl

That should solve it..

PS. the current directory can be added to the PATH, if you want. but it isn't there by default.

---

### Post by cwmoser on 2007-09-14
In addition, you will need the vmware patch.

Download it at:
[http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

Untar the patch:
tar xvzf /Path/To/vmware-any-any-update109.tar.gz 
Enter the directory: 
cd vmware-any-any-update109
Run the patch script:
sudo ./runme.pl


Carl

---

### Post by anaconda on 2007-09-14
> **cwmoser said:**
> In addition, you will need the vmware patch.

Hmm. I forgot that. Is it really STILL needed? I thought that vmware was going to fix the problem.

---

### Post by Mubat on 2007-09-16
Thanks all!
> 
itc@ITCS:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to find the binary installation directory (answer BINDIR)
       in the installer database file "/etc/vmware/locations".

Failure

Execution aborted.


How Can I solve this?

---

### Post by aktiwers on 2007-09-16
Is there any reason you are not installing VirtualBox?
 ```
sudo apt-get install virtualbox
```

---

