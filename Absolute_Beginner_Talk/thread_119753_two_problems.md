---
title: "two problems"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by priyank on 2006-01-20
I had installed the Ubuntu successfully...
:) 
Mounted the NTFS and FAT partitions also on that .. :) 

Now have three problems
1  I have one DIAS (Direct internet access system) modem installed on LAN.  for which we need to install the driver (dialer) for windows its easy to do .. but linex they said "> FOR LINUX 
----------
For redhat 7.2 or higher 

Installing using RPM

Copy RPM rp-pppoe-3.5-1.i386.rpm in the root directory. 

Execute the command
rpm -Uvh rp-pppoe-3.5-1.i386.rpm

To configure
/usr/sbin/adsl-setup

To connect
/usr/sbin/adsl-start


To stop/disconnect 
/usr/sbin/adsl-stop


To install GUI based PPPoE
rpm -Uvh rp-pppoe-3.5-1.i386.rpm rp-pppoe-gui-3.5-1.i386.rpm

To connect GUI based PPPoE
/usr/bin/tkpppoe


when I tried to copy these files to root directory of file system ... it dosn't allow that (means the pasting option doesn't come ... 

What should I Do

2  I have a PCI CDMA Internet Card to connect net .... its DotSurfer GTRAN 3000 Card .... I am not able to find out the driver for this ... can anyone help me out. ..

3  I am LAN and all other pcs are on Windows plateform  When I tried to access lan it gives error

"The folder contents could not be displayed. Sorry, couln't display all the contents of "Windows Network :workgroup"]

Please help

---

### Post by bartbes on 2006-01-20
1. for installing RPM files you need to convert them with alien and use sudo in front of the commands you can't do because you don't have enough rights
3. check if network connection is ok and install samba and smbfs with 'sudo apt-get install samba smbfs' (without quotes)

---

### Post by rooster on 2006-01-20
Hi,

the ```
rp-pppoe-3.5-1.i386.rpm
``` seems to be the Roaring Penguin PPP over Ethernet driver. Try to install it with Synaptic or use another PPPoE-driver. (Use the search-functionality in Synaptic)

Then use the configuration for this driver (depends on the driver, for the RP PPoE you have the information, for another one look in the "man-pages"  from the CLI ```
man program
``` where "program" is the name of the programm you are searching help for.

You can try to install the GUI-Version ```
rp-pppoe-gui-3.5-1.i386.rpm
```, too. But I don't know if it's depending on gnome or KDE or ncurses (last one is most universal).

Good luck, hope it helps (sitting in front of a windows-PC),

Rooster

---

### Post by jon_z on 2006-01-20
for a guide on installing setting up samba, i must suggest: [Samba Guide]("http://www.ubuntuforums.org/showthread.php?t=76647")

---

### Post by priyank on 2006-01-21
when I tried to do anything it says :
Warning
W: Couldn't start source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe package (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_binary-i386_packages) - start (2 No such file or directory)

and so on

:(

---

### Post by rooster on 2006-01-26
[QUOTE=priyank]when I tried to do anything it says :
Warning
W: Couldn't start source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe package (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_binary-i386_packages) - start (2 No such file or directory)

and so on

:([/QUOTE]

Do you have internet connection? If not then these messages are quite normal.

---

### Post by priyank on 2006-01-26
Thanks for reply

As I had told you that earlier that I have internet connections ... three different types of connections.

1  Normal Dial up connection which runs through the inbuilt modem.
2  DIAS connection which is a sort of ADSL connection which run through LAN
3  GTRAN PCI CDMA Internet Card 

All these three connections are working properly when I boot my system using Win XP...

Note that I have HP Compaq Presario ML2000 series laptop.

---

### Post by rooster on 2006-02-01
[QUOTE=priyank]Thanks for reply

As I had told you that earlier that I have internet connections ... three different types of connections.

1  Normal Dial up connection which runs through the inbuilt modem.
2  DIAS connection which is a sort of ADSL connection which run through LAN
3  GTRAN PCI CDMA Internet Card 

All these three connections are working properly when I boot my system using Win XP...

Note that I have HP Compaq Presario ML2000 series laptop.[/QUOTE]

Sorry for not answering in the last few days!

I meant that if you haven't a _working_ Internet connection then the message above from synaptic is quite normal. And it seems to me that your Internet connection isn't working or you haven't connected to the Internet before starting Synaptic.

Is this right?

Rooster

---

