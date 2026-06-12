---
title: "ATI Radeon HD 2400 Pro"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Bill60643 on 2007-12-23
I just put together a new computer, AMD 64/2 5000 and picked up the ATI 2400.  So far it does not work.  It boots and dumps me to a text mode.  Does any one know if this card is workable, or just replace it with a Nvidia.  My primary reason for geting it was the HMDI interface. I should also add that while I have played with Linux for a while, I am very much the novice. Any help would be appreciated.

---

### Post by blueridgedog on 2007-12-23
Was this a clean install of Ubuntu on this machine with this card or was the card added after the system was running?

---

### Post by tgilber1 on 2007-12-23
> **Bill60643 said:**
> I just put together a new computer, AMD 64/2 5000 and picked up the ATI 2400.  So far it does not work.  It boots and dumps me to a text mode.  Does any one know if this card is workable, or just replace it with a Nvidia.  My primary reason for geting it was the HMDI interface. I should also add that while I have played with Linux for a while, I am very much the novice. Any help would be appreciated.

I have a 2400HD card that works fine using Ubuntu Gutsy, but it only works with ATI prorprietary driver.  ATI's driver creates a kernel object module (fgrlx.ko), which Ubuntu loads fglrx.ko module during boot up.  The file is located in the /lib/modules/<kernel version - uname-r>/kernel/drivers/char/drm/fglrx.ko

The version that comes with Ubuntu is an Xorg driver that is created by the Xorg developers.  The Xorg drivers (radeonhd_drv.so & radeonhd_drv.ls) are libraries rather kernel objects that are placed in the /usr/lib/xorg/modules/drivers/ and /usr/lib64/xorg/modules/drivers/directories (64-bit platform).  However, I cannot get the xserver or gdm to come up.  It reverts to the xorg.conf.failsafe configuration, which loads the vesa driver.  The bottom line with the ATI's 2400HD card is the xorg driver.  X does not recognize the card.  I get an error message:  

"(EE) RADEONHD(0): Cannot map connectors on an unknown card!"  

With Ubuntu, if the primary xorg file fails to load, it reverts to the failsafe xorg.conf file.  It should prompt you to continue, shutdown, or configure.

I submitted the error and card type to the xorg radeonhd developers mailing list . . . waiting for response.  I am hoping the problem is a quick fix for them to code.

Another error I got was read-edid was not installed - cannot retrieve EDID.  This error message is bogus on AMD systems, since the read-edid package works only with Intel and PPC platform.  I believe the script /etc/gdm/failsafeXServer needs to be reworked to check and verify platform.  If non-Intel or PPC, then do not send read-edid error, thereby not leading people on wild-goose chase.

You can use the vesa driver by replacing the driver info in the /etc/X11/xorg.conf file under the device section.  However, if you want to use more of the card's capabilities, then you will have to install the proprietary version.

In any event, to install the proprietary verison at the following URL:  

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html).

[LIST=1]
[*]Download ATI's 2400HD driver
[*]Using the terminal #Applications#Accessories#Terminal
[*]Type vi /etc/default/linux-restricted-modules-common and add fglrx to disabled modules line (DISABLED_MODULES="nv fglrx") 
[*]The previous line prevents Ubuntu from trying to search and load its fglrx version
[*]Make sure the ubuntu fglrx driver is uninstalled - "sudo apt-get purge xorg-driver-fglrx"
[*]sudo ./ati-driver-installer-7-11-x86.<PC-type - AMD/INTEL>.run
[*]Accept all the default settings - Automatic installation
[*]Type sudo aitconfig --initial -f
[*]sudo /etc/init.d/gdm restart or reboot with sudo shutdown -r now
[/LIST]


You should be all set at this point


Lastly, if you continue to have errors.  You can see exactly what your errors are by checking your log files located in the /var/log/gdm/ directory.  You will see a few log files:  \:0.log, \:0.log.1, \:0.log.2, & \:0.log.3.  Make sure you view them using your favorite editor or viewer.  If you're opening the files from terminal, you need to start with a backslash (escape character) to signify that the colon is to be taken literally.  The colon is special  character when not escaped.  In any event, check for lines that start with EE, which denotes that the line is critical in xorg.conf file.  The lines with WW are warnings that should not prevent X from starting.

Sorry for the details, just want to post this info for anyone that is new to Ubuntu or Linux.  It may save them a lot of grief with xorg and linux.

---

### Post by CuBone on 2008-02-10
I tried this solution and it installs ok but there is no signal on tv-out. I don't have any monitor connected to my pc only a tv that's connected to tv-out. 

I can see my desktop if I connect via vnc and the catalyst control center seems to work. Catalyst finds the tv and it looks like it's configured properly.  Any ides on how to get my tv-out working?

---

### Post by ScottLind on 2008-02-10
> **tgilber1 said:**
> 
In any event, to install the proprietary verison at the following URL:  

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html).

[LIST=1]
[*]Download ATI's 2400HD driver
[*]Using the terminal #Applications#Accessories#Terminal
[*]Type vi /etc/default/linux-restricted-modules-common and add fglrx to disabled modules line (DISABLED_MODULES="nv fglrx") 
[*]The previous line prevents Ubuntu from trying to search and load its fglrx version
[*]Make sure the ubuntu fglrx driver is uninstalled - "sudo apt-get purge xorg-driver-fglrx"
[*]sudo ./ati-driver-installer-7-11-x86.<PC-type - AMD/INTEL>.run
[*]Accept all the default settings - Automatic installation
[*]Type sudo aitconfig --initial -f
[*]sudo /etc/init.d/gdm restart or reboot with sudo shutdown -r now
[/LIST]


You should be all set at this point


Hi there.
I've also got the ATI HD2400 Pro card, but I am really new to Linux and I need some help.
When I type "sudo ./ati-driver-installer-8-01-x86.<AMD>.run" - Nothing happens. I'm logged in a root. I have downloaded the new 8.01 version of the driver and my PC-type is AMD. - Can you please help me?

---

### Post by chajuram on 2008-04-06
> **ScottLind said:**
> Hi there.
I've also got the ATI HD2400 Pro card, but I am really new to Linux and I need some help.
When I type "sudo ./ati-driver-installer-8-01-x86.<AMD>.run" - Nothing happens. I'm logged in a root. I have downloaded the new 8.01 version of the driver and my PC-type is AMD. - Can you please help me?

You have to remove the > <AMD> by what it there in the name of the file. USe "tab" twice after you type > sudo ./ati-driver-installer-8-01-x86. that should prompt you the options available, choose the one you need. 

Chajuram

---

