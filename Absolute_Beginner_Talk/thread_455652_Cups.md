---
title: "Cups"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by Tumpster on 2007-05-26
So my printer isn't printing, I got it to print a test page in HP Toolbox, closed that out and tried printing something from open office to test it and it went no where, it just sits in the print icon saying it's printing but I have nothing. Is this a cups related issue some how? I have cups installed and can get to the user interface but I prefer the HP-Toolbox method. I've uninstalled the printer and currently await any great souls willing to help! :) THank you!

---

### Post by drs305 on 2007-05-26
It will help if you tell us what model you have. I had similar problems with an HP1000 and got it working following the instructions posted in this thread. I had an HP1000 laserjet so just substituted 1000 wherever 1020 was mentioned. Good luck.

[http://ubuntuforums.org/showthread.php?t=220766&highlight=foo2zjs+1020](http://ubuntuforums.org/showthread.php?t=220766&highlight=foo2zjs+1020)

---

### Post by Tumpster on 2007-05-26
I have an HP 1410 PSC All in One, I ran a HP-Check and it came back with only two errors, one being that it didn't find an active printer (this being cause it's uninstalled), and also found this:

 "HPOJ running?
error:
Yes, HPOJ is running. HPLIP is not compatible with HPOJ. To run HPLIP, please remove HPOJ."


Should this be of concern to me?? Thanks!

---

### Post by Pollywoggy on 2007-05-26
> **Tumpster said:**
> I have an HP 1410 PSC All in One, I ran a HP-Check and it came back with only two errors, one being that it didn't find an active printer (this being cause it's uninstalled), and also found this:

 "HPOJ running?
error:
Yes, HPOJ is running. HPLIP is not compatible with HPOJ. To run HPLIP, please remove HPOJ."


Should this be of concern to me?? Thanks!

I have a PSC 2110 All-In-One printer and I use CUPS.  I suggest you remove HPLIP unless you are sure you need it.  Then restart HPOJ:

/etc/init.d/hpoj restart
and then
/etc/init.d/hpoj setup

One other thing.  You might need to edit the configuration files in /etc/cups/ in order to get CUPS printing to work.  How did you configure CUPS, though KDE?  I usually have to edit /etc/cups/cupsd.conf and also /etc/cups/client.conf (this one I did not need to touch in the latest CUPS version) so that I am allowed to print from all my client machines.

After you have HPOJ setup, try connecting to CUPS using telnet like this:

telnet localhost 631
and do the same from each of the CUPS clients:

telnet <yourserver> 631

If these connections are refused, you have CUPS slightly misconfigured.

---

### Post by Tumpster on 2007-05-26
I do that and I get this:

craig@craig-desktop:~$ /etc/init.d/hpoj restart

Currently defined device names ([*]=default):
    (none)

Syntax for the root user:
    /usr/sbin/hpoj start|stop|setup|status|condrestart [-q[uiet]|-v[erbose]]

craig@craig-desktop:~$ /usr/sb/hpoj start
bash: /usr/sb/hpoj: No such file or directory
craig@craig-desktop:~$ /etc/init.d/hpoj setup

Currently defined device names ([*]=default):
    (none)

Syntax for the root user:
    /usr/sbin/hpoj start|stop|setup|status|condrestart [-q[uiet]|-v[erbose]]

craig@craig-desktop:~$


What is wrong?

---

### Post by Pollywoggy on 2007-05-26
craig@craig-desktop:~$ /usr/sb/hpoj start
 bash: /usr/sb/hpoj: No such file or directory

Are those typos?  Did you somehow change the /etc/init.d/hpoj script?

I suggest you 'sudo apt-get remove --purge hpoj' and then install it again.
There might be a problem with that script unless your post had typos.

Once you reinstall it, run 'sudo /etc/init.d/hpoj setup'

These are the cupsys packages you need to explicitly install if they are not already installed.

cupsys
cupsys-bsd
cupsys-client

---

### Post by Tumpster on 2007-05-26
?craig@craig-desktop:~$ sudo apt-get remove --purge hpoj
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  hpoj*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1368kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137580 files and directories currently installed.)
Removing hpoj ...

Stopping the HP OfficeJet Linux driver.
Purging configuration files for hpoj ...
craig@craig-desktop:~$ sudo apt-get install hpoj
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  hplip foomatic-db-hpijs sane mtools hpoj-xojpanel
The following NEW packages will be installed:
  hpoj
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/456kB of archives.
After unpacking 1368kB of additional disk space will be used.
Selecting previously deselected package hpoj.
(Reading database ... 137502 files and directories currently installed.)
Unpacking hpoj (from .../archives/hpoj_0.91-9_i386.deb) ...
Setting up hpoj (0.91-9) ...
hpoj: To enable scanning with sane you must
hpoj: manually uncomment the hpoj entry in /etc/sane.d/dll.conf.
Adding user `hpojlp' to group `lp'...
Done.

Stopping the HP OfficeJet Linux driver.
Starting the HP OfficeJet Linux driver.
    No hpoj devices have been configured.
    As root, run "/etc/init.d/hpoj setup".


craig@craig-desktop:~$ sudo /etc/init.d/hpoj setup

Stopping the HP OfficeJet Linux driver.

----------------------------------------------------------------------

This program manages devices controlled by the HP OfficeJet Linux
driver (hpoj).  It attempts to probe your computer for local parallel-
and USB-connected devices, and allows you to specify network addresses
for remote JetDirect-connected devices.

If you experience any difficulties in detecting your device(s), then
refer to the hpoj documentation for troubleshooting information.

----------------------------------------------------------------------

Currently defined device names ([*]=default):
    (none)

----------------------------------------------------------------------

Probe for parallel-connected devices ([y]/n)?  y

Successfully loaded kernel module "lp" for the device probe.

Warning: Probing incorrect I/O port addresses could result in system
instability and/or data loss!  Consult your hardware documentation, BIOS
setup and/or kernel messages to verify correct base addresses in the
following prompts.   Also, take care not to probe parallel ports that
have non-printer devices (such as disk or tape drives) connected.

Probe parallel port "-base 0x378 -basehigh 0x778 -device /dev/lp0" (y/[n])?  y

    *** ptal-mlcd failed to start!  Check syslog file for error messages.

Press <Enter> alone to continue, or if you would like to probe an
undetected parallel port, then enter its hexadecimal base address
(such as "378", "278", or "3BC") here --->

----------------------------------------------------------------------

Probe for USB-connected devices ([y]/n)?  y

Probing "%002%001"...
    No device found.

Probing "%001%002"...
    No device found.

Probing "%001%001"...
    No device found.

----------------------------------------------------------------------

Press <Enter> alone to continue, or if you would like to add a
JetDirect-connected device, then enter its dotted-decimal
IP address or hostname here --->

----------------------------------------------------------------------

Done updating device configuration files stored under /etc/ptal.
If you make manual changes to those files, then be sure to run
"/etc/init.d/hpoj start" so they will take effect.

----------------------------------------------------------------------

Starting the HP OfficeJet Linux driver.
    No hpoj devices have been configured.
    As root, run "/etc/init.d/hpoj setup".

craig@craig-desktop:~$



All 3 of the cupsy packages are installed too....

---

### Post by Pollywoggy on 2007-05-26
Do you have the printer plugged in?  It is USB, correct?  Plug the printer into the machine running CUPS and start the printer, then run setup again.
One other thing... are you running KDE or Gnome?  I have never set up CUPS using Gnome, only KDE or else the web interface that comes with CUPS.
The KDE  control panel has a tool for doing it and I think it is easy to use.  Gnome has one too but I have not familiarized myself with it.

---

### Post by Tumpster on 2007-05-26
yeah it's plugged in via usb, I just got it to print the allignment page in the HP-TOolbox BUT, when I go after that to print from something else or try printing the allignment page again it dosent.

---

### Post by Tumpster on 2007-05-26
I'm getting this:


Probe for USB-connected devices ([y]/n)?  y

Probing "/dev/usblp0"...
    *** Found "PSC 1400 series" but failed to communicate with it!
    *** Elapsed time for this attempt was 0 second(s).
    *** Check syslog file for ptal-mlcd error messages.
    *** See hpoj documentation for troubleshooting information.

Probing "%002%001"...
    No device found.

Probing "%001%003"...
    No device found.

Probing "%001%001"...
    No device found.



Like it says, it sees it but it's not communicating for some reason.....

---

### Post by Pollywoggy on 2007-05-26
I don't know what is causing those errors.  Perhaps HPLIP would work best with your printer, but before you install it:

sudo apt-get remove --purge hpoj

Before you remove HPOJ, turn the printer on and then run 'sudo /etc/init.d/hpoj restart'

Does the printer do anything when you run that command?

what does 'sudo lsusb' say when the printer is plugged in and turned on?

---

### Post by Tumpster on 2007-05-26
craig@craig-desktop:~$ sudo /etc/init.d/hpoj restart
Password:

Stopping the HP OfficeJet Linux driver.
Starting the HP OfficeJet Linux driver.
    No hpoj devices have been configured.
    As root, run "/etc/init.d/hpoj setup".

craig@craig-desktop:~$


craig@craig-desktop:~$ sudo lsusb
Password:
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 03f0:4d11 Hewlett-Packard
Bus 001 Device 001: ID 0000:0000
craig@craig-desktop:~$

---

### Post by Pollywoggy on 2007-05-26
I think you should remove HPOJ and install HPLIP instead.

Once you get CUPS working and if you want to get the scanner working, you might look here:
[http://ubuntuforums.org/showthread.php?t=428679&highlight=hplip](http://ubuntuforums.org/showthread.php?t=428679&highlight=hplip)

---

### Post by Tumpster on 2007-05-26
Stopping the HP OfficeJet Linux driver.
Purging configuration files for hpoj ...
craig@craig-desktop:~$ sudo apt-get install hplip
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  kdeprint gtklp xpp
The following NEW packages will be installed:
  hplip
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 461kB of archives.
After unpacking 2028kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main hplip 0.9.7-4ubuntu1 [461kB]
Fetched 461kB in 2s (180kB/s)
Selecting previously deselected package hplip.
(Reading database ... 137502 files and directories currently installed.)
Unpacking hplip (from .../hplip_0.9.7-4ubuntu1_i386.deb) ...
Setting up hplip (0.9.7-4ubuntu1) ...
Creating/updating hplip user account...
Starting hpiod:                                            [FAILED]
Starting hpssd:                                            [FAILED]


Now what can I do?

After loading up HPLIP and running a print it still dosen't talk to my printer, there's a breakdown somewhere in communication!! :) I'm ready to smash my head into the wall.....

---

### Post by Pollywoggy on 2007-05-26
> **Tumpster said:**
> Stopping the HP OfficeJet Linux driver.
Purging configuration files for hpoj ...
craig@craig-desktop:~$ sudo apt-get install hplip
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  kdeprint gtklp xpp
The following NEW packages will be installed:
  hplip
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 461kB of archives.
After unpacking 2028kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main hplip 0.9.7-4ubuntu1 [461kB]
Fetched 461kB in 2s (180kB/s)
Selecting previously deselected package hplip.
(Reading database ... 137502 files and directories currently installed.)
Unpacking hplip (from .../hplip_0.9.7-4ubuntu1_i386.deb) ...
Setting up hplip (0.9.7-4ubuntu1) ...
Creating/updating hplip user account...
Starting hpiod:                                            [FAILED]
Starting hpssd:                                            [FAILED]


Now what can I do?

Go here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1410](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1410)
It says there that the driver you need is hpijs

'apt-cache show hpijs' says that this driver is used with the foomatic-filters package.

[http://hplip.sourceforge.net/supported_devices/inkjet_aio.html](http://hplip.sourceforge.net/supported_devices/inkjet_aio.html)  confirms your printer is supported by hplip.

[http://hplip.sourceforge.net/install/manual/distros/ubuntu.html](http://hplip.sourceforge.net/install/manual/distros/ubuntu.html)  has step-by-step instructions for Ubuntu
Since you have the hplip package installed, you might skip the part that tells you how to install it from a tarball and jump to the section "Once the Install is Completed"

---

### Post by Tumpster on 2007-05-26
AFter following the walk through and everything else it works!!!! I'm printing like mad to make sure this works!! YES!!, Thank you for you're help!!

One more thing, how do I get the HP Toolbox in my applications menu so I can have all the nifty features for my printer?

---

### Post by Pollywoggy on 2007-05-27
HP Toolbox is part of HPLIP, if I am not mistaken, so I don't use it.  My printer uses HPOJ.

Try searching "hp toolbox" in Google Linux [http://www.google.com/linux](http://www.google.com/linux)

---

### Post by tdmoore on 2007-12-06
drs305,

Glad to hear you got your HP 1000 working.  Am running 7.10 and am TERRIBLE with command lines (still a real newb) but sure would like to get my printer going.  Have a color Xerox that actually worked right out of the box....but like to use the HP for straight monochrome.

I have tried following all the codes, links etc but got confused.  Any other way to do this using a GUI format?

Thanks for any assistance you can give.

---

### Post by stchman on 2007-12-06
> **Tumpster said:**
> So my printer isn't printing, I got it to print a test page in HP Toolbox, closed that out and tried printing something from open office to test it and it went no where, it just sits in the print icon saying it's printing but I have nothing. Is this a cups related issue some how? I have cups installed and can get to the user interface but I prefer the HP-Toolbox method. I've uninstalled the printer and currently await any great souls willing to help! :) THank you!

According to the open printing database your printer should work by using the hpijs driver.

[http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1410](http://openprinting.org/show_printer.cgi?recnum=HP-PSC_1410)

---

