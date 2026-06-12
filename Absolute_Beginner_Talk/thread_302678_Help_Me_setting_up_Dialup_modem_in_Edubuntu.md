---
title: "Help Me setting up Dialup modem in Edubuntu"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by kamalarora2kin on 2006-11-19
hello,

recently i installed Edubuntu 6.06, i have dialup modem working very gud in Windows XP, which was not detected by edubuntu. then i took some help from forums and got downloaded "**scanModem.gz file**" 

i ran scanModem and got the following result in file **ModemData.txt**
and a complete detail of modem configuration is as below:


 --------------------------  System information ----------------------------
 Ubuntu 6.06.1 LTS 
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 scanModem update of:  2006_November_07


USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:00:08.1	125d:1999	1028:00bb	Communication controller: ESS Technology ES1983S Maestro-3i PCI Modem Accelerator 

 Modem interrupt assignment and sharing: 
  5:        593          XT-PIC  Maestro3

 --- Bootup diagnositcs for card in PCI slot 0000:00:08.1 ----

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

 For candidate modem in PCI bus:  0000:00:08.1
   Class 0780: 125d:1999 Communication controller: ESS Technology ES1983S Maestro-3i PCI Modem Accelerator
      Primary PCI_id  125d:1999
 Support type needed or chipset:	ESS.com
 


 Vendor=125d is ESS Technologies, [http://www.esstech.com/](http://www.esstech.com/)
 The PCI id 125d:1999 modems are NOT_Supported under 2.6.n kernels.

 The driver resources for 125d:2898 modems should be downloaded
 from  [http://tx.technion.ac.il/~raindel/ess_2.6-v0.2.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.2.tar.gz) , benefitting
 from an update by Jeff Trull. There are brief instructions at [http://ubuntuforums.org/showthread.php?t=185079](http://ubuntuforums.org/showthread.php?t=185079)
 Under Linux, unpack with:
 $ tar zxf ess_2.6-v0.2.tar.gz
 Move into the folder wit:
 $ cd ess_2.6-v0.2
 Browse the files therein and run as Root the:
 $ sudo ./setup

 The setup program creates a port:
 $ ls -l /dev/ttyS_ESS0
    crw-rw-rw- 1 root root 62, 64 2006-09-23 23:08 /dev/ttyS_ESS0
 and a symbolic link to it:
   /dev/modem --> /dev/ttyS_ESS0
 Specify either /dev/modem or /dev/ttyS_ESS0 as the modem port for dialer utilities.
 A file is installed:
   /etc/udev/rules.d/ess.rules  , with line:
     "KERNEL=\"ttyS_ESS0\", SYMLINK=\"modem\"" 
 which supports automated port creation during driver loading.

 If the drivers do not autoload during bootup, they can be loaded by:
 $ sudo modprobe esscom
 after which the driver interdependencies can be displayed by:
   $ lsmod | grep esscom
   esscom                 16580  0
   esscom_hw             421328  1 esscom
   linmodems             345678  2 esscom esscom_hw
 
 The modem should be found by:
 $  sudo wvdialconf  wvtest
 See wvdial.txt and Testing.txt for follow through details.
 ===============
 For 2.4.n Linux kernels and are there some kludges of fading utility:
   [http://linmodems.technion.ac.il/archive-fourth/msg00317.html](http://linmodems.technion.ac.il/archive-fourth/msg00317.html)   (2004Feb08)
   [http://andrew.cait.org/ess/](http://andrew.cait.org/ess/)
   [http://sidlo.penguin.cz/ES2838/index_en.html](http://sidlo.penguin.cz/ES2838/index_en.html)
   [http://tx.technion.ac.il/~raindel/](http://tx.technion.ac.il/~raindel/) 
   [http://phep2.technion.ac.il/linmodems/archive/msg04424.html](http://phep2.technion.ac.il/linmodems/archive/msg04424.html)

  There was only formal support under for Linux for kernels 2.2.2.
 ====== end ESS.com section =======


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 The kernel was compiled with gcc version 4.0.3 and a compiler is not installed


If compiling a modem driver proves to be necessary, one of the two procedures must be followed.
If not yet on the Internet, put the Dapper install CD in the drive
Open a terminal and therein:
$ sudo apt-get install  gcc-4.0  make
Additionally the package linux-headers-2.6.15-26-386 must be downloaded.  
Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/)  and search for linux-headers-2.6.15-26-386 
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
	gcc-4.0 make linux-headers-2.6.15-26-386


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-07-05 09:00 /usr/sbin/pppd

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

---

### Post by kamalarora2kin on 2006-11-19
Hi 

now i got downloaded the driver file from this site:

[http://tx.technion.ac.il/~raindel/ess_2.6-v0.2.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.2.tar.gz)

i unzipped this file successfully on the desktop but unable to compile.

errors is: "no make command found"

suggest me.

---

