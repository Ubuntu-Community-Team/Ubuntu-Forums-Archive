---
title: "i cannot detect my agere systems PCI soft modem  in ubuntus"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by dennykvg on 2006-12-01
i have a  compaq pc ( 64 bit AMD ATHELON) recently i installed ubuntu in place windows but i can not connect internet i seached driver for my modem working in linux didn,t get my  modem name is agere systems PCI soft modem  i nstalled scan modem details got are pasted below please give assisstance to this problem

 --------------------------  System information ----------------------------
 Ubuntu 6.06 LTS 
Linux version 2.6.15-23-amd64-generic (buildd@yellow) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Tue May 23 13:45:47 UTC 2006
 scanModem update of:  2006_November_07


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:02:02.0	11c1:048c	11c1:044c	Communication controller: Agere Systems V.92 56K WinModem 

 Modem interrupt assignment and sharing: 

 --- Bootup diagnositcs for card in PCI slot 0000:02:02.0 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  0000:02:02.0
   Class 0780: 11c1:048c Communication controller: Agere Systems V.92 56K WinModem
      Primary PCI_id  11c1:048c
 Support type needed or chipset:	Agere.SV2P
 Under Linux 2.6.n kernels, the chipset is NOT SUPPORTED . Read InfoGeneral.txt about alternatives.


 Vendor 11c1 is Lucent Technologies or subsidiary Agere Systems, Inc. Their Linux
 code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced, 
 and two have support under Linux:
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048(c,d,f) none           SV2P            soft modem 
 0600       none                           soft modem, very few in the field.
 062(0-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

-------------- end Agere Systems section -------------------

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 The kernel was compiled with gcc version 4.0.3 and a compiler is not installed


If compiling a modem driver proves to be necessary, one of the two procedures must be followed.
If not yet on the Internet, put the Dapper install CD in the drive
Open a terminal and therein:
$ sudo apt-get install  gcc-4.0  make
Additionally the package linux-headers-2.6.15-23-amd64-generic must be downloaded.  
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  and search for linux-headers-2.6.15-23-amd64-generic 
After downloading, it can be installed with:
$ sudo dpkg -i linux-header*.deb

Or alternatively if online through Ethernet do:
$ sudo apt-get update
$ sudo apt-get install build-essential
will do all the necessary installations mentioned above.

In either installation case, set a symbolic link which will be expected later:
$ sudo ln -s /usr/bin/gcc-4.0  /usr/bin/gcc
After check with:
$ ls -l /usr/bin/gcc*
which should display:
lrwxrwxrwx 1 root root    16 2006-07-09 21:53 /usr/bin/gcc -> /usr/bin/gcc-4.0
-rwxr-xr-x 1 root root 93584 2006-04-20 18:22 /usr/bin/gcc-4.0
-rwxr-xr-x 1 root root 16245 2006-04-20 18:13 /usr/bin/gccbug-4.0

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	gcc-4.0 make linux-headers-2.6.15-23-amd64-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 306720 2006-02-23 22:01 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
auth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:
/etc/udev/rules.d/60-symlinks.rules:# Create /dev/modem symlink
/etc/udev/rules.d/60-symlinks.rules:KERNEL=="ttyLTM[0-9]*",			SYMLINK+="modem"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
 
thank u

---

### Post by Ireclan on 2006-12-01
Well, how about that. You, good sir, appear to have a modem simular to the one that came with MY PC. In fact, I'm in the same boat you are- I need dail-up under Ubuntu as well. The bad news? Your modem isn't supported according to this scanout. Sorry, but you'll have to buy a new softmodem and try again. Alternatively, you could spend some time searching for a hardware-based modem, which are somehow supposed to be easier to get working under Ubuntu. Trouble is, I've heard hardware-based modems are REALLY rare these days, so good luck finding one. If you have cash to burn and it's available in your area, you could upgrade to a high-speed connection, which I THINK Ubuntu supports with virtually no hitches whatsoever.

---

