---
title: "One more battle against Lucent Agere modem gained - Martian module"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by RJQ on 2007-07-30
After several months finally I could install the Martian module in Feisty (Kubuntu, not yet in Ubuntu but I suppose it may work equally) .
The previous conditions where like this: I was not able (and still) to extract the Martian folder, I believed my CD may be defective and the extracting tool does not work, also I could not compile the driver in any way (once I extracted the folder in my Dapper box and loaded in Feisty).

Solutions:
(Disclaimer: I am an absolute beginner, this is not a &#8220;how to&#8221;, this solutions are partial and may apply just to those who have the same situation, obviously there are some people who do not have to pass trough this trouble as we can see in some post related to the Martian drive, also I do not know if this information is already documented but I was never lucky enough to find it, finally the solution to this my own case focus on the simplest part this is the extraction, compilation and installation of the Drive, then I just follow the basic instructions, I really hope this steps can help some one in the same situation, in which I almost sure there is some defectiveness in the install CD plus some bugs)

Computer preconditions: If you have a windows system running you can right away know what type of modem you have under the modem information, yet the sacanmodem tool will give you some recommendations to follow, since I install Dapper I did not had any problem with the modem, following &#8220;Blastus How To&#8221;, I also receive  always the green light with the scanmodem but in Feisty things where not working, I new that my modem is somehow supported then I tray different approaches until I could make this thing work, for us the novices this is quite frustrating and many &#8220;How to&#8221; presume an Internet access which makes no sense if one is trying to make the only way possible for us (the dial up-ers) to get online, ...now knowing that the modem is supported and that some  people is getting the Martian module to work I tryed to find the problem and solve it (some how)

Steps to follow
Download the latest package ( I used martian-full-20061203.tar.gz)
extract the folder ( in my Kubuntu this is impossible and I have not figure it out why, what it actually happens is that the folder is extracted but with errors and corruptions then my solution to this is just extract the folder under my Dapper system)

In a &#8220;fresh&#8221; install of Kubuntu I add the live CD (Kubuntu 7.04) as a repository then I install the rest of the packages listed as &#8220;not installed&#8221; (exept bpalogin, drdsl, eagle-usb-data/utils, lunux-wlan-ng and mouseemu which after reading the description I knew I did not need them but some one else may want them installed)
I open the terminal and enter into the Martian folder ($ cd /home/rj/Desktop/martian-full-20061203.tar.gz_FILES) in my own case.

Then compile with ($ make all)

Now I change directory to the folder named kmodule and install ($ sudo make install)

Then and very important change again directory to the folder named modem and again install ($ sudo make install) for some reason I could not install from the main folder (Martian), the terminal just give a ('install' is up to date) or either I am just typing wrong and not making the command right but  at the end my approach works.

Now the insertion of the module ($ sudo modprobe martian_dev)

Make a symlink to find the modem ($ sudo ln -s /dev/ttySM0 /dev/modem)

And finally star the &#8220;Martian&#8221; ($ sudo martian_modem)

Next is the configuration of the dialer  but that is another and well documented story. This is what I have done to make the Martian and the Lucent Aegere modem work in Kubuntu 7.04 now i need to load it a boot time, there are more than one way apparently, I will post later which one works for me, once again I hope this may be helpful for someone else. :-({|=

---

### Post by feistyfirsttimer on 2007-07-30
Those goddamn Lucent winmodems are more trouble than they're worth.  I had a laptop that had one built-in.  I went through the whole rigmarole, scanModem, then downloading and compiling the "correct" driver... and it still didn't work.  Ubuntu acknowledged its existence, but claimed that the modem couldn't do anything.  So I just forgot about the thing, bought me a real modem for pennies.  Lucent's bad juju, man.  If they don't wanna play with Ubuntu, then *I* don't wanna play with *them*.  Life's too short to waste on them suckers.

---

### Post by legonum on 2007-09-24
Hello from a Totally new Feisty fawn,
( no Linux experience, no Unix history, truly an absolute beginner)

Many of us can not afford to go out and "buy me a real modem for pennies" and even if we could the "real modem" would do us no good, since a dial-up internet connection is our ONLY available option. This is why we need to be able to activate that "Bad juju"  win/lucent modem which has served us flawlessly during our Windows user phase. Should we really have to spend three months searching out obscure and confusingly conflicted information in our efforts to accomplish that? I don't think so.

---

### Post by ZeroShadow on 2007-11-05
That is true legonum, not all of us can easily access hardware, and/or go out and buy it. Linux for human beings, not linux for the rich and powerful.

---

### Post by RJQ on 2007-11-18
And the good news... are... si senhior it also works well for Ubuntu 7.10, actually little bit better since this time there is no need to do a separate "make installs" therefore we can skip one step.

:guitar: :popcorn:

---

### Post by pandan on 2007-11-21
**[SIZE="3"]I got my PCI Lucent Winmodem to work in Gutsy 7.10![/SIZE]**

**The Community Documentation is the place to start**
There is advice here to run scanmodem.
If it is a Lucent/Agere modem you can find out  where to load the Martian driver from at the bottom of the DialupModemHowto/Lucent page.
< I found that the "ltmodem" installation didn't work under Gutsy so tried Martian>

If you use the Scanmodem tool, it makes a file called AgereDSP.txt
I followed this exactly as root user (you can sudo every command from where it says switch (su) to root if you want) and I can now connect with SUDO WVDIAL.  There is one thing you probably shouldn't do which I've noted below.


In AgereDSP.txt, it tells ubuntu users to download and install "libc6-dev.deb"
Download it from: [http://packages.ubuntu.com](http://packages.ubuntu.com) from the folder "library development"
The website will tell you all it's dependencies (dependent packages). You need to download them too.
('recommends' and 'suggests' packages not necessary)
Do this on another computer that has a internet connection and put all the DEB files on a USB key.

Copy the Deb files to a folder on your ubuntu box.

From the terminal, change directory to that folder and issue the command:
sudo dpkg -i *.deb

Check that the installation has no errors or unresolved dependencies.

Now, you can try install the martian driver according to AgereDSP.txt
Remember: skip the following step in the howto:
>  To automate martian_modem action upon martian_dev loading,
 the following SINGLE line can be added to one of the files /etc/modprobe* 
 or to a new file /etc/modprobe.d/martian 
 install martian_dev  modprobe --ignore-install martian_dev ; /usr/sbin/martian_modem

 However, there is a report that (at least in some Systems), boot up processes
 are slowed. This is associated with bootup testing of potentially needed modules.
 Thus you may choose not to use this automation.
( I found that it stalls my boot and or had toI use a live cd to mount as root and undo the above)
Another way is to load martian_modem with sudo with each session by adding with the session control panel.
It will have to be added to the sudoers list with the NOPASSWD: qualifier.  Find out more with "man sudoers"
and edit the file with "sudo visudo"

< this is quite a hassle to do, but hey, you're getting valuable Linux experience in the process! >
< funny thing is, the same modem was heaps easier under 6.06 and 6.10! What happened?!>

Now if you want the **AgereDSP.txt **file I used, here it is.  However, it's better to get the latest scanmodem and use the one it generates.
>  Modems with Lucent/Agere DSP chipsets
 --------------------------------------
A detailed installation report is:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/MarsTest.txt](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/MarsTest.txt) 

 For Lucent/Agere/Xircom modems with DSP (digital signal processing) chipsets Apollo or Mars chip sets, 
LSI Inc. maintainer Soumyendu Sarkar provides occassional updates.
LSI Inc. [http://www.lsi.com/](http://www.lsi.com/), a descendant of Lucent through the former Agere Systems. This code includes a Closed Source component, ltmdmobj.o,  encrypting  copyrighted compression algorithms and other critical Proprietary code.
AMD x86_64  processors are supported, though only in 32 bit mode currently.

The Appolo/Mars support packages have had several variants over the years,
with Linmodems List volunteers contributing to a more friendly package. 
Initially there was only a unitary driver, later split into a ltmodem + ltserial driver pair.
Most recently the ltmdmobj.o has been shifted into a non-driver martian_modem by Alexie Chentsov,
leaving a residual Open Source martian_dev.ko  driver/module.
For Alexie's concept details see: [http://martian.barrelsoutofbond.org](http://martian.barrelsoutofbond.org)
These current packages are available at [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)
This support is robust into the 2.6.20 Linux kernels.

Brad House has reported a problem undering emerging 2.6.22 kernels
which he bypassed by shifting back to the older ltmodem + ltserial format.
See [http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02111.html](http://linmodems.technion.ac.il/bigarch/archive-seventh/msg02111.html)

Support packages for 2.6.13  kernels are at:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

For 2.6.12 and earlier kernels use a package in the folder [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/)

In addition to general compiling support, there may be needed
additional kernel_header files in /usr/include/  folders.  
For Debian and Ubuntu related Distros these are provided by the package libc6-dev. 
For Ubuntu, search for it at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install after download with:
$ sudo dpkg -i *.deb
For Fedora, the comparable packages (one to all of) have names like:
glibc-headers-2.3.5-10.i386.rpm
glibc-kernheaders-2.4-9.1.94.i386.rpm
glibc-devel-2.3.5-10.i386.rpm
which after download can be installed with:
# rpm -i glibc*.rpm
Do read the  package documentation carefully!!

Here is a detailed instruction set, assuming COMMANDs needing Admin permission are acquired through a preliminary:
$ su root
Ubuntu users would instead initiate such COMMANDs with:
$ sudo COMMAND
=========================================
Get the martian-full-20071011.tar.gz or more recent update from:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/martian/)

Under Linux:
$ tar zxf  mar*.tar.gz
$ cd  martian-full-20071011

Look around:
$ ls

$ make clean
$ make all
$ su root
# make install

for setup:
# modprobe martain_dev
you can get a report like that below with:
#  dmesg | grep martian
[ 4742.716000] martian loaded - 20071011
[ 4742.716000] "martian_dev": detaching 11c1:445 from serial
[ 4742.732000] "martian_dev": added device 11c1:445 BaseAddress =
0x2040, CommAddres = 0xd4c660ac, irq = 11

The martian_dev provides contact with the hardware.
But most of the COMM smarts are provided by the /usr/sbin/martian_modem. 
Merely test basic sanity with:
# martian_modem --help
# martian_modem --info countries
You can skip these two next time.

You can watch kernel messages with:
#  tail -f /var/log/messages &
The & tells tail to run in the background.
press  RETURN to get the COMMAND prompt back.

Now activate the modem with:
# martian_modem  --country=us
which reports:
 martian: info: Your port is /dev/ttySM0
"martian_dev": serving irqs in module
"martian_dev": martian_modem is attached.
-------
Leave martian_modem running, as it maintains the ports 
and does much of the COMM work!!

Open another Tab/console.  Look at the ports with
$ ls -l /dev/ttySM0 /dev/pts/*
crw--w---- 1 marv tty  136, 0 2007-09-23 22:27 /dev/pts/0
crw--w---- 1 root tty  136, 1 2007-09-23 22:27 /dev/pts/1
crw--w---- 1 marv tty  136, 2 2007-09-23 22:30 /dev/pts/2
lrwxrwxrwx 1 root root     10 2007-09-23 22:27 /dev/ttySM0 -> /dev/pts/1
-------
The ttySM0 is just a convient symbolic link for next steps.
The real and dynamically created /dev/pts/N port,
 that /dev/ttySM0 leads to may have a different N next session.

Next interrogate the modem hardware and start creating a dialout config file:
# wvdialconf  /etc/wvdial.conf
whose report should include:
--------
ttySM0<*1>: ATQ0 V1 E1 -- OK
ttySM0<*1>: ATQ0 V1 E1 Z -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySM0<*1>: Modem Identifier: ATI -- LT V.92 Data+Fax Modem Version 8.30
ttySM0<*1>: Speed 4800: AT -- OK
ttySM0<*1>: Speed 9600: AT -- OK
ttySM0<*1>: Speed 19200: AT -- OK
ttySM0<*1>: Speed 38400: AT -- OK
ttySM0<*1>: Speed 57600: AT -- OK
ttySM0<*1>: Speed 115200: AT -- OK
ttySM0<*1>: Speed 230400: AT -- OK
ttySM0<*1>: Speed 460800: AT -- OK
ttySM0<*1>: Max speed is 460800; that should be safe.
ttySM0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySM0.
--------

If the modem is thus found
# gedit  /etc/wvdial.conf
delete the  ;  and on those lines replace the <xxxx> with your personal info.
add a line:
 Carrier Check  =  no
for a final product like:
[Dialer Defaults]
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
# without - or spaces:
Phone = 1112223333
# when you need to go through a switchboard with say prefix 9, use a , to pause
# Phone = 9,,1112223333
ISDN = 0
Username = Your_Login_Name
Init1 = ATZ
Password = Your_Password
Modem = /dev/ttySM0
Baud = 460800
#  needed for  /dev/pts/N  ports:
Carrier Check  =  no
# see wvdial info for other options
### End wvdial.conf

Save and  and dialout with:
# wvdial
===========================
This ends the example.

 To automate martian_modem action upon martian_dev loading,
 the following SINGLE line can be added to one of the files /etc/modprobe* 
 or to a new file /etc/modprobe.d/martian 
 install martian_dev  modprobe --ignore-install martian_dev ; /usr/sbin/martian_modem

 However, there is a report that (at least in some Systems), boot up processes
 are slowed. This is associated with bootup testing of potentially needed modules.
 Thus you may choose not to use this automation.

	Support for the former  driver pair, ltmodem + ltserial terminates with 
 2.6.15 kernels. 
	 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
	Call waiting normally specified by, +pcw=1, is not implmented in the Linux drivers.
 	For older ISA card modems, specification of resources through forcing is
 sometimes necessary: [http://linmodems.technion.ac.il/archive-fifth/msg00055.html](http://linmodems.technion.ac.il/archive-fifth/msg00055.html) 

 The remainder of this section is historical info, awaiting a final edit.
------------------------------------------------------------------------

Support packages for 2.6.n kernels are at:
[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/) with folders for
	debian/  containing some installers
	ubuntu/  containing some installers
The ltmodem-8.26b1.tar.gz  and ltmodem-8.31b1.tar.gz are driver compiling resources,
with the 8.31 having support for SMP (symmetric multi processor) motherboards.
These packages are more automated versions of the ltmodem-2.6-alk* packages
The ltmodem-2.6-Nalk.src.rpm packages can be used with rpm using Distros.
	   # rpmbuild --rebuild ltmodem-2.6-Nalk.src.rpm  
	   will deposit an installer at:
	        /usr/src/rpm/RPMS//ltmodem-kv_2.6.17-11-386.rpm 	   Check with  
            # ls -l   /usr/src/rpm/RPMS//ltmodem*
	    Then install with:
	    # rpm -i /usr/src/rpm/RPMS//ltmodem-kv_2.6.17-11-386.rpm
	    or similar.

The martian.tar.gz represents a new developmental track, meeting emerging kernel requirements.
See for details:  [http://martian.barrelsoutofbond.org/](http://martian.barrelsoutofbond.org/)
[http://linmodems.technion.ac.il/archive-sixth/msg00142.html](http://linmodems.technion.ac.il/archive-sixth/msg00142.html)
AMD x86_64 competency is provided only bt the martian.

For 2.4.n kernels packages are at [http://ltmodem.heby.de/](http://ltmodem.heby.de/) or [http://phep2.technion.ac.il/linmodems/packages/ltmodem/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/)

 There are some installer packages and also resources for compiling drivers.
 ----------------------
 SuSE/Novell Linux and some other Distros provide compiled drivers +installers.
    Search package lists for ltmodem  
 For other Distros and 2.6.n kernels, see: 

 Packages for compiling drivers are:
 ResourceName                Use for kernel ranges
--------------------------------------------------------------------------------
ltmodem-8.26a.tar.gz         2.4.21 and earlier
ltmodem-8.30a3.tar.gz        2.4.21 and subsequent 2.4.2n kernels
	    which were assembled with a gcc-2.9 comiler
ltmodem-8.31a10.tar.gz     beginning with 2.4.21 and upto about 2.6.8  kernels
martian.tar.gz             2.6.n SMP (symmetic multiprocessor) support not verified.
ltmodem-8.31b1.tar.gz      2.6.n with    SMP support, for some* Systems
ltmodem-8.26b1tar.gz       2.6.n without SMP support
   * While SMP capacity should in principle be without ill effect on single processor systems,
the are some cases of ill effects on single processor systems.

Some additional 2.4.n installers are available from:
[http://dag.wieers.com/packages/kernel-module-ltmodem/](http://dag.wieers.com/packages/kernel-module-ltmodem/) for some other 2.4.n installers.



---

### Post by RJQ on 2007-11-22
> **pandan said:**
> **[SIZE="3"]I got my PCI Lucent Winmodem to work in Gutsy 7.10![/SIZE]**

**The Community Documentation is the place to start**
There is advice here to run scanmodem.
If it is a Lucent/Agere modem you can find out  where to load the Martian driver from at the bottom of the DialupModemHowto/Lucent page.
< I found that the "ltmodem" installation didn't work under Gutsy so tried Martian>

If you use the Scanmodem tool, it makes a file called AgereDSP.txt
I followed this exactly as root user (you can sudo every command from where it says switch (su) to root if you want) and I can now connect with SUDO WVDIAL.  There is one thing you probably shouldn't do which I've noted below.


In AgereDSP.txt, it tells ubuntu users to download and install "libc6-dev.deb"
Download it from: [http://packages.ubuntu.com](http://packages.ubuntu.com) from the folder "library development"
The website will tell you all it's dependencies (dependent packages). You need to download them too.
('recommends' and 'suggests' packages not necessary)
Do this on another computer that has a internet connection and put all the DEB files on a USB key.

Copy the Deb files to a folder on your ubuntu box....


Hey that is good news, that more and more people are getting this thing to work, about the "libc6-dev.deb" and other packages, they are actually in the CD, you do not need to download them, just put your CD in and star synaptic as I explain in my first post little bit above. you just need the martian source and the scanmodem if you do not know your modem, in a computer with windows in it, the information shall be there.

congrats PANDAN this should inspire more people to try Ubuntu.

---

### Post by RJQ on 2008-05-23
This method also works with Hardy Heron, I put toghether a little tutorial in [this thread]("http://ubuntuforums.org/showthread.php?t=804378"). hope it help.

---

