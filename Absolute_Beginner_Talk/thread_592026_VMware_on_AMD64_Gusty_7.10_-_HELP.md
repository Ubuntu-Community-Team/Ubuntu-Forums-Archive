---
title: "VMware on AMD64 Gusty 7.10 - HELP"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by AlienTech on 2007-10-26
I have a amd64 set up with 7.10 64 on it. I've installed VMware via the tutorial here: [http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)

Everything went smooth... no issues but I can't seem to get vmware to actually start. I see it under my applications directory but when I click... nothing happens. I've also tried running it through the "alt+F2" command line. Did I miss something? Is this because I'm 64bit? 

Thanks in advance

---

### Post by swoll1980 on 2007-10-26
in terminal type VirtualBox post the out put

---

### Post by gtdaqua on 2007-10-26
I dont think that link will help u have what u need.

Make sure you have the needed build environment and tools to compile the vmware modules for the kernel.
```

aptitude install linux-headers-`uname -r` build-essential
aptitude install xinetd

```

for server
```

sudo aptitude install libxtst6 libxt6 libxrender1

```

on 64-bit (in your case, yes)
```

sudo apt-get install ia32-libs libc6-i386

```

The latest 1.04 version does not need any patch to be installed. Its a straight forward installation. I have installled several times on my Ubuntu 64 bit both Feisty and Gutsy and had no problems.

---

### Post by jusmurph on 2007-10-26
Oh and no it has nothing to do with being on 64.

And i think Swoll means "VMware"

---

### Post by AlienTech on 2007-10-26
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

is the output of VMware in the terminal. I also tried running the code '/usr/bin/vmware-config.pl." with no joy. Then the next suggestion = 

paul@Alien:~$ sudo apt-get install ia32-libs libc6-i386
[sudo] password for paul:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
libc6-i386 is already the newest version.
libc6-i386 set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Any new ideas?

---

### Post by AlienTech on 2007-10-26
I also noticed that after about 4 or 5 minutes my system crashes after trying to start Vmware. I appreciate all the help the forums have offered. Thanks again.

---

### Post by jusmurph on 2007-10-26
Uninstall VMWare, search for any other folders where VMware remains and delete them, a search of the forum should net an answer for this.

After all this, reinstall it and it should work fine.

---

### Post by gtdaqua on 2007-10-26
You may want to remove everything and try this. This is my personal guide I prepared myself. 


Build Environment:
Make sure you have the needed build environment and tools to compile the vmware modules for the kernel.
```

aptitude install linux-headers-`uname -r` build-essential
aptitude install xinetd

```

for server
```

sudo aptitude install libxtst6 libxt6 libxrender1

```

for 64-bit
```

sudo apt-get install ia32-libs libc6-i386

```

Downloading VMware Server 1.04 (not 1.03)

 Vmware Server can be downloaded from:
 [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) 
After accepting the EULA grab the vmware server .tgz file (around 102MB).

Installing VMware Server (1.04)

Untar the VMware Server package:
```

tar -xzf /Path/To/VMware-server-1.0.4-xxx.tar.gz

```

Change into the install directory:

```

cd vmware-server-distrib

```

Run the installer:
```

sudo ./vmware-install.pl

```

Hit enter to choose the defaults to all the questions, though you will probably want to manually choose which networking features you want. To access the server run
```

vmware

```

Mgmt Interface

from VMWare Download Site

```

tar zxvf VMware-mui-<xxx>.tar.gz
sudo ./vmware-install.pl

```

If you receive a "starting httpd.vmware:-ne failed" error at the end of running vmware-config-mui.pl you will need to run the following command.

**EXECUTE CAREFULLY!!**

```

sudo ln -s -f /bin/bash /bin/sh
sudo vmware-config-mui.pl

```

Install thin, basic KDE Environment on Server

```

sudo apt-get install kdebase kdm x-window-system-core

```



If VMWare hangs after some time, it could be because swap is not being used correctly. This happened once to me. You may have to reconfigure swap. Type "top" in terminal and see if swap memory is actually being used. If not, then reconfigure it.

---

### Post by AlienTech on 2007-10-26
This post found via a google search worked out for anyone else who may have this same issue: -in the terminal typed:

cd /etc/vmware
sudo mv not_configured not_configured.bkup

started VMware again and bingo bango It's there.

Thanks for the suggestions though peeps :)

---

