---
title: "Installing Epson Perfection 3170 Photo scanner"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-26
I'm trying to install an Epson 3170 Perfection scanner. Have downloaded the iscan-2.6.0 tarball, unzipped it and run ./configure.

I get the following errors:

checking for gtk+-2.0... checking for gtk+... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
yes
checking GTK_CFLAGS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking GTK_LIBS... sh: gtk-config: not found
sh: gtk-config: not found
sh: gtk-config: not found
 
checking for imlibgdk... Package imlibgdk was not found in the pkg-config search path. Perhaps you should add the directory containing `imlibgdk.pc' to the PKG_CONFIG_PATH environment variable No package 'imlibgdk' found
configure: error: Library requirements (imlibgdk) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

-----------------------------------

Synaptic locates gtk-config but for some reason will not install it.

---

### Post by 1/0 on 2007-03-26
I don't know much about iscan but xsane is in synaptic so why not install xsane instead?

---

### Post by lwalper on 2007-03-26
xsane is installed, but when I run it I'm told there are "no devices available." and am given a list of possible reasons:

1) There really is no device that is supported by SANE
2) Supported devices are busy
3) The permissions for the device do not allow you to use it - try as root
4) The backend is not loaded by SANE (man sane-dll)
5) The backend is not configured correct (man sane-"backendname")
6) Possibly there is more than one SANE version installed

I'm plugged into the USB2 port, power is on.

---

### Post by lwalper on 2007-03-26
Given my options I uninstalled XSANE and tried again to run ./configure on the iscan-2.0.6 file with the same results.

Is the sane backend loaded? It looks like xsane is the frontend.

---

### Post by lwalper on 2007-03-26
I read this page (over my head) but I did read it . . .


[http://ccrma.stanford.edu/planetccrma/man/man1/gtk-config.1.html](http://ccrma.stanford.edu/planetccrma/man/man1/gtk-config.1.html)

Where can I get a copy of gtk-config?

---

### Post by lwalper on 2007-03-26
I read the man sane-dll information

DESCRIPTION
       The  sane-dll library implements a SANE (Scanner Access Now Easy) back&#8208;
       end that provides access to an arbitrary number of other SANE backends.
       These  backends  may  either  be  pre-loaded  at  the time the sane-dll
       library is built or, on systems that support dynamic loading of  shared
       libraries,  the backends may be loaded at runtime.  In the latter case,
       adding support for a new backend simply involves installing  the  rele&#8208;
       vant  library in /usr/lib/sane and adding an entry to the dll.conf con&#8208;
       figuration file.  In other words, no applications need to  be  modified
       or recompiled to add support for new devices.


---------------------------

Do I need the gtk-config file or, do I need to install a different/addtional sane library?

---

### Post by lwalper on 2007-03-26
[http://www.ubuntuforums.org/showthread.php?t=386804&highlight=scanners](http://www.ubuntuforums.org/showthread.php?t=386804&highlight=scanners)

I found this thread and ran the instructions in post#6 -- Xsane seems to work now. I also installed everything in Synaptic that had to do with sane -- maybe that did something too??

---

### Post by lwalper on 2007-03-26
Well, at least the software loads. Now, when I click Scan (or preview) I get the error

 'Failed to start scanner: invalid argument.'

What's up??

---

### Post by lwalper on 2007-03-26
[http://khk.net/sane/download.html](http://khk.net/sane/download.html)

Went to this place and found a backend for the epson scanner. Do I need this?

---

### Post by 1/0 on 2007-03-27
I don't think you need any extra installs. Are you scanning as regular user or root? This could be an error message due to insufficient permissions. I'm guessing its an USB scanner so the scanner should mount in /dev/bus/usb/x/y. What are the permissions there? (ls -l)

Is the user added to the scan group?

```
adduser username scanner
```

What do you get from lsusb and sudo sane-find-scanner?

---

### Post by lwalper on 2007-03-27
> I don't think you need any extra installs. Are you scanning as regular user or root?
I don't know. I just click "Scan"
> I'm guessing its an USB scanner so the scanner should mount in /dev/bus/usb/x/y. What are the permissions there? (ls -l)
Yes, it's a USB2 scanner.

Permissions? I don't know?? When I run 'ls -l' I get
```
total 680
-rw-r--r-- 1 leslie leslie   4244 2007-03-25 10:33 Accounts 3-23-07
-rw-r--r-- 1 leslie leslie    170 2007-03-23 12:19 Accounts 3-23-07.20070323121947.log
-rw-r--r-- 1 leslie leslie    192 2007-03-23 12:19 Accounts 3-23-07.20070323121949.log
-rw-r--r-- 1 leslie leslie   4919 2007-03-25 10:28 Accounts 3-23-07.20070325102420.log
-rw-r--r-- 1 leslie leslie   4125 2007-03-23 12:19 Accounts 3-23-07.20070325103355.xac
-rw-r--r-- 1 leslie leslie    170 2007-03-25 10:33 Accounts 3-23-07.20070325103357.log
-rw-r--r-- 1 leslie leslie 612884 2007-03-22 05:35 background mono.mp3
drwxr-xr-x 3 leslie leslie   4096 2007-03-23 10:39 cbtracker
drwxr-xr-x 6 leslie leslie   4096 2007-03-26 12:09 Desktop
lrwxrwxrwx 1 leslie leslie     26 2007-03-19 08:17 Examples -> /usr/share/example-content
drwx------ 2 leslie leslie   4096 2007-03-23 05:34 memo_file
drwx------ 4 leslie leslie   8192 2007-03-23 19:49 MyPDA
drwxr-xr-x 7 leslie leslie   4096 2007-03-22 18:39 openchrome
-rw-r--r-- 1 leslie leslie    156 2007-03-23 10:40 personal 3-23-07
-rw-r--r-- 1 leslie leslie    156 2007-03-23 10:40 personal 3-23-07.backup
-rw-r--r-- 1 leslie leslie   4540 2007-03-23 12:19 translog.20070323121308.log

```
> Is the user added to the scan group?

Don't know that either. I'm the only one using the system. When I run 
```
adduser leslie scanner
```
I get the following:
> Only root may add a user or group to the system.
> What do you get from lsusb and sudo sane-find-scanner?
```
found USB scanner (vendor=0x04b8 [EPSON], product=0x0116 [EPSON Scanner]) at libusb:005:002
```
```
lsusb
Bus 005 Device 002: ID 04b8:0116 Seiko Epson Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

---

### Post by lwalper on 2007-03-27
So I read this thread

[http://www.ubuntuforums.org/showthread.php?t=389067&highlight=scanner](http://www.ubuntuforums.org/showthread.php?t=389067&highlight=scanner)

and thought I'd just adjust the scanner group in the Users and Groups. I was already there, so, added 'root' to the users. Still no go. Changed it back to the way it was.

Under my user privileges there is a tic in the "Use Scanners" box.

---

### Post by 1/0 on 2007-03-27
If you type groups in a terminal you will see which groups your user is added to. The permissions would be the ones for /dev/bus/usb/x/y, i.e. ls -l /dev/bus/usb/x/y where x and y is 005 002

Some of the commands has to be done by root, I'll try to remember to add sudo in my comments. If you're not in sthe scanner group do this:

```
sudo gpasswd -a leslie scanner
```

I just saw that Ubuntu doesn't add Epson drivers in the standard package so you need to install the backends in libsane-extras:

```
sudo apt-get install libsane-extras 
```

Somehow the correct config file is not added. I'm not sure if its needed but you could add it by:
```
sudo cp /etc/sane.d/epson.conf /etc/sane.d/epkowa.conf
```

The config files need to adjusted to usb
```
sudo nano /etc/sane.d/epson.conf 
```
Comment (add # in the beginning) all lines with scsi.
Uncomment (remove the #) all lines with usb and adjust to your setting to "usb 0x4b8 0x116" (from your lsusb). Exit and save (ctrl x). 

It should be working now but you might have to:
```
sudo chmod 0666 /proc/bus/usb/005/002
```

Try xsane/iscan/kooka now.

---

### Post by lwalper on 2007-03-27
OK, so each command seemed to go as described. Thanks. What follows is my epson.conf file (with the suggested changes).

--------------------------------------------------

# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
#scsi EPSON                     ([COLOR="Red"]this line got an added #[/COLOR])
# for the GT-6500:
#scsi "EPSON SC"                     ([COLOR="Red"]this line got an added #[/COLOR])
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the $
# For any system with libusb support (which is pretty much any recent Linux dis$
# following line is sufficient. This however assumes that the connected scanner$
# accurate, it's device ID) is known to the backend.
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
 usb 0x4b8 0x116[COLOR="Red"]             (and this had one removed)[/COLOR]
# And for the scanner module, use the following configuration:
usb /dev/usbscanner0            [COLOR="Red"] (and this had one removed)[/COLOR]
usb /dev/usb/scanner0             [COLOR="Red"](and this had one removed)[/COLOR]

--------------------------------------------------------------

When I attempt to open xsane I get the error (unable to locate scanner (or device, or some such thing)). Xsane does open, but of course, the same error is generated "Failed to start ..."

Since I continued to have problems I ran 

sudo chmod 0666 /proc/bus/usb/005/002

Still no go.

---

### Post by 1/0 on 2007-03-27
Did you make a copy of epson.conf to /etc/sane.d/epkowa.conf

The config looks good. Also try switching the scanner off and on.

---

### Post by lwalper on 2007-03-27
Yes, I made a copy of that file -- checked the file manager to make sure it was there -- yep.

Restarted the computer, turned the scanner off/on. Still no joy. When I click on the Xsane button in the applications drop-down list (Applications > Graphics > Xsane) I get the "Searching for devices" pop-up, then a "No devices available" pop-up which hangs the loading of the scanning software.

If I click "More" in that window I get the previously described list of options. Clicking "Close" of course does just that, and the Xsane app does not load.

When I look in my devices the USB stuff is all labeled 1.1. Shouldn't that be 2.0 (or 2.something)?

---

### Post by lwalper on 2007-03-28
Would it be better to just go to Synaptic and uninstall all the Xsane stuff and try something different?--maybe re-start this whole process from scratch? As a *new* newbie maybe I've messed something up somewhere?

---

### Post by 1/0 on 2007-03-28
I doubt it. I just borrowed an Epson scanner from a friend so now I can see if I can reproduce your problems on this one (4490).

---

### Post by lwalper on 2007-03-28
WOW!! You've really gone the second mile. Thanks. Hope we can get something worked out.

---

### Post by 1/0 on 2007-03-29
Ok, I got it working with iscan. Basically the drivers don't like coexisting with each other so you'll need to do the following (I take it you already made .deb files of the rpm:s from avasys):

```
sudo dpkg -i --force-overwrite iscan_2.6.0-0.c2_i386.deb
```
Answer 'N' at the question.
```
sudo dpkg -i iscan-plugin-gt-x750_1.0.0-1.c2_i386.deb
```
Now the problem I had is that every now and then the scanner is mounted under a different bus by udev/hotplug. So if you get a problem you have to poll the ports via 'lsusb' and you'll figure out your X and Y (it was 005 002). Then do this and it'll be fine:
```
sudo chmod 0666 /proc/bus/usb/X/Y
```
Now start iscan and it should be fine... hopefully

---

### Post by lwalper on 2007-03-29
An RPM file can be converted to a DEB?

Do I need Alien to do that?

[http://linuxhelp.blogspot.com/2005/06/convert-between-rpm-deb-and-tgz.html](http://linuxhelp.blogspot.com/2005/06/convert-between-rpm-deb-and-tgz.html)

I have downloaded everything from avasys.

---

### Post by lwalper on 2007-03-29
I installed alien through Synaptic and ran the following:

sudo alien -i iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
Warning: Skipping conversion of scripts in package iscan-plugin-gt-9400: postrm
Warning: Use the --scripts parameter to include the scripts.

So tried this:

sudo alien -i -scripts iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm
You can not use --generate or --single with --install.

I'm obviously doing something wrong. Looked for a help file with alien:

alien help
Must run as root to convert to deb format (or you may use fakeroot).

So tried:

fakeroot alien help
bash: fakeroot: command not found

And:

sudo alien help
File "help" not found.

So I ran the following:

 sudo alien -i --scripts iscan-plugin-gt-9400-1.0.0-1.c2.i386.rpm [using the -- double dash in front of scripts]

Something seemed to happen - at least a few seconds went by and there were no errors generated, but I see no copy of the rpm renamed as deb. Did alias put the file somewhere other than on the desktop?

---

### Post by 1/0 on 2007-03-29
Yes, you need alien. The following commands should do the trick:

```
sudo alien iscan-2.6.0-1.c2.i386.rpm
sudo alien iscan-plugin-gt-x750-1.0.0-1.c2.i386.rpm
```

Maybe you'll need the flags -d -c and -k. Alien will then create a .deb file in the present directory (check which with pwd). After you've done that do the install (dpkg) as I wrote before. Good luck!

---

### Post by lwalper on 2007-03-29
Well I'll be. My smile's as wide as the Mississippi River. The scanner works!!

Thanks a lot for all your help.

---

### Post by 1/0 on 2007-03-30
Happy to help. I learned a bit myself and got to try scanning with the 4490, which isn't that bad.

---

### Post by xoros on 2007-04-29
> **1/0 said:**
> Ok, I got it working with iscan. Basically the drivers don't like coexisting with each other so you'll need to do the following (I take it you already made .deb files of the rpm:s from avasys):

```
sudo dpkg -i --force-overwrite iscan_2.6.0-0.c2_i386.deb
```
Answer 'N' at the question.
```
sudo dpkg -i iscan-plugin-gt-x750_1.0.0-1.c2_i386.deb
```
Now the problem I had is that every now and then the scanner is mounted under a different bus by udev/hotplug. So if you get a problem you have to poll the ports via 'lsusb' and you'll figure out your X and Y (it was 005 002). Then do this and it'll be fine:
```
sudo chmod 0666 /proc/bus/usb/X/Y
```
Now start iscan and it should be fine... hopefully

Hi, I have a perfection 2450 and I feel i'm really close to getting it working with iscan...   

Where is the plugin file ??  I dont see that on the avasys site for my scanner,  I installed the first .deb though

All I get is when iscan starts and I hit preview... "cannot send command to scanner"  

Any ideas ?

---

### Post by xoros on 2007-04-29
By the way this is happening:

$ sudo modprobe scanner vendor=0x04b8 product=0x0112
FATAL: Module scanner not found.

---

### Post by xoros on 2007-04-29
And this is dmesg when running iscan: 

[  343.288000] usb 2-2: usbfs: interface 0 claimed by usbfs while 'iscan' sets config #1
[  351.432000] usb 2-2: usbfs: interface 0 claimed by usbfs while 'iscan' sets config #1

---

### Post by david_2001 on 2007-05-13
> **xoros said:**
> By the way this is happening:

$ sudo modprobe scanner vendor=0x04b8 product=0x0112
FATAL: Module scanner not found.

That's not going to work, I'm afraid, as the 2.6 kernel no longer has a scanner module!

**How to install an Epson Perfection 3170 Photo the easy way **(I'm just assuming that sane is already installed):

[LIST]
[*]Switch scanner off.  (Do not skip this step!)
[*]Install libsane-extras
```
sudo apt-get install libsane-extras
```
[*]Open and **read** "/usr/share/doc/libsane-extras/README.Debian".  This will tell you where to get the necessary Epson rpm package from, how to extract libesint32 and esfw32.bin, and where they should be installed.  Note that only the plugin package (currently "iscan-plugin-gt-9400-1.0.0-1.c2.i386") is really needed and that the installation directories differ between different versions of libsane-extras.
[*]If using a version of libsane-extras that is earlier than 1.0.18.5, read the following two bug reports:
[/LIST]
[INDENT][https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/77392](https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/77392)
[https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/77395](https://bugs.launchpad.net/ubuntu/+source/sane-backends-extras/+bug/77395)[/INDENT]
[LIST]
[*]Edit /etc/sane.d/dll.conf and comment out "epson".  For improved startup time, comment out everything.
[*]Add the path to libesint32, e.g. /usr/lib/iscan, to /etc/ld.so.conf
[*]Run ldconfig
```
sudo ldconfig
```
[*]Switch scanner on
[*]Start xsane.
[/LIST]
Job done :cool:.

---

### Post by Lapino on 2007-06-03
I tried the above solution and in works perfectly in Feisty 32bit. Unfortunately, it fails in 64 bit. Anyone has an idea on how to fix this?

---

### Post by ahurd on 2008-01-17
Hi David_2001

I tried your solution and the first step resulted in following messages:

albert@ALBERT-KUBUNTU:~/Desktop$ sudo apt-get install libsane-extras
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libltdl3
The following NEW packages will be installed:
  libltdl3 libsane-extras
0 upgraded, 2 newly installed, 0 to remove and 38 not upgraded.
Need to get 411kB of archives.
After unpacking, 1008kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main libltdl3 1.5.22-4 [168kB]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe libsane-extras 1.0.18.5 [243kB]
Fetched 411kB in 3s (115kB/s)
Selecting previously deselected package libltdl3.
(Reading database ... 134929 files and directories currently installed.)
Unpacking libltdl3 (from .../libltdl3_1.5.22-4_i386.deb) ...
Selecting previously deselected package libsane-extras.
Unpacking libsane-extras (from .../libsane-extras_1.0.18.5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsane-extras_1.0.18.5_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man5/sane-epkowa.5.gz', which is also in package iscan
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libsane-extras_1.0.18.5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Could you tell me what to do now?

---

### Post by Lapino on 2008-01-22
I'm not sure if that is the problem, but try completely uninstalling iscan before you try david's tutorial.

---

