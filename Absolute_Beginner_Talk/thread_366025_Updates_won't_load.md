---
title: "Updates won't load"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by gewitty on 2007-02-20
Just installed 6.1 with Gnome for the very first time, having finally got fed up with Windows. I have very little knowledge of Linux and am still groping around finding out how things work.

My problem at the moment is that after an hour or so of running, I got an alert saying that there are 135 updates available to download. I fired up the Up date Manager and it listed all the updates OK. However, when I clicked the 'Install Updates' button, I got an error message, as follows:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Needless to say, that stopped me dead in my tracks. I made an attempt at entering the command in Terminal, which gave me the following response:

dave@dave-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
dave@dave-desktop:~$ 

Now I'm stuck. I think that I need to enter a password to gain superuser privileges, but haven't a clue what that might be. Can anyone enlighten me as to why the error happened in the first place and what I need to do to resolve it?

---

### Post by Obor on 2007-02-20
you need to run it as root i.e.
sudo dpkg --configure -a

It will ask you for your user password - thats the one you set up during install

---

### Post by gewitty on 2007-02-20
That seemed to work, but I haven't a clue what actually happened. There were some errors reported (see below) which appear to be concerned with a VM app that I installed earlier. Should I un-install this?



dave@dave-desktop:~$ sudo dpkg --configure -a
Password:
Setting up libqt3-mt (3.3.6-3ubuntu3) ...

Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.152.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet8/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet8/nat/nat.conf that this program was about to install 
already exists.  Overwrite? [yes] 

Configuring a host-only network for vmnet1.

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.76.0/255.255.255.0 appears to be unused.

The file /etc/vmware/vmnet1/dhcpd/dhcpd.conf that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases that this program was about to 
install already exists.  Overwrite? [yes] 

The file /etc/vmware/vmnet1/dhcpd/dhcpd.leases~ that this program was about to 
install already exists.  Overwrite? [yes] 

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
dave@dave-desktop:~$

---

### Post by gewitty on 2007-02-20
I've un-installed the VM app and the update packages are now downloading, so it looks as if that was what caused the problem.

---

### Post by skyhopper88 on 2007-02-20
I had that exact problem with vmware, and I just uninstalled it. I haven't looked for a fix for it though.

---

