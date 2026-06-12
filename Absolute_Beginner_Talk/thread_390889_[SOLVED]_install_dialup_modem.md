---
title: "[SOLVED] install dialup modem"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by Stan% on 2007-03-22
Hi Folks,

My name is Stan. I'm completely new to Linux and this is my first post here.

I have an OEM system running Win 98 SE I recently dual booted with Ubuntu.

The system had a US Robotics dialup modem, not supported, so I bought a new SmartLink Modem that works with Windows and Linux. Well, the seller says it works with Redhat, SuSe, and Mandrake and should work with other distros too.

The new modem is installed and setup in Windows and works fine. Unfortunately, I'm so new to Linux I can't figure out how to install and set it up in Ubuntu.

Any help with this will be greatly appreciated.



If you know any good sites covering 'working in terminal mode' please post the links.

Thanks Stan,

The following is from the readme file on the CD that came with the modem, maybe it will be helpful.

Smart Link Ltd.
[http://www.smlink.com](http://www.smlink.com)
Apr 12, 2002


Smart Link Soft Modem for Linux
-------------------------------Smart Link Ltd.
[http://www.smlink.com](http://www.smlink.com)
Apr 12, 2002


Smart Link Soft Modem for Linux
-------------------------------


Introduction
============

This is Smart Link Soft Modem for Linux version 2.X. It provides
full-featured 56K Voice Fax Modem.


Features
========

Modem: V.92, V.90, V.34, V.32bis, V.23, V.22, V.21, Bell 103/212.
Flow control: V.42, MNP 2-4.
Compression: V.44, V.42bis, MNP5.
Fax: Class 1.
Voice: ADPCM voice compression, Digital Answering Machine.


Requirements
============

CPU: Intel Pentium II, Celron. AMD K6, Cyrix 400MHz or higher.
Memory: 64MB (may work also with 32MB).
OS: Linux 2.4 series.


Supported Hardware
==================

HAMR5600 based AMR/CNR/MDC/ACR modem cards on the following Southbridge
chips:
- Intel ICH0, ICH2
- Via 686A, 686B, 8231, 8233
- SiS 630
- ALI 1535.
SmartPCI56/561/562/563 based PCI modem cards.
SmartUSB56 based USB modem.


Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmdm-2.X.X.tar.gz | tar xf -

2. 'cd' to package directory:

	$ cd slmdm-2.X.X

3. Review and edit (if need) 'Makefile'.

   Note: Probably you will want to correct in Makefile path to your
         local linux kernel header files:

         	KERNEL_INCLUDES=/path/to/linux/include

         Another way is to pass command line the parameter while
         running 'make':

         	$ make KERNEL_INCLUDES=/path/to/linux/include ...

4. Run 'make' command to compile package:

	$ make

5. Install.

   If you are going to use AMR/CNR/PCI modem type (as superuser):

	# make install-amr

   , or 

	# make install-usb

   if you are going to use USB modem.

   It will install:
   - modem kernel modules slmdm.o (modem core), slfax.o (fax)
     into '/lib/modules/<kernel-version>/misc' directory
     (standard linux modules' directory).
   - hardware specific kernel module slamrmo.o (for AMR/CNR/PCI) or
     slusb.o (for USB) into '/lib/modules/<kernel-version>/misc'
     directory (standard linux modules' directory).
   - country settings data file 'country.dat' into directory '/etc'.

   Also it will:
   - create character tty device entry '/dev/ttySL0' with major
     number 212 and symbolic link 'dev/modem'.
   - config you '/etc/modules.conf' file in order to provide
     possibility for loading the modem modules into kernel on demand
     automatically by kmod, when you are going to use them.

   Note: currently you cannot use both AMR/CNR/PCI and USB Modems.

6. Config modem country.

   You can configure your current country by using module parameters
   'country' or 'country_code'.
   Add 'options' directive line to file '/etc/modules.conf':

	options slmdm country=<MyCountry>

   , for example

	options slmdm country=USA

   , or use module parameter while module loading:

	# modprobe slmdm country=<MyCountry>

   Use 'slver -c' to see list of all supported countries and their
   codes (utility 'slver' may be found in package directory).

   Note: Command ATI7 shows installed country setting.

7. Using the modem.

   Installation will automatically create character tty device entry
   '/dev/ttySL0' with major number 212 and symbolic link '/dev/modem'.
   Use one of them as modem device for your dialing application.

8. Uninstallation.

   In package directory just type:

	# make uninstall


Using RPM
=========

1. Build SRPM and RPM from tar.gz package:

   In order to build RPM and SRPM run command:

	# rpm -ta slmdm-2.X.X.tar.gz

   It will build in your RPM directory:
   - slmdm-2.X.X-Y.src.rpm       - Source SRPM package
   - slmdm-2.X.X-Y.i386.rpm      - Core Modem RPM package
   - slmdm-amr-2.X.X-Y.i386.rpm  - AMR/CNR/PCI Modem driver
   - slmdm-usb-2.X.X-Y.i386.rpm  - USB Modem driver

2. Install

   To install Modem core package run:

	# rpm -i /path/to/slmdm-2.X.X-Y.i386.rpm

   To install Modem hw driver run:

	# rpm -i /path/to/slmdm-amr-2.X.X-Y.i386.rpm

   if you are going to use AMR/CNR/PCI Modem, or

	# rpm -i /path/to/slmdm-usb-2.X.X-Y.i386.rpm

   if you are going to use SmartUSB56 Modem.

   Note: currently you cannot install and use both AMR/CNR/PCI and USB Modems.

3. Uninstall.

	# rpm -e slmdm slmdm-<amr|usb>


Getting Started
===============

After successful installation and configuration modules will be loaded on
demand if you are using 'kmod' in linux kernel.

Also you can load modules by hand:

	# modprobe slamrmo

if you are using AMR/CNR/PCI modem, or

	# modprobe slusb

if you are using SmartUSB56 Modem.


Troubleshooting
===============

If you get an error message during installation/configuration or loading
the modules try to see it in FAQ file.

Please report the problem to your modem provider or to us
(support@smlink.com). 


Customization
=============

Look at 'editme.c' file in package directory.


Feedback
========

Please send any feedbacks to Smart Link. See the Smart Link
web site for contact information ([www.smlink.com](www.smlink.com)) or to
[email]support@smlink.com[/email].

---

### Post by dstew on 2007-03-22
It looks like your SmartLink modem comes with a kernel module (driver) that will need to be compiled. There are some problems I see. One, it says "OS Linux 2.4 series". That is worrisome. It may mean that the module will not work with 2.6.X kernels, which is what you have. The date, I see, is 2002, which is consistent with the 2.4.x kernels.

The second problem, is that compiling is tricky. You need to have installed in your filesystem the compiler package, build-essentials, and change the files in the module package to point to the correct header files.

My suggestion is first read this:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

It will direct you to more useful, modern kernel modules. It is possible that one is already compiled for you. Note, you will need to install and run the ScanModem program to find out exactly what to do, but this is not difficult.

---

### Post by Bachstelze on 2007-03-22
```
sudo apt-get install sl-modem-daemon
```

should be enough, then run

```
sudo wvdialconf /etc/wvdial.conf
```

and paste what you get.

---

### Post by Stan% on 2007-03-22
dstew,

Yes, I noticed the 2.4.x series. The modem only cost 10.00. I'll give it a shot. I'll see what I can learn from your link.



HymnToLife,

Results of your first command: "couldn't find package sl-modem-daemon"

Results of second command: "command not found"

If apt-get downloads from the internet, I can't get on internet in Ubuntu, only in Windows.

Thanks,
Stan

---

### Post by cowlip on 2007-03-22
You can download Ubuntu packages here:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sl-modem-daemon&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=sl-modem-daemon&searchon=names&subword=1&version=edgy&release=all)

So download them from Windows, mount the hard drives in ubuntu (if it's an ntfs file system, you could use ntfs-3g and ntfs-config to mount it with a GUI), and double click on the deb files.

---

### Post by equability on 2007-03-23
Ciao Stan.

Wich Ubuntu do you use?

What did your Device Manager say?

Look at /etc/ (cd /etc or browse) wether there is a file named wvdial.conf or not).
If there is, the command 'sudo wvdialconf /etc/wvdial.conf' works well.

---

### Post by _duncan_ on 2007-03-23
Click on the 3rd link on my signature (Conexant and Smartlink Modem How-To). There is a section explaining the steps to compile the open-source smartlink driver. This should work for 2.6.xx kernels.

The 2nd link (Dial-Up Modem Wiki) is also useful once you have successfully compiled the driver. It provides ways to configure various dialer programs.

---

### Post by Stan% on 2007-03-24
> **equability said:**
> Ciao Stan.

Wich Ubuntu do you use?  

6.10 Edgy 

What did your Device Manager say?

What should I look for? What do you want to know?

Look at /etc/ (cd /etc or browse) wether there is a file named wvdial.conf or not).
If there is, the command 'sudo wvdialconf /etc/wvdial.conf' works well.

wvdiat.conf is there. What will your command do?

---

### Post by yaye on 2007-03-24
If the instructions from others don't work and you get tired of trying to get an internal PCI modem to work, try an external modem that connects to the computer via a serial port (not USB).  An external serial port modem should work with just about any OS, even DOS.

---

### Post by Bachstelze on 2007-03-24
Stan% : then, what happens when yo do this ?

```
sudo wvdial
``` Ç

---

### Post by Stan% on 2007-03-24
> **_duncan_ said:**
> Click on the 3rd link on my signature (Conexant and Smartlink Modem How-To). There is a section explaining the steps to compile the open-source smartlink driver. This should work for 2.6.xx kernels.

The 2nd link (Dial-Up Modem Wiki) is also useful once you have successfully compiled the driver. It provides ways to configure various dialer programs.


Results of lspci and lspci -n........

stan@Gateway:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0e.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
00:0f.0 Mass storage controller: Promise Technology, Inc. PDC20262 (FastTrak66/Ultra66) (rev 01)
00:10.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
stan@Gateway:~$ lspci -n
00:00.0 0600: 8086:7190 (rev 03)
00:01.0 0604: 8086:7191 (rev 03)
00:07.0 0601: 8086:7110 (rev 02)
00:07.1 0101: 8086:7111 (rev 01)
00:07.2 0c03: 8086:7112 (rev 01)
00:07.3 0680: 8086:7113 (rev 02)
00:0e.0 0401: 1102:0002 (rev 07)
00:0e.1 0980: 1102:7002 (rev 07)
00:0f.0 0180: 105a:4d38 (rev 01)
00:10.0 0703: 163c:3052 (rev 03)
01:00.0 0300: 10de:002d (rev 15)

---

### Post by Stan% on 2007-03-24
> **HymnToLife said:**
> Stan% : then, what happens when yo do this ?

```
sudo wvdial
``` Ç

Cannot open  /dev/modem: no such file or drectory.

---

### Post by Stan% on 2007-03-24
> **yaye said:**
> If the instructions from others don't work and you get tired of trying to get an internal PCI modem to work, try an external modem that connects to the computer via a serial port (not USB).  An external serial port modem should work with just about any OS, even DOS.

Thanks for the other option. It may end up that way but I installed Linux to learn something new so I'll try to work this out first. BTW the computer I'm using is an older one I keep just for learning on.

---

### Post by equability on 2007-03-24
> **Stan% said:**
> wvdiat.conf is there. What will your command do?

Ciao Stan.

This command tries to find the modem, read the working information of the modem (connect port -> eg. ttyS2, speed, etc.) and tries to configure it (write the information into the file wvdial.conf). That's all.

If the command doesn't find the modem, nothing happens (and there are no written information in the file).

Try it.

---

### Post by Stan% on 2007-03-24
> **equability said:**
> Ciao Stan.

This command tries to find the modem, read the working information of the modem (connect port -> eg. ttyS2, speed, etc.) and tries to configure it (write the information into the file wvdial.conf). That's all.

If the command doesn't find the modem, nothing happens (and there are no written information in the file).

Try it.

No modem was detected.

---

### Post by equability on 2007-03-24
> **Stan% said:**
> No modem was detected.

Ciao Stan.

Seems, it's one of these modems, Linux cannot handle or/and there might be no current driver for it. Sorry.

Try to use an external modem or buy a Linux compatible internal modem.

---

### Post by Bachstelze on 2007-03-24
Stan% > did you *apt-get install sl-modem-daemon* ?

---

### Post by Stan% on 2007-03-24
> **HymnToLife said:**
> Stan% > did you *apt-get install sl-modem-daemon* ?

No, I have not apt-get anything. I have a second Windows XP system which has both floppy drive and CD burner. I think there are at least several downloads I will need. If you can give me a list I'll get them.

---

### Post by Bachstelze on 2007-03-24
Well, the package contains the driver for your modem so if you haven't installed it, it's normal it isn't detected. You can download the DEB file from [http://packages.ubuntu.com](http://packages.ubuntu.com) . So download it from your Win system, copy it somewhere on your Ubuntu and run :

```
sudo dpkg -i /path/to/file.deb
```

It might possibly complain about other packages being needed, install them the same way.

---

### Post by Stan% on 2007-03-24
> **HymnToLife said:**
> Well, the package contains the driver for your modem so if you haven't installed it, it's normal it isn't detected. You can download the DEB file from [http://packages.ubuntu.com](http://packages.ubuntu.com) . So download it from your Win system, copy it somewhere on your Ubuntu and run :

```
sudo dpkg -i /path/to/file.deb
```

It might possibly complain about other packages being needed, install them the same way.

Results:

stan@Gateway:~$ sudo dpkg -i /home/stan/Desktop/untitled folder/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb
dpkg: error processing /home/stan/Desktop/untitled (--install):
 cannot access archive: No such file or directory
dpkg: error processing folder/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/stan/Desktop/untitled
 folder/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb



stan@Gateway:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS2<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS2<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS3<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS3<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS3<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.

---

### Post by Mark_in_Hollywood on 2007-03-24
I'm assuming you have an internal pci yet controller based (hardware based) modem. I had the exact same problem(s).

I could get the modem online but only for indefinite periods of time.

I believe the problem is caused by Microsoft having, originally, only 4 COM ports and using only 2 IRQs. The firmware in your modem is probably trying to install itself on COM 5. Linux has a ttyS5, but isn't happy with finding an IRQ to use.

I did EVERYTHING I could to get the ActionTec PM560LKi internal and Linux supported modem to work. If you want to find what I've done with it, use the search feature at this forum for Mark_in_Hollywood and the keyword modem: that will get you started.

Meanwhile I found a Creative ModemBlaster flash56 and it's smokin'. Fired right up after sudo wvdialconf /etc/wvdial.conf

Let me know if this helps. But I'm neither a programmer nor a Linux expert, like most of the guys here.

---

### Post by Bachstelze on 2007-03-24
The first command, which is the package installation, throws an error : the file you typed does not exist. The reason why you get that is that you have a space in the dir name, so when you type 

```
sudo dpkg -i /home/stan/Desktop/untitled folder/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb
```

you tell *dpkg* to install */home/stan/Desktop/untitled* and *folder/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb*, as two different files, it's like typing

```
sudo dpkg -i file1.deb file2.deb
```

To make the shell understand the space is part of the path, put a **back**slash before it, like this :

```
sudo dpkg -i /home/stan/Desktop/untitled\ folder/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb
```

And in the future, please avoid using spaces in files or directories names to avoid such mistakes, or you could reget it very badly.

---

### Post by equability on 2007-03-24
Ciao mi amici.

Please do me a favour.

Can someone post an original wvdial.conf (or the content)?

That would be very nice.

Thank you for your trouble.

---

### Post by Bachstelze on 2007-03-24
That depends on your modem. You can run *wvdialconf* again to generate a new one.

---

### Post by equability on 2007-03-24
> **HymnToLife said:**
> That depends on your modem. You can run *wvdialconf* again to generate a new one.

O.K. Thanks. That the information I am looking for.

Great.

---

### Post by yaye on 2007-03-25
> **Stan% said:**
> Thanks for the other option. It may end up that way but I installed Linux to learn something new so I'll try to work this out first. BTW the computer I'm using is an older one I keep just for learning on.

I started using Linux with an AMD 486 DX4 - 120 MHz based computer.  I would connect to the Internet with an ISA based modem.  During the time I used modems, I always used ISA hardware based modems where I could set the com port and irq manually via jumpers on the card.  I specifically avoided jumperless, Winmodems because they were designed to work primarily with Windows and not other operating systems.

When I saw your post, I realised that you may have a great deal of trouble getting the PCI modem to work.  If you are willing to spend the time and energy getting it to work, great.  If you are not successful, your best options are:

- if that older computer has ISA slots, get an ISA hardware (controller) based internal modem with jumpers to set com port and irq

- an external modem that connects to the computer via a serial port

Either way, Good Luck.

(Our oldest computer is an Intel Pentium 100 Mhz based clone running DSL Linux)  :D

---

### Post by Bachstelze on 2007-03-25
I have a 66 MHz with 16 MB of RAM running OpenBSD here.

Mine is smaller than yours :D

---

### Post by yaye on 2007-03-25
> **HymnToLife said:**
> I have a 66 MHz with 16 MB of RAM running OpenBSD here.

Mine is smaller than yours :D

:D

---

### Post by Stan% on 2007-03-25
HymnToLife,

You're right about the space after "untitled". We made some progress:

stan@Gateway:~$ sudo dpkg -i /home/stan/Desktop/untitled\ folder/sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb
Password:
(Reading database ... 88041 files and directories currently installed.)
Preparing to replace sl-modem-daemon 2.9.10+2.9.9d+e-pre2-5build1 (using .../sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb) ...
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Unloading modem driver from kernel ... snd_atiixp_modem.
Unpacking replacement sl-modem-daemon ...
Setting up sl-modem-daemon (2.9.10+2.9.9d+e-pre2-5build1) ...
FATAL: Module ungrab_winmodem not found.
FATAL: Module slamr not found.
Starting SmartLink Modem driver for: auto.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

stan@Gateway:~$ sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS1<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS1<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS1<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
ttyS2<*1>: ATQ0 V1 E1 -- 

The terminal window hangs here (not the whole computer) with a blinking curser. Windows tells me the device is using Comm 3. Seems I read somewhere that Comm 3 would equate to ttyS2.



Mark_in_Hollywood,

Thanks, I'll take a look at your thread.



Yaye,

Thanks for the info, I may need it. The system does have one ISA slot. (empty)

---

### Post by Bachstelze on 2007-03-25
Stan% : All right, you'll also need to compile the kernel module for your modem. Install the package sl-modem-source the same way you installe dsl-modem-daemon earlier, then do :

```
sudo module-assistant auto-install sl-modem
sudo depmod -a
sudo nano /etc/default/sl-modem-daemon
```

edit the COUNTRY line to match the country you're in and finally, do

```
sudo modprobe slamr
sudo /etc/init.d/sl-modem-daemon restart
```

Now you should be fine.

---

### Post by Stan% on 2007-03-25
Sorry HymnToLife, we're not quite there yet. I have sl-modem-source on a floopy, double click the file, it installs and I get:

Error: Dependancy is not satisfiable: module-assistant.

---

### Post by Stan% on 2007-03-25
Everyone hang on, I'm installing other packages.

---

### Post by Stan% on 2007-03-25
I need:

 devhelper
html2txt
dpkg-dev


When installing these,from the floppy, it recommends I install the same versions from a software channel. What does that mean?

---

### Post by Bachstelze on 2007-03-25
Dunno, never seen something like this. Could you please paste the exact output of the command ?

---

### Post by Stan% on 2007-03-25
After reading the file and before I am able to click "Install Package", a second window opens. The window has a lightbulb icon and says:

"Same Version is available in a software channel
You are recommended to install the software from the channel instead."

Then there is a close box at the bottem.

Is there a way to send a screen shot? If you need it.

---

### Post by Bachstelze on 2007-03-25
Just install from the CLI with *sudo dpkg -i*...

---

### Post by Stan% on 2007-03-25
After running sudo module-assistant...

"Installation of sl-modem-source source failed.

Ignoring this package. Maybe you need to add something to sources.list, maybe the contriband non-free archives."

---

### Post by Bachstelze on 2007-03-25
```
dpkg -l | grep sl-modem
```

Does sl-modem-source appear in the list ? If not, it is not installed, install it :)

---

### Post by Stan% on 2007-03-25
Installed sl-modem-source. Ran the first command again, got another error. here is the module-assistant log file:

                                                                              
 â&#8221;&#338;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;¤ module-assistant, log file viewer â&#8221;&#339;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221; 
 â&#8221;&#8218;                                                                            â&#8221;&#8218; 
 â&#8221;&#8218; dh_testdir                                                                 â&#8224;&#8216; 
 â&#8221;&#8218; dh_testroot                                                                â&#8211;® 
 â&#8221;&#8218; rm -f build-arch-stamp build-indep-stamp configure-stamp                   â&#8211;&#8217; 
 â&#8221;&#8218; # Add here commands to clean up after the build process.                   â&#8211;&#8217; 
 â&#8221;&#8218; /usr/bin/make clean SUPPORT_ALSA=1                                         â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Entering directory `/usr/src/modules/sl-modem'                    â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Leaving directory `/usr/src/modules/sl-modem'                     â&#8211;&#8217; 
 â&#8221;&#8218; cd modem; /usr/bin/make clean SUPPORT_ALSA=1                               â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Entering directory `/usr/src/modules/sl-modem/modem'              â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'               â&#8211;&#8217; 
 â&#8221;&#8218; dh_clean                                                                   â&#8211;&#8217; 
 â&#8221;&#8218; /usr/bin/make -C drivers clean                                             â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'            â&#8211;&#8217; 
 â&#8221;&#8218; rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o               â&#8211;&#8217; 
 â&#8221;&#8218; amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~                                â&#8224;&#8220; 
 â&#8221;&#8218;                                                                              
 â&#8221;&#8218;                                   <Ok>      


Sorry, I have some other chores to do. I'll get back to this ASAP.

---

### Post by Stan% on 2007-03-25
any response to the log file?

---

### Post by Bachstelze on 2007-03-25
Could you paste the error you get ?

---

### Post by Stan% on 2007-03-25
When I run: sudo module-assistant auto-install sl-modem: some of the build is completed but then the terminal changes to a grey window inside a blue background and the words:

                               module-assistent, interactive mode

Build of the package slmodem failed! How do you wish to proceed?


   View        Examine the build log file
   Continue   Skip and continue with the next operation
   Stop         Stop processing the buid commands

Using arrow keys I can choose any of the three options. If I choose View I get the following:

                                                                              
 â&#8221;&#338;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;¤ module-assistant, log file viewer â&#8221;&#339;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221;&#8364;â&#8221; 
 â&#8221;&#8218;                                                                            â&#8221;&#8218; 
 â&#8221;&#8218; dh_testdir                                                                 â&#8224;&#8216; 
 â&#8221;&#8218; dh_testroot                                                                â&#8211;® 
 â&#8221;&#8218; rm -f build-arch-stamp build-indep-stamp configure-stamp                   â&#8211;&#8217; 
 â&#8221;&#8218; # Add here commands to clean up after the build process.                   â&#8211;&#8217; 
 â&#8221;&#8218; /usr/bin/make clean SUPPORT_ALSA=1                                         â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Entering directory `/usr/src/modules/sl-modem'                    â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Leaving directory `/usr/src/modules/sl-modem'                     â&#8211;&#8217; 
 â&#8221;&#8218; cd modem; /usr/bin/make clean SUPPORT_ALSA=1                               â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Entering directory `/usr/src/modules/sl-modem/modem'              â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'               â&#8211;&#8217; 
 â&#8221;&#8218; dh_clean                                                                   â&#8211;&#8217; 
 â&#8221;&#8218; /usr/bin/make -C drivers clean                                             â&#8211;&#8217; 
 â&#8221;&#8218; make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'            â&#8211;&#8217; 
 â&#8221;&#8218; rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o               â&#8211;&#8217; 
 â&#8221;&#8218; amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~                                â&#8224;&#8220; 
 â&#8221;&#8218;                                                                              
 â&#8221;&#8218;                                   <Ok>      

The wierd 'a' symbols you see here are not on the terminal.

---

### Post by Bachstelze on 2007-03-25
According to the Wiki, you might need to install GCC 3.4, maybe it will help...

[https://help.ubuntu.com/community/DialupModemHowto/FromSource](https://help.ubuntu.com/community/DialupModemHowto/FromSource)

---

### Post by Stan% on 2007-03-25
During the build ,or at sometime, I read part of the message on the terminl that said:

Suggested Packages:
GCC-4.1-doc
lib64stdc++6glibc-doc
manpages-dev
libstdc++6-4.1-doc

Need to get 0b/7821 kb of archives

---

### Post by Bachstelze on 2007-03-25
Suggested packages are just suggested, not mandatory. Not having them should not make the build fail. Anyway, try to follow all the steps there, you maybe missed something :

[https://help.ubuntu.com/community/DialupModemHowto/Smartlink](https://help.ubuntu.com/community/DialupModemHowto/Smartlink)

---

### Post by Stan% on 2007-03-25
I installed GCC3.4 The terminal told me to run another command (sorry didn't write it down). I guess it updated the GCC 3.4 file to GCC 3.4.6. Then I tried to install cpp-3.4 and it said I need Gcc 3.4. tried to reinstall Gcc3.4 and it tells me "a later version is all ready installed". So I can't install any of the other three files from : [https://help.ubuntu.com/community/DialupModemHowto/FromSource](https://help.ubuntu.com/community/DialupModemHowto/FromSource)

---

### Post by Stan% on 2007-03-25
The command I ran after installing gcc-3.4-base_3.4.4-6ubuntu8_i386.deb was 
sudo apt-get install -f

I think I now have : gcc-3.4-base_3.4.6-3ubuntu1_i386.deb

Terminal results:

stan@Gateway:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gcc-3.4 cpp-3.4
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  cpp-3.4 gcc-3.4
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 8495kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 90173 files and directories currently installed.)
Removing gcc-3.4 ...
Removing cpp-3.4 ...
stan@Gateway:~$

---

### Post by Stan% on 2007-03-26
anybody here tonight?

---

### Post by stalkingwolf on 2007-03-28
Ok I'm Using Xubuntu  6.06 on a Compaq EVO N410c.  It identifies the internal modem and port,
I entered all the necessary information, it activates the connection and all that.

The problem is I can't seem to find a "connect" button.  Any ideas?

---

### Post by dstew on 2007-03-28
I recommend starting a new thread, this one is pretty worn out. But, try **wvdialconf** at the command line.

---

