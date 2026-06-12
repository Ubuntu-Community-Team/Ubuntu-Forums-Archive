---
title: "Vmware Player error"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-19
I got an error. I couldnt copy it so i took a screen shot.
[ATTACH]27872[/ATTACH]

I previously tried to install the vmware server, but i figured out theat player will do fine. So how do I fix this?

---

### Post by tonyr1988 on 2007-03-19
If you haven't already, try this:

Applications -> Accessories -> Terminal

Type:

> sudo /usr/bin/vmware-config.pl

And go through all the steps. See if that works.

---

### Post by ProjectWhat on 2007-03-19
gave me this error:
```
ben@ben-ubuntu:~$ sudo /usr/bin/vmware-config.pl
sudo: /usr/bin/vmware-config.pl: command not found
ben@ben-ubuntu:~$ 

```

---

### Post by ProjectWhat on 2007-03-19
I searched for the file
```

vmware-config.pl 

```
and it was found here:
```

/home/ben/bin

```

---

### Post by AndyCooll on 2007-03-19
Two things.

1. When you tried installing VMware server did you follow this howto?: [ HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://www.ubuntuforums.org/showthread.php?t=183209")

2. Not sure why you're taking the approach you are for installing VMware Player since it is in the repositories, Using Synaptic should make the install process easier.

:cool:

---

### Post by ProjectWhat on 2007-03-19
yes that is the tut I went by. I got errors in that too should I redo that tut and paste the results?

I used synapic for player (at least I thought so).

---

### Post by AndyCooll on 2007-03-19
> **ProjectWhat said:**
> I used synapic for player (at least I thought so).

It doesn't appear to me that you are using Synaptic (System > Administration > Synaptic Package Manager) if you're using the command line.

By all means attempt the tutorial for Server again. Pay close attention to the software you need to install before you actually begin the VMware installation.

:cool:

---

### Post by ProjectWhat on 2007-03-19
i get this error now.
```
ben@ben-ubuntu:~$ sudo apt-get install linux-headers-`uname -r` build-essential xinetd
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-11-generic is already the newest version.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  debian-keyring gcc-4.1-doc lib64stdc++6 glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev xinetd
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 3753kB/8063kB of archives.
After unpacking 30.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com edgy-security/main linux-libc-dev 2.6.17.1-11.35 [1770kB]
Get:2 http://us.archive.ubuntu.com edgy-updates/main libc6-dev 2.4-1ubuntu12.3 [1852kB]
Get:3 http://us.archive.ubuntu.com edgy/main xinetd 1:2.3.14-1 [131kB]         
Fetched 3753kB in 20s (182kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 110484 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.17.1-11.35_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.4-1ubuntu12.3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.1-13ubuntu5_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.1.1-6ubuntu3_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Selecting previously deselected package xinetd.
Unpacking xinetd (from .../xinetd_1%3a2.3.14-1_i386.deb) ...
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.68.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] yes

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.34.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] yes

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] yes

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
VMware Player is installed, but it has not been (correctly) configured
for the running kernel. To (re-)configure it, invoke the
following command: /usr/bin/vmware-config.pl.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-libc-dev (2.6.17.1-11.35) ...
Setting up libc6-dev (2.4-1ubuntu12.3) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up xinetd (2.3.14-1) ...
Stopping internet superserver: xinetd.
Adding `diversion of /etc/init.d/inetd to /etc/init.d/inetd.real by xinetd'
Starting internet superserver: xinetd.

Setting up libstdc++6-4.1-dev (4.1.1-13ubuntu5) ...
Setting up g++-4.1 (4.1.1-13ubuntu5) ...
Setting up g++ (4.1.1-6ubuntu3) ...

Setting up build-essential (11.3) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)
ben@ben-ubuntu:~$ cd /tmp 
ben@ben-ubuntu:/tmp$ cd vmware-server-distrib
ben@ben-ubuntu:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

ben@ben-ubuntu:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

ben@ben-ubuntu:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

ben@ben-ubuntu:/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

ben@ben-ubuntu:/tmp/vmware-server-distrib$ 

```

Never got this one.

I even tried synapic

---

### Post by ProjectWhat on 2007-03-19
so can anyone help me any further?

---

### Post by ProjectWhat on 2007-03-19
bump

---

