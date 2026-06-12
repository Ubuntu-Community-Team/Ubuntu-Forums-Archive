---
title: "EX2 IFS for windows"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-10-19
I was just wondering if anyone know of a program like EX2 IFS that will run with Vista.....I need it until i get my gusty up and running (still need to figure out winmodem and  HDA sound card).

Thank in advance for your help!

---

### Post by Sef on 2007-10-19
> ...still need to figure out winmodem....

Have you checked [Linmodems]("http://linmodems.org")?

---

### Post by natehatewindows on 2007-10-19
Yes i have, but little luck on getting it to work in 6.06 and i have not installed 7.10 yet....(wife is bringing it home from work or me :) because i only have dial up here in Ukraine :( ) I sent my modemdata.txt to the thread and they tol me to look at the conexant.txt.....tried to do that and it still does not work....im sure i will get it to someday. I have ubuntu on my other computer and never needed to configure a winmodem because i have broadband but thats back in the good old USA.....
Im hoping i guess when i put 7.10 on here it might make it a little easier to get my modem to work (even though im sure it wont its nice to dream :)

if you have any other tips here is what i got:

toshiba Satellite p-105

modemdata.txt:

 Only plain text email is forwarded by the  [email]DISCUSS@linmodems.org[/email] List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry  kernel 2.6.15-26-386 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) .
 Local Linux experts can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html)
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
 scanModem update of:  2007_Oct_09


 There are no blacklisted modem drivers in /etc/modprobe*  files 
USB modem not detected by lsusb


Advanced Linux Sound Architecture  (ALSA) spackage providing audio support 
on your System, also includes drivers for some modems. For modems using the 
snd-hda-intel  audio+modem driver, upgrades to a new ALSA version are sometimes 
necessary to achieve function. See for example:
      [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02144.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02144.html)
Copying ALSA diagnostics to Modem/ALSAroot.tgz
ALSAversion = 1.0.10

Modem or candidate host audio card have firmware information and diagnostics:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 0000:00:1b.0	8086:27d8	1179:ff31	0403: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 50:      53237   IO-APIC-level  HDA Intel
 --- Bootup diagnostics for card in PCI slot 0000:00:1b.0 ----
[17179593.096000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 50
[17179593.096000] PCI: Setting latency timer of device 0000:00:1b.0 to 64

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

  The High Defintion Audio card with PCI ID 8086:27d8 may host a soft modem chip.
 snd-hda-intel may not be competent to read /proc/asound/card0/codec*#1
 before 2.6.15 kernels, for HDA card 8086:27d8
Bootup diagnostics lack ALSA data.
 Modem not detected though HDA card diagnostics
 For candidate modem in PCI bus:  0000:00:1b.0
   Class 0403: 8086:27d8 0403: Intel Corporation 82801G
      Primary PCI_id  8086:27d8
    Subsystem PCI_id  1179:ff31 
    Softmodem codec or Vendor from diagnostics: 
                              from    Archives: 
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.0.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

 Already loaded into the kernel is snd-hda-intel and audio drivers it depends on,
 displayed by:	lsmod | grep snd_hda_intel
Module                  Size  Used by
-------------------------------------
snd_hda_intel          18964  4 
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm                89864  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    55268  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm


Writing Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read Conexant.txt

 Read Conexant.txt

Writing Conexant.txt

Writing Smartlink.txt
============ end Smartlink section =====================

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

 linux-headers-2.6.15-26-386 resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	gcc-4.0 make linux-headers-2.6.15-26-386


If a driver compilation files with message including some lack of some FileName.h (stdio.h for example. 
Some additional kernel-header files need installation to /usr/include.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:
$ sudo apt-get -s install linux-kernel-devel
While some of the files may be on the install CD, others may have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)

For Ubuntu Feisty, additional packages required were:
 libc6-dev linux-libc-dev
available through [http://packages.ubuntu.com/](http://packages.ubuntu.com/) , if not on the install CD.
Such packages may have different names for other Linux distributions.
Try installing just the libc6-dev, then test the compile again.


Checking pppd properties:
	-rwsr-xr-- 1 root dip 257720 2006-07-05 16:00 /usr/sbin/pppd

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

thanks for everything!!

have a great friday! :)

---

### Post by JackTrust on 2008-03-27
I did not take the time to read the extensive guides in the previous posts though I'm sure they are very helpful.
Though, when you run installer for the ex2 IFS program in Vista you must right click and go to properties and in the compatibility tab set the OS to Windows XP.  This, fixed the problem for me.

Thanks for reading and good luck.

---

### Post by stchman on 2008-03-27
> **natehatewindows said:**
> I was just wondering if anyone know of a program like EX2 IFS that will run with Vista.....I need it until i get my gusty up and running (still need to figure out winmodem and  HDA sound card).

Thank in advance for your help!

If you are wanting to access your EXT2/3 partitions from Windows use this.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

It works for both XP and Vista.  I triple boot and I can access my EXT3 partitions from Vista.

---

