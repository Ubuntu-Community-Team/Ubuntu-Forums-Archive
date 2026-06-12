---
title: "ATI Radeon Driver Install Write-Up"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by gmward on 2006-10-17
Proprietary ATI Driver Installation for 
Ubuntu Live and Ubuntu Installed Instances

NOTE:  The purpose of this write-up is to provide a simplistic process for installing an ATI driver in an Ubuntu Live or installed Ubuntu instance.  It is meant for people with limited Linux knowledge.  This is a problem I ran into and I would have found a document like this helpful (although I probably wouldn’t have learned as much as I did by having to figure this out on my own….)


My first experiences with Ubuntu in both LIVE and installed instances were tainted by a crash.  Initial boot of the Ubuntu version 6.06 LTS yielded the following error:

"Failed to Start the X server (your graphical interface).  It is likely theat it is not set up correctly.  Would you like to view the X Server output to diagnose the problem?" 

Select "Yes"

error output reads:

Log file: /var/log/xorg.0.log
Using config file: conf --> /etc/X11/xorg.conf

(EE) No Devices detected.

Fatal server error:

no screens found
XIO: fata IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processesd) with 0 events remaining.

In doing some quick research, I found that this was a problem common to many users whose systems were using later versions of ATI Radeon video cards.  My particular system was a Dell Optiplex D620 using an ATI Radeon x600 video card.

I worked around this problem the first time by booting from the Ubuntu CD in Safe Graphics Mode.   The display resolution used was optimal for my display (1280x1024 on my Dell 19” FPD) but it was my guess that the full power of the ATI card was not available to me.  There are several resources available that list the cause for this problem and report many fixes.  ATI also offers instructions on how to install its proprietary driver for Linux, but they are not specific to Ubuntu and they also assume that a user will be logged into X when installing the driver.

The purpose of this write-up is to give a step by step accounting of how to boot the Ubuntu CD for a live session, allow the X failure, and then install the proprietary ATI driver from removable media (a USB key in this case.)  The following assumes you are working on a system with an ATI card as described that has network (internet) connectivity.

The ATI proprietary driver can be downloaded from the following location:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)



•	Boot from the Ubuntu CD and choose the “Start or Install” option

•	sudo apt-get install linux-686

•	sudo apt-get update

•	sudo apt-get install linux-restricted-modules-$(uname -r)

Mount the portable media device containing the ATI driver:

•	Check the device name fdisk –l (will read something like sdb1)

•	Create directory for mount point: mkdir /home/ubuntu/USB

•	mount device to directory: sudo mount -t vfat /dev/sdb1 /home/ubuntu/USB

•	Create a temporary directory to which you can copy the driver file: mkdir /home/ubuntu/temp

•	copy ATI driver file from USB to /temp directory: sudo cp /home/ubuntu/USB/ati- /home/Ubuntu/temp

DO NOT attempt to run the driver installation from the USB mount.  It will fail.

•	Execute the driver setup: sudo ./ati....-run

•	Accept the defaults throughout the driver setup

Once the driver installation is complete you will be back at a prompt.  Run the following: 

•	sudo aticonfig –initial 

•	sudo aticonfig --overlay-type=Xv

These previous steps back up your existing X environment.

•	Run: sudo dpkg-reconfigure xserver-xorg

Accept all of the defaults for the dpkg command with ONE exception:  At the very first prompt, change selection from ATI to fglrx.

Once this is complete, the driver is installed.  To verify launch and editor with the following command:

•	sudo nano /etc/X11/xorg.conf

Verify that “Device” is set to fglrx. 

Exit the editor (CTRL X) and you will be back at a prompt.

•	To launch X, type start x

Once the GUI has launched, open a terminal window. Type the following command:

•	Fglrxinfo

The following should be displayed:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)

Your proprietary ATI driver is now installed.

You can also follow this process from a terminal window in order to update the driver on your Ubuntu install.  While the fglrx driver available from Xorg works, it lacks some of the 3D functionality of the proprietary driver.

This write-up is based upon information found at the following locations:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  

On the Ubuntu site they have you download the fglrx driver via apt-get using the following command:

sudo apt-get install xorg-driver-fglrx fglrx-control

To my knowledge this driver is NOT the ATI proprietary driver.  

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6-inst.html)

This site is linked from the driver download page.  It assumes that the installer package will be run from within the GUI and has no command based instructions.

---

### Post by meng on 2006-10-17
You may want to change the title to
HOWTO: <rest of title>
for the benefit of others.

---

### Post by Roobert on 2006-10-31
I have a question - if I go through all these steps and wind up even worse off than before, can you tell me how to remove the newly installed ATI drivers and revert back to square one?

---

### Post by l0rdz3r0 on 2006-10-31
i did all that steps 
from 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 

and when i got to this part 
add the following lines at the end of your xorg.conf

Section "Extensions"
        Option      "Composite" "0"
EndSection

Don't forget to save. You can reload xorg by pressing Ctrl Alt and Backspace simultaneously. 

after the ctr alt backspace 
i got it a black scren
any solution or i need to install it again
 by tha way my graphic card is ati radeon xpress 200M

---

### Post by sadalmelik57 on 2006-11-04
I've followed several guides to get my ATI Radeon 9800 Pro working with my Dell Dimension 8300 (P4, 3.06 gh, 512mb).  This post seems to most accurately describe the problem I am having so I've used it as my guide.

I'm doing fine until I get to "Execute the driver setup: sudo .ati...-run.

At that point I get the response: "ati-install.sh: 991 Syntax Error: Bad Substitution.  Removing temporary directory: fglrx-install."

Am I doing something wrong?

---

### Post by SubWolf on 2006-11-05
I'm suffering the same issue, and researching a fix now. If I find it, I'll let you know. ;-)

Edit - Found the solution here - [http://www.ubuntuforums.org/archive/index.php/t-243342.html](http://www.ubuntuforums.org/archive/index.php/t-243342.html)

And yeah, just running the installer specifying bash doesn't work, I had to actually move sh out temporarily.

---

