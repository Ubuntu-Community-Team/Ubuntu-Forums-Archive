---
title: "Need modem help again, sorry :("
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by learning on 2006-05-18
O.k., I have followed the steps from the wiki.  still get FATAL module not found error.
This is my output from scanmodem (not sure what is important so got whole thing pasted in):

UPDATE=2006_April_11
ONLY use scanModem downloaded as: [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)

./scanModem should ONLY be run within a Linux/UNIX partition.
If within a MicroSoft/DOS partition, abort with Ctrl-C now !!!
Copy scanModem.gz to your Linux partition and restart.


./scanModem: line 756: gcc: command not found
PCIBUS=0000:01:0a.0

Providing detail for device at  0000:01:0a.0
  with vendor-ID:device-ID
            ----:----
Class 0780: 11c1:044c   Communication controller: Agere Systems LT WinModem (rev 02)
  SubSystem 11c1:044c  Agere Systems LT WinModem
        Flags: medium devsel, IRQ 11

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian_version 2.6.15-22-386  4.0.3 none   i686

 The modem has a supported Lucent/Agere DSP (digital signal processing) Mars or Apollo DSP
 (digital signal processing) chipset with primary PCI_ID:  11c1:044c
 DSP=1

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
                /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-22-386.rpm        Check with
            # ls -l   /usr/src/rpm/RPMS/i686/ltmodem*
            Then install with:
            # rpm -i /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-22-386.rpm
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
--------------------------------------------------------------------------------ltmodem-8.26a.tar.gz         2.4.21 and earlier
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



   A subfolder Modem/  has been written,  containing these files with more detailed Information:
 ------------------------------------------------------------------------------------------
 1stRead.txt DriverCompiling.txt InfoGeneral.txt ModemData.txt Rational.txt Slmodem-ALSA.txt Slmodem.txt SoftModem.txt Testing.txt UNSUBSCRIBE.txt YourSystem.txt
-------------------------------------------------------------------------------------------


What do I do?

---

### Post by Mustard on 2006-05-18
Well it looks like you go to this link and download and install the .deb package for your particular kernel version...

[http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/Ubuntu/](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/Ubuntu/)

I'm assuming you have a 2.6.x.x kernel of some kind, and there is a reference to ubuntu packages in the /ubuntu folder at that ftp site.

That's my take on what its trying to say anyway.

This command will return your current kernel version...

```
uname -r
```

It also says that a subfolder was created called Modem/ which should contain more detailed information.  I'd certainly be reading over that information. :)

---

### Post by learning on 2006-05-18
Kernel is 2.6.15-22-386

I don't see one that matches it.

Would a different one work?  Should I go back to Breezy for a while?

---

### Post by Mustard on 2006-05-18
[QUOTE=learning]Kernel is 2.6.15-22-386

I don't see one that matches it.

Would a different one work?  Should I go back to Breezy for a while?[/QUOTE]

Hmm.well that does make it problematic.  I wonder whether there is a tar.gz version you could compile for your new kernel.  There are a number of tar.gz packages on level up from that directory that are marked with the notation 'alk'..I'm wondering whether that means 'all kernels'.  I don't really know for sure though. :)

-edit-
I'm on breezy atm and I'm using a 2.6.12-10-386 kernel.  A package does exist for that kernel version in the ubuntu directory at the ftp site.  I suppose that is an easy option to take.  Compiling the drivers for the dapper kernel could be a frustrating experience.

---

### Post by learning on 2006-05-18
I have no idea how to compile, either.](*,) 

I am really new to this.  I really love Ubuntu so far though.
I partitioned my hard drive on my work computer today. :-#   Going to install ubuntu there tomorrow.  I think I can replace everything I use for work with the included apps, (I mainly just use outlook and word anyway).  Seems to be no trouble with network there.

---

### Post by mlind on 2006-05-18
if you're going to build something manually for you ubuntu installation, you need
at least build-essential package installed which provides gcc (version 4?)
and for kernel stuff you need to install gcc-3.3.

And check out post [http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/Ubuntu/ubuntu-install.html](http://phep2.technion.ac.il/linmodems/packages/ltmodem/kernel-2.6/Ubuntu/ubuntu-install.html)

---

### Post by learning on 2006-05-18
Is there a way I can do what it says:

# rpmbuild --rebuild ltmodem-2.6-Nalk.src.rpm
will deposit an installer at:
/usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-22-386.rpm Check with
# ls -l /usr/src/rpm/RPMS/i686/ltmodem*
Then install with:
# rpm -i /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-22-386.rpm
or similar.

I guess the command would change or something, when I tried it (rpmbuild), it didn't seem to understand the command.

---

### Post by mlind on 2006-05-18
[QUOTE=learning]Is there a way I can do what it says:

# rpmbuild --rebuild ltmodem-2.6-Nalk.src.rpm
will deposit an installer at:
/usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-22-386.rpm Check with
# ls -l /usr/src/rpm/RPMS/i686/ltmodem*
Then install with:
# rpm -i /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.15-22-386.rpm
or similar.

I guess the command would change or something, when I tried it (rpmbuild), it didn't seem to understand the command.[/QUOTE]

basically,, no.
Ubuntu uses .deb (dpkg, apt) for package management, while f.ex fedora has .rpm. You can use 'alien' to convert from .rpm to .deb, but that's not what you want here.

If you can't find .deb package that someone else has provided for you, you have to compile the modules from source.
Relevant part should be this:

```

Make a note to include the following to Ubuntu users. The kernel-version may have to be different sometimes, but the pattern will be the same.
----
To prepare for compiling install the following packages:
   gcc-3.3
   kernel-kbuild-3.6
   linux-headers-2.6.10-5
   linux-headers-2.6.10-5-386
   wvdial
With your install disk in the driver, it should suffice to:
# apt-get install gcc-3.3   kernel-kbuild-3.6 wvdial   linux-headers-2.6.10-5-386
and the dependent linux-headers-2.6.10-5 will be installed too.

Dire,

After the above preliminary, for your
-----------------------
Class 0780: 11c1:0441   Communication controller: Lucent 
Microelectronics 56k WinModem (rev 01)
  SubSystem 1179:0001  

Use the software from:
 http://linmodems.technion.ac.il/packages/ltmodem/
    ltmodem-2.6-7-alk-7.tar.bz2  
Under Linux in your Root folder, do
# tar jxf ltmodem-2.6-7-alk-7.tar.bz2 
# cd ltmodem-2.6-7-alk-7
Look around with
# ls -l
# make clean
# make
will output drivers ltmodem.ko and  ltserial.ko
Read the instructions on how to manually install them.
Then do
# update-modules
# modprobe ltserial
should load the drivers.  The first function test is:
# wvdialconf  /etc/wvdial.conf
edit your personal info into  /etc/wvdial.conf  and dialout with:
# wvdial &
See Testing.txt for details

```

---

### Post by mlind on 2006-05-18
have you tried installing linux-restricted-modules package?
for 386 arch it's called linux-restricted-modules-386

```

sudo apt-get install linux-restricted-modules-386

```

restricted modules should contain ltmodem driver already.

/edit
```

apt-cache policy linux-restricted-modules-386
linux-restricted-modules-386:
  Installed: (none)
  Candidate: 2.6.15.22
  Version table:
     2.6.15.22 0
        500 http://fi.archive.ubuntu.com dapper/restricted Packages

```

(you need to enable restricted repository if you haven't already.)

---

### Post by learning on 2006-05-18
yes. already did the restricted modules thing.

I can find gcc-3.3

Don't see linux-headers with numbers. (In synaptic)

Do see just linux-kernel headers.  Is that the same thing?

kernel I have -package or -wedge.  no -kbuild.

Just tried modules again to be sure.  Got this output:

jason@jason-desktop:~$ sudo apt-get install linux-restricted-modules-386
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jason@jason-desktop:~$

---

### Post by mlind on 2006-05-18
well, if you got restricted-modules package installed, you don't need to do any building yourself.

just try
```

sudo modprobe ltmodem

```

if no input comes after that, you have succesfully applied ltmodem module on your running kernel.
command *lsmod | grep ltmodem* should include it on output.

---

### Post by learning on 2006-05-18
Got this:

jason@jason-desktop:~$ sudo modprobe ltmodem
jason@jason-desktop:~$ lsmod | grep ltmodem
ltmodem               566638  0


Guess it worked?

---

### Post by mlind on 2006-05-18
[QUOTE=learning]Got this:

jason@jason-desktop:~$ sudo modprobe ltmodem
jason@jason-desktop:~$ lsmod | grep ltmodem
ltmodem               566638  0


Guess it worked?[/QUOTE]

I hope so. Module seems to be loaded ok.

does command **wvdial** work now?

---

### Post by learning on 2006-05-18
No:

jason@jason-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.55
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
jason@jason-desktop:~$

---

### Post by mlind on 2006-05-18
[QUOTE=learning]No:

jason@jason-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.55
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
jason@jason-desktop:~$[/QUOTE]

okay, I've got no idea how to setup modems, sorry.

you may need additionally to do
```

sudo modprobe ltserial
wvdialconf  /etc/wvdial.conf
wvdial

```

I bet there's a gui alternative for configuration once you've loaded the two required modules.
To get these modules loaded by default, add their names to /etc/modules

---

### Post by learning on 2006-05-18
Well, thanks for trying.  Guess something will break my way eventually!

Here is what I got:

jason@jason-desktop:~$ sudo modprobe ltserial
Password:
FATAL: Error inserting ltserial (/lib/modules/2.6.15-22-386/volatile/ltserial.ko): Invalid argument
jason@jason-desktop:~$

---

### Post by mlind on 2006-05-18
[QUOTE=learning]Well, thanks for trying.  Guess something will break my way eventually!

Here is what I got:

jason@jason-desktop:~$ sudo modprobe ltserial
Password:
FATAL: Error inserting ltserial (/lib/modules/2.6.15-22-386/volatile/ltserial.ko): Invalid argument
jason@jason-desktop:~$[/QUOTE]

This looks like a good bit of advice
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems#head-cc17ea0ff3df391406e74527f1aed569be04709f](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems#head-cc17ea0ff3df391406e74527f1aed569be04709f)

---

### Post by learning on 2006-05-18
I tried that first before I posted for help.

---

### Post by mlind on 2006-05-18
[QUOTE=learning]I tried that first before I posted for help.[/QUOTE]

okay, that wiki seems to be outdated. modules names seem to be wrong..(?)

You got "invalid argument" when modprobing ltserial, where I got "no such device",
because I don't have serial ports enabled.

Try to create that /etc/udev/rules.d/10-local.rules like WIKI suggests.
then do *sudo /etc/init.d/udev restart*

try modprobing ltserial ltmodem modules again.

---

