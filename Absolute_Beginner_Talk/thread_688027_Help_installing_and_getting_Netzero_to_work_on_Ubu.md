---
title: "Help installing and getting Netzero to work on Ubuntu"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by soccerislife8 on 2008-02-04
I'm relatively new to linux and ubuntu and i was wondering if there was a way to install netzero on ubuntu. I downloaded the .deb file from netzero.com and installed it. after running the /opt/nzclient/runclient.sh in the terminal it said "DM set to off." does anyone have any solutions for netzero on ubuntu?

---

### Post by LowSky on 2008-02-05
seems this might help, figure I should give credit where it is due

> **darthchaosofrspw said:**
> You need to try to get the Netzero debian file and install it like this :

sudo dpkg -i netzero.deb

The next step is VERY important. In order to get the NetZero dialer software to work with Ubuntu, you MUST use the Synaptic Package Manager or apt-get to download and install the Java 2 Runtime Environment (j2re). The NetZero software depends on j2re. Without j2re, the NetZero dialer will NOT work. To download j2re, you have to enable the Multiverse repositories which are listed at [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) and then once the apt sources are updated, you can download and install j2re...easiest way is to use Synaptic Package Manager and search for anything that has j2re.



Then you need to make a link on your desktop to the NetZero dialer. For this, you need to have the NetZero shortcut point to the following command :

sudo bash /opt/nzclient/runclient.sh

If that doesn't work, try running "sudo bash /opt/nzclient/runclient.sh" in a terminal window. It should work.

---

### Post by soccerislife8 on 2008-02-05
Thanks for the reply. Since Netzero is my ISP i currently can only get onto the internet on Windows so i downloaded a .bin file from the Java website. do you think that it would work? it is called jre-1_5_0_14-linux-i586.bin and it installs okay but i still get "DM set to off"

---

### Post by Shazaam on 2008-02-05
What type of dialup modem are you using? Depending on the type drivers for it COULD be free.
Go here........
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

BTW, you don't absolutely need the NetZero software to connect with linux. Unless you like the ugly panel they use:)

---

### Post by soccerislife8 on 2008-02-05
Can you post a link to a guide on how i can connect to the internet on Ubuntu without the netzero software?

---

### Post by Shazaam on 2008-02-05
> **soccerislife8 said:**
> Can you post a link to a guide on how i can connect to the internet on Ubuntu without the netzero software?

Do you have the drivers installed for your modem? Some types are automatically recognized by Ubuntu. What version Of Ubuntu are you running?

---

### Post by Shazaam on 2008-02-05
Also if you are running Gutsy go to Applications>Internet and see if gnome-ppp is there. If it is open it and enter your NetZero info.

---

### Post by soccerislife8 on 2008-02-05
I'm running Gutsy Gibbon 7.10. Is there a way to connect to netzero without using their software? How can i tell if my modem is installed?

---

### Post by Shazaam on 2008-02-05
Did you look for gnome-ppp per my previous post?

---

### Post by soccerislife8 on 2008-02-05
gnome-ppp is not installed on my system.

---

### Post by Shazaam on 2008-02-05
Go here-
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
then here....
[https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem)
Post back with the results of the scanmodem tool.

---

### Post by soccerislife8 on 2008-02-05
Which text file should i post?

---

### Post by Shazaam on 2008-02-05
Sorry about that. It will be listed in ModemData.txt (your modem) or scanout.txt

---

### Post by soccerislife8 on 2008-02-05
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007
 scanModem update of:  2008_11_01


 There are no blacklisted modem drivers in /etc/modprobe*  files 
USB modem not detected by lsusb

For candidate card in slot 00:1e.3, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1e.3	8086:266d	103c:3082	Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW 

 Modem interrupt assignment and sharing: 
 18:       2492          0   IO-APIC-fasteoi   Intel ICH6
 --- Bootup diagnostics for card in PCI slot 00:1e.3 ----
[   16.533391] ACPI: PCI Interrupt 0000:00:1e.3[A] -> GSI 22 (level, low) -> IRQ 18
[   16.533400] ACPI: PCI interrupt for device 0000:00:1e.3 disabled

 The PCI slot 00:1e.3 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===



 For candidate modem in PCI bus:  00:1e.3
   Class 0703: 8086:266d Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW
      Primary PCI_id  8086:266d
    Subsystem PCI_id  103c:3082 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: CXT, a Conexant type using hsfmodem software.
      CXT is  a generic for all CXTnumbers, with  Linuxant hsfmodem software support.                  

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	hsfmodem


Writing Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

 The hsfmodem package serves a great variety of Conexant chipset modems. 
 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem_VersionSpec_k2.6.22_14_generic_ubuntu_i386.deb.zip 
                           with 2.6.22_14_generic equivalent to 2.6.22-14-generic, your kernel version.
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See Testing.txt  for details.
 
 Read Conexant.txt

Writing Conexant.txt


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.3
             and the compiler used in kernel assembly: 4.1.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.22-14-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-04 12:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

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

### Post by Shazaam on 2008-02-05
Much better. I was hoping Dell had updated support for Gutsy for their free drivers but they haven't yet. Try a search of the forums for your driver or go to-

[http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)

and download a HSFmodem driver. The free version is crippled at 14.4; the pay version is full speed. Yes they do have a lot of dialup users over a barrel but since you have a Conexant chipset (me too) there isn't much to do about it. We can end this here if you plan on getting broadband or you can stick it out and see what happens.

What I HIGHLY suggest if you feel the need to throw money at linuxant for drivers is that you go to a place like ebay or newegg.com and purchase an external (serial or ethernet) dialup modem. You can find decent ones for a reasonable price and you don't need to worry about drivers. Stay away from the USB type as you will end up in the same boat as you are now.

---

### Post by soccerislife8 on 2008-02-05
Thank you for all of your help Shazaam. I think i will stick it out with what i have. Thanks for the info.

---

