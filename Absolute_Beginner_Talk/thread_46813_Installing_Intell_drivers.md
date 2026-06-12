---
title: "Installing Intell drivers"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-06
If anyone can please assist me in installing the correct drivers for my system.
Here is the link for my board in case anyone want to take a look.

[http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1674&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1674&lang=eng)

There is a couple of Linux drivers. SUSE, Red Fat, Red Flag and Novell. They all have seperate headings. Which one for Ubuntu? I understand Ubuntu is Debian-based?

I downloaded the following one: graphics_1.1_RF.tar. Unzipping it I get a file calles install.sh. Should I just double click it or how will I go ahead installing and updating the file. The readme with it is not very clear, cause there is a lot of things I should ensure I have.

Regards

---

### Post by brim4brim on 2005-07-06
.deb files are for Ubuntu I think as it's based on debian  but an install.sh should work aswell.  From my experience it's better to open up root terminal, go to the directory and type sh install.sh but make sure your following the instructions they gave as far as where to run this from etc...

If you read the instructions carefully they are generally pretty good at describing what you have to do but if you just glance over it, it can appear a bit much.

---

### Post by poofyhairguy on 2005-07-06
[QUOTE=GrootBrak]If anyone can please assist me in installing the correct drivers for my system.
Here is the link for my board in case anyone want to take a look.

[http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1674&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Product_Filter.aspx?ProductID=1674&lang=eng)

There is a couple of Linux drivers. SUSE, Red Fat, Red Flag and Novell. They all have seperate headings. Which one for Ubuntu? I understand Ubuntu is Debian-based?

I downloaded the following one: graphics_1.1_RF.tar. Unzipping it I get a file calles install.sh. Should I just double click it or how will I go ahead installing and updating the file. The readme with it is not very clear, cause there is a lot of things I should ensure I have.

Regards[/QUOTE]

DO this:

> cd directoryofdriver (ex: /home/username/drivername/)

then 

> sh install.sh

If that doesn't work, we can try something else.

---

### Post by GrootBrak on 2005-07-07
Had to work late last night. Thanx. I will try it out tonight. I'm just a bit worried about the "need to haves" as listed in the below pages. I know its asking a lot, but if you can just peek at the software requirements in the quote below, and help me out how I should confirm that what I have is what I need. Esp. the kernel version. Hopefully this will sort out some graphics problems I have. If I can kick this one, I want to go for my sound. So far I did not even had a beep from Linux!!!

> ============================
=================================
3 - Supported Linux Distributions
=================================
Intel(R) has performed limited validation to ensure basic functionality of
the Intel(R) GMA Graphics driver on the following distributions:
-- Red Hat* Enterprise Linux* Desktop 3.0 - Update 3 (kernel: 2.4.21-20.EL)
-- Novell* Linux* Desktop 9 (kernel: 2.6.5-7.111)
-- Red Flag* Linux* Desktop 4.1 (kernel: 2.4.26-1)
Linux drivers for the Intel(R) GMA 900 have also been released to the Linux
community. Thus, future releases of distributions hopefully should contain
native Intel(R) GMA 900 support.
4 - Pre-Install Requirements
============================
Prior to installing the Intel(R) GMA Driver on an Intel(R) Desktop Board
product, please ensure that your system meets the installation requirements
defined in the following sub-sections.
4.1 - Platform Hardware Requirements
------------------------------------
Verify that the following hardware requirements are met:
-- The desktop system must contain a 915G chipset-based Intel(R) Desktop
Board.
-- The desktop system must contain an integrated Intel(R) GMA 900 solution.
-- The desktop system should contain at least 256MB of system memory.
4.2 - Platform BIOS Requirements
--------------------------------
Verify that the following BIOS requirements are met:
-- The Primary Video Adapter option in system BIOS must be set to “Auto”, and
a PCI Express video card must not be installed in the system.
NOTE: Please check any documentation accompanying your product for
instructions on changing BIOS settings.
4.3 - Platform Software Requirements
------------------------------------
Verify that the following software requirements are met:
-- Verify that the specific kernel version installed in the system meets the
minimum required kernel version listed in Section 3 for the Linux
distribution you are running. If needed, check the currently running kernel
version using the 'uname' command as follows:
uname –r
-- Verify that XFree86 version 4.2.0 or later is installed on the system. The
Intel(R) GMA Driver will not function with earlier versions.
X –version
=================================
5 - Installing the Driver Package
=================================
1. Log into the system as root.
2. Make sure X11 is not running by bringing up a shell prompt and running the
command:
init 3
NOTE: You might have to press Ctrl+Alt+F1 to change to console 1 after
running init 3. You will have to re-login to the system after running init 3.
3. Log into the system as the "root" user and provide the "root" user
password when prompted.
4. Go to the directory where you downloaded the driver installation package.
If you downloaded the driver installation package to "/tmp":
cd /tmp
5. Enter the following command to Install the RPM:
rpm –ihv i915Graphics-1.0-0.i386.rpm
6. Reboot the system.
7. Log into the system as root.
8. Run your distribution-specific display configuration utility.
9. Select the i915 G driver and turn on Accelerated Graphics.
10. Reboot the system
NOTE: A reboot of the system is required to successfully load the Intel(R)
GMA Driver.
============================================
6 - Verifying Driver Was Installed Correctly
============================================
Use the 'lsmod' command to verify that the Intel(R) GMA Driver installed
correctly. If the returned result contains "gdg", then the Intel(R) GMA
Driver installation completed successfully.
lsmod | grep -i 'gdg'
========================
7 - Known Issues/Errata
========================
Below is a list of known issues and errata uncovered during validation of the
Beta Intel(R) GMA Driver. Also included are some steps to workaround these
issues until fixes are implemented.
7.1 - Distribution Independent Issues/Errata
--------------------------------------------
SYMPTOM: The uninstall feature of the Automated Installer does not
function.
CAUSE: Currently under investigation.
WORKAROUND: Manually configure the system to use the "vesa" drivers and
delete the "gdg.o" file from the system.
SYMPTOM: Intel(R) GMA Driver does not load when using 8-bit (256) color
depth.
CAUSE: Currently under investigation.
WORKAROUND: Change the color depth to 16-bit or higher.
7.2 – Red Flag* Linux* Desktop 4.1 Specific Issues/Errata
--------------------------------------------
SYMPTOM: Known issues with video games when direct rendering is active:
CAUSE: When running Quake* 3, some blocks do not display correctly.
When running Tuxracer*, the upper half of the screen does not
display correctly. When playing some WMF files using Kaffeine*,
the right half of the screen might blur.
WORKAROUND None
SYMPTON: A non-root user cannot run direct rendering graphics. The
glxinfo command shows an access problem with the device.
CAUSE: The /dev/dri/card0 device has no permissions for non root
users.
WORKAROUND: As root, do: chmod go+rw /dev/dri/card0

---

### Post by GrootBrak on 2005-07-07
When running the "sh install.sh" I get a promp to choose Install or Uninstall. I install. (DUH...) A line appear that says "get_osname()" The the next line. "Compiler is not available to compile modules, aborting..." and then its back to my prompt.

Going the way of the Intel doc, (and I have what you need on my system). I get the following lines:

rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open packages database in /var/lib/rpm

And back to prompt.
Any ideas?

---

