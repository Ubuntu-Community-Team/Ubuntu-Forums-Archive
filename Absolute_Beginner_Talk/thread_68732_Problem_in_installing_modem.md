---
title: "Problem in installing modem"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by johnxxv on 2005-09-24
Hi!

I'm a total newbie to anything other than Windows. I just got a Ubuntu CD and I installed in my PC. I am impressed with Ubuntu! But I still have a problem installing my modem. 

It seems that it is recognized in the device manager. But the modem cannot be autodetected by the dialer. 

I don't know what to do. My modem is an internal modem, HSF 56k HSFi Modem. 

Any help would be greatly appreciated.

Thanks!

johnxxx

---

### Post by phen on 2005-09-24
hi!
I did a search for your modem and was redirected to that page in the ubuntu wiki:
[https://wiki.ubuntu.com/forum/hardware/Conexant](https://wiki.ubuntu.com/forum/hardware/Conexant)

it looks like your modem is not natively supported by linux, but there is a selfwritten module available. follow the instructions on that page, and when lspci returns the same serial numbers you should try to install that module. if you dont know how, just ask!

cheers!

---

### Post by johnxxv on 2005-09-26
Thanks a lot! Ill try that.

---

### Post by johnxxv on 2005-09-26
Hi Phen,

When I bought the modem, I got a CD that has drivers. I tried following the instructions installing the driver for Linux, but I can't make it work. 
This is what is written in the readme file.
---------------
The document describes the SoftModem Linux V4.06.06.02 release (A Beta release).
The release supports Linux 2.2 and 2.4 kernels. The source kit is divided into two parts, pre-compiled kernel
independent modules, and source code for building kernel-specific modules on the target machine. The
installation of the drivers is covered in the installation section of this document. The driver features V.90 Data
modem only. All data AT commands are implemented. Fax and Voice are not are supported at this time. V.92 is
not featured in this release.
Please see the README file for general information.
BEFORE INSTALLING
Remove any old HSF modem drivers, either manually or by running "rpm -e hsflinmodem" or "make uninstall"
if using the RPM or tar versions of this package respectively.
INSTALLATION INSTRUCTIONS
If your Linux distribution supports RPM (RedHat Package Manager), and has a recent libc, it is easiest to install
the binary RPM package with METHOD A. If your system has RPM but the distributed binaries are not
suitable, you may use METHOD B. METHOD C is for distributions without RPM support, or those who prefer
not to use RPM.
METHOD A: BINARY RPM PACKAGE (*.i586.rpm)
If you have obtained the driver package in RPM format:
1. install the rpm with "rpm -i hsflinmodem-<version>.i586.rpm"
2. run "hsfconfig" to complete the installation and configure your modem.
METHOD B: SOURCE RPM PACKAGE (*.src.rpm)
If no pre-generated binary RPM package is adequate for your system,you may download the source RPM
package and:
1. generate a new binary RPM package for your platform with "rpm --rebuild hsflinmodem-<version>.src.rpm"
2. install the new binary RPM package as described in METHOD A.
METHOD C: TAR PACKAGE (*.tar.gz)
If you have obtained the driver package in tar format:
1. extract the package with "tar -xzf hsflinmodem-<version>.tar.gz"
2. change to the package directory with "cd hsflinmodem-<version>"
3. run "make install" from the top of the package directory.
4. run "hsfconfig" to complete the installation and configure your modem.
(Alternatively to this whole procedure you may generate RPMS from the tar
package using rpm -ta hsflinmodem-<version>.tar.gz")
AFTER INSTALLATION
If an error occurred during installation, please see the sections 'BUGS'and 'REPORTING PROBLEMS' below.
Once the modem is installed and configured, you may access it as /dev/ttyHSF0 or /dev/cuaHSF0 (call-out
device). Additionally, you can use it via the symbolic link /dev/modem (equivalent to ttyHSF0).
Please review the permissions on the device nodes with "ls -l" to ensure that they are adequate for your system.
The "hsfconfig" command can be used to change certain modem configuration options or recompile the kernel
modules after installation of the package. Run "hsfconfig --help" for usage information.
CHANGING THE COUNTRY PARAMETER
With "hsfconfig --country" you may select another country supported by your modem.
MANUALLY UNLOADING THE DRIVERS
The modem drivers can be manually unloaded using the "hsfstop" command.
USING ALTERNATIVE PCI VENDOR AND DEVICE IDS
If your modem uses a chipset supported by the drivers but isn't recognized by the supplied .inf files, you may
use (at your own risk) "hsfconfig --hwtype" to explicitly configure the PCI vendor and device Ids of your
modem.
REMOVING THE DRIVER
If for any reason you wish to un-install the HSF drivers from your system, the proper way to proceed depends
on how they were initially installed.
If you used an RPM installation method, execute "rpm -e hsflinmodem" to remove the package. If you used the
tar method, change your current directory to where you extracted the archive, and execute "make uninstall"
------
johnxxv

---

### Post by Mustard on 2005-09-26
I thought it might be worth mentioning that there is a package called 'alien' which is able to change RPM's into .deb packages.  This might enable you to use the RPM installs after converting them to .deb.  I have no idea how easy alien is to use however.  If it looks to hard, I would stick with the tarball installation.

I've tried many times to get winmodems to work on a linux system, but I haven't ever had any success.  It's possible I am sure, as its obviously been done before.  My solution was to go out and buy a proper external modem.

---

