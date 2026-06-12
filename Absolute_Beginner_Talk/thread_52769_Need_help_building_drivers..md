---
title: "Need help building drivers."
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by Dural on 2005-07-28
I'm trying to install the atmel wireless drivers (July 2005) for a Linksys WUSB11 Wireless Adapter v 2.8. I have extracted the folder for said drivers into my home folder. I have spent the past 2 hours trying to build said drivers by using the instructions. First, I assumed that I would not have to use superuser to install the drivers, so I just typed into a regular terminal

#make
#make usb buildonly=debug
#make install

When I realized that nothing was happening, I added the command sudo before #make, but all that displayed was a series of examples showing how sudo could and could not be used. Then, I tried using su #make and I entered the password when the terminal requested it, but everytime it would display authentication error, even when the password was right.

I have reread the instructions given with the file several times, looked through the forums for Networkiing and on LinuxQuestions, but I still could not figure out how to build, then install these drivers. How can these drivers be built and installed in Ubuntu Hoary Hedgehog?

---

### Post by amohanty on 2005-07-29
Are you sure you dont need to do:
>> ./configure
in the source directory first???

If you cannot figure out, post the README or INSTALL for the drivers, or post the URL where I can download it and take a look.

Also you need to be su/root to run 
>> make install
primarily because it is likely this will try to copy files to /usr/bin /usr/lib etc which is not writable by regular users.

Also I would recommend that you use 'checkinstall' (install it via synaptic) instead of 'make install'. That way to remove the app you will not have to hunt all the files, just:
>> dpkg -r <driver package name>

HTH
AM

---

### Post by kspr on 2005-07-29
no wonder nothing happens if you try the command #make   ...you cant have a # in a command.. the '#' comments it out. try make instead.  ;)

---

### Post by poofyhairguy on 2005-07-29
you need build essential. Put this is regular terminal:

> sudo apt-get install build-essential

---

### Post by Dural on 2005-07-29
[QUOTE=poofyhairguy]you need build essential. Put this is regular terminal:[/QUOTE]
 To amohanty: Here's a copy of the readme.

[I]	Table of Contents
--------------------------------------------------------------------------------
I.	Kernel Compilation
II.	Building the Driver Modules
	i.	Building for 2.4.x Kernels
	ii.	Building for 2.6.x Kernels
III.	Setting up Configuration Scripts
	i.	./scripts/atmel.conf and ./src/includes/usb/config.h
	ii.	/etc/pcmcia/wireless.opts , /root/.vnetrc and /sbin/iwconfig
IV.	Loading the Driver
V.	Enabling Ethernet Interface
VI.	Applications
	i.	lvnet
	ii.	winter
	iii.	atmelup and fucd 
--------------------------------------------------------------------------------



STEP I: Kernel compilation
--------------------------------------------------------------------------------
NOTICE: Sometimes, you may not have to build your kernel manually. This happens
when you are so lucky that your precompiled kernel which your distribution uses
fullfills all the requirements mentioned below. However, in any case you still
have to obtain the kernel sources that correspond to your running kernel, and
put them in the right place.
To configure your kernel build options, in the kernel source directory
(most probably /usr/src/linux-2.x.x), do a `make menuconfig` under console
or `make xconfig' under X environment. (If no such dir exists, this means that
you have no kernel sources, and you have to install them)
The following parameters must be configured, in order for the driver to work:
- Loadable Module Support -> Enable (Module unloading is also recommended)
- Processor types and features -> Symmetric Multiprocessing Support - Disabled
- Device Drivers -> Networking Support -> Wireless LAN (non-hamradio)
        No further specific drivers need to be selected there.
- (PCMCIA only) Bus Options -> PCMCIA/CardBus support -> yenta-compatible.
        Select this only if you prefer to use internal card services
	Otherwise, When you build the external package pcmcia_cs,select i82365.
	You may have to edit /etc/sysconfig/pcmcia, filling the `PCIC=' field,
	with `i82365' or `yenta_socket', according to your selection.
- (USB only) The appropriate host controller interface has to be selected. 
	If unsure, select both ehci, ohci and alternate-uhci and you'll 
	later determine which one is actually used.
- (USB for 2.5 and 2.6) In order to make the driver work for 2.6 kernels,
	you have to download and install the reset-usb kernel patch.
	To make things easier, we provide a link to download the patch from 
	(atmelwlandriver.sourceforge.net/downloads.html).
	Gzip -d it, Copy the ungzipped file to /usr/src/linux-2.6.x and run:
	#patch -bf -p1 < patch_atmel_reset
	This keeps backups of the updated files, in case something goes wrong.
	After the patch has been applied, rebuild your kernel.

To find out if your kernel (custom or not) has these parameters configured as 
required, view the file /usr/src/<Your Running Kernel>/.config and check if the
following lines are the same. 
(they wont be found together, you have to search for each one of them)

CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y 		# recommended
# CONFIG_SMP is not set
CONFIG_NET_RADIO=y		# to enable wireless extensions
CONFIG_NET_WIRELESS=y

CONFIG_PCMCIA=m			# mandatory for pcmcia
CONFIG_YENTA=m			# if not using external cs
CONFIG_CARDBUS=m

CONFIG_USB=y			# mandatory for usb
CONFIG_USB_EHCI_HCD=m		# `=m' to all 3 HCI's is the least risky option
CONFIG_USB_OHCI_HCD=m		# therefore `=y' is not recommended.
CONFIG_USB_UHCI_UHCI_ALT=m	# you only need to select the one that suits you
				# but selecting all of them won't do any harm
				

WARNING: There are serious conflicts when our driver tries to cooperate with 
usb-uhci, that can lead to a crash. Using uhci (instead of usb-uhci)
is higly recommended. So, if your system starts with usb-uhci loaded 
(you can see this with lsmod), rmmod it and manually load uhci.o (or uhci-hcd.ko
for 2.5+ kernels). In kernel Configuration, select as module only the alternate
UHCI driver if your bus is of that type.


Some further info for linux newbies:
After having finished with kernel tweaking, do `make bzImage', `make modules'
and `make modules_install'.
(For 2.4.x kernels, `make dep' must be run after exiting `make config')
The kernel image shall reside in ./arch/i386/boot/bzImage and should be copied
to /boot directory. For GRUB, just adding a section (in /boot/grub/menu.lst)
containing the new kernel image, is enough to activate the newly compiled kernel
and to be able to load it when booting.

Fedora Core 2 Specific Tips:
Although there is already a precompiled kernel that meets the requirements, you
are strongly recommended to build your own. Having acquired the kernel sources,
do as usual a `make menuconfig', then just save and exit. You need not change
anything. Go on with the kernel building process, as described above in this 
chapter.
Having compiled and installed the atmelwlandriver, you are also suggested to 
disable the script /etc/sysconfig/network-scripts/ifup-wireless . You can do so
by commenting all it's lines. 



STEP II: Building the Driver Modules
--------------------------------------------------------------------------------
Unpack the tarball (tar jxvf) and change dir to atmelwlandriver.

There are 2 variations of Makefile architectures at the moment, depending on
which kernel version you intend to build the drivers. One for 2.6.x kernels and
one for 2.4.x and below.
In each case, make sure that you run every following command as superuser.

i) Building for 2.4.x Kernels

# make config
( `#' represents the superuser's prompt, whereas `$' is a normal user's one.
Either way, you don't have to type it :-)
A number of yes/no questions shall be asked, such as:
1. Build all
2. Set extra module version information
3. Build Debug version
4. Build USB Drivers
	a) Build USB 503A RFMD Driver
	b) Build USB RFMD 505 Driver
	c) Build USB RFMD 505+2958 Driver
	d) Build USB RFMD 505A Driver
5. Build PCMCIA Drivers
	a) Build PCMCIA rfmd Driver
	b) Build PCMCIA 3COM Driver
	c) Build PCMCIA rfmd revision d Driver
	d) Build PCMCIA rfmd revision e Driver
	e) Build PCMCIA 504 Driver
	f) Build PCMCIA 504+2958 Driver
	g) Build PCMCIA 504A+2958 Driver
6. Build miniPCI Driver
7. Build applications
        a) Build console-application (lvnet)
        b) Build X Windows application (winter)
8. Build Firmware Upgrade Tools

You have to find and select your device chipset amongst them. If you are unsure
about your device id, select and build every device of the corresponding bus 
(pci, pcmcia or usb) and you will find out which one is actually used when you
insert the device, by watching console output or the file /var/log/messages.
Except from specific chipset selection options, there are also some preferences
that apply to whatever driver you build. In each one of them, just pressing
enter means answering "no", which is usually safer. Furthermore, answering "yes"
to 2 is highly discouraged, unless you really know why you need that. It is also
recommended when trying the drivers for the first time, to build them in debug
mode (which means answering "yes" to 3), so as to determine easier whatever
malfunction is responsible for a potential error. Be prepared, however, for a
great console output. (this can be ceased by `echo 0 > /proc/sys/kernel/printk`)
The two applications accompanying the drivers are `lvnet' and `winter' and are
suited for console and X respectively. lvnet requires ncurses, while winter is a
wxWidgets app, therefore it needs wxGTX-4.2 or greater. Both must be run as root.

Having finished with the selections, order the building with
# make all
and finally run
# make install
This will copy the modules to a directory inside:
/lib/modules/<Your Running Kernel>/kernel/drivers/ , depending on the selected
bus, and shall report to module-init-tools about their existence, so that 
modprobe can find and load them, resolving their dependencies.


ii) Building for 2.6.x Kernels

# make 
This will display all the available build options:

Pick one of the following targets for KERNELS 2.X.X:
make clean	- remove all directories of object files
make device buildonly=argument 
		- where device = usb or pcmcia, argument = debug or release
make lvnet	- compile lvnet utility
make winter 	- compile winter utility 
make world	- compile all modules with debug and release information
make install	- install modules and programs
							
example:
# make pcmcia buildonly=debug 
Builds every pcmcia module with debug information 

It is generally recommended when trying the drivers for the first time, 
to build them in debug mode, so as to determine easier whatever
can be responsible for a potential error. Be prepared, however, for a
great console output. (this can be ceased by `echo 0 >/proc/sys/kernel/printk')
The two applications accompanying the drivers are `lvnet' and `winter' and are
suited for console and X respectively. lvnet requires ncurses, while winter is a
wxWidgets app, therefore it needs wxGTX-4.2 or greater.Both must be run as root.

Having finished with building procedure, run:
# make install
This will copy the modules to a directory inside:
/lib/modules/<Your Running Kernel>/kernel/drivers/ , depending on the selected
bus. Finally, run, as prompted:
# depmod -aeq
which shall report to modprobe about the modules' existence, so that it
can find and load them, resolving their dependencies.



Possible Complications:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
i) An error was encountered during `make all', hence building has been aborted.
This usually happens with newly introduced kernels. Apparently, something in the
linux kernel has changed or is no longer where it was expected to be. It could
be a header file or a variable name that has changed, or a function's parameters
that differ. A common cause of that error is the use of custom kernel sources
provided along with a distro, even for an older kernel version.
This is not surprising, since the linux kernel is a totally dynamic collection
of drivers. What you have to do, anyway, is:
Check out if you have the complete kernel sources of the same version with your
running kernel. If there are reports for a missing file, check if the file 
exists in another path than that where it is expected to be found, and try to
resolve the conflict manually. (a symbolic link would be fine)
Whether the problem was solved or not, please send us a report, describing the
error you encountered (see Appendix I: Reporting Errors)

ii) Make install fails.
The most common cause of this, is missing the directory where the modules should
be copied. Try to find if your modules were actually copied somewhere inside 
`/lib/modules/<Your Running Kernel>/' and if not, copy them manually to the
place where modules of this category reside. This should be `./pcmcia/', 
`./kernel/drivers/net' or './kernel/drivers/usb/' or so. Then depmod -a to 
inform modutils about the change.

iii) `depmod -a` fails.
If you receive the message `depmod cannot be found' the execute `su -' and 
`make install' again. If you notice some errors when running depmod, make sure
they have to do with the driver. In the case that they really have, then this
means that the module wouldn't be able to load anyway. Check the requirements
mentioned in Step I, try to determine which modules contain the missing
variables that depmod complains about, and rebuild your kernel to enable those
modules. Before rebuilding, it would be a good idea to insmod the driver just
to see if you can get more evidence about what's going wrong.
(or even insmod -f for risky ones, which forces the module to load, but
increases the chances for a complete crash)



STEP III: Setting up Configuration Scripts
--------------------------------------------------------------------------------
i) ./scripts/atmel.conf	./src/includes/usb/config.h
Atmel.conf contains all the information that lets your system know which driver
it should load for any pcmcia atmel wlan device.
Therefore, editing it can serve a very specific purpose:
If no driver is loaded for your pcmcia wlan device, but you know for sure that
it contains an atmel chipset (you can visit linux-wlan.org to verify it) then
you have to add it on your own. First do a `cardctl ident' with your card
inserted. This will give an output of such form:
....
Socket 1:
	product info: "CARD's VENDOR", "YOUR DEVICE ID"
	manfid: 0x0000, 0x0000
	function: 6 (network)
From the above, we keep the `product info' field. That's all we need.
To make your card recognizable, you have to add a registration to atmel conf:
card "YOUR DEVICE NAME"
	version "CARD'S VENDOR", "YOUR DEVICE ID"
	bind "pcmfxxxx"
In the third line, `bind' command defines the module that should be loaded upon
card insertion. To activate changes you have to run `make install' again.
You can send us a report with the lines of your card's registration, to be
included in atmel.conf for everybody.

./src/includes/usb/config.h, serves the same purpose, with the difference that
it is compiled into the drivers, so editing it without rebuilding is not 
sufficient to apply your changes. For usb devices, use lsusb, or watch the 
output of dmesg, or follow /var/log/messages to identify card's vendor and id.


ii) /etc/pcmcia/wireless.opts , /root/.vnetrc and /sbin/iwconfig
The files wireless.opts (for PCMCIA) and .vnetrc (for USB) are the startup
scripts for your card, if wireless extensions are enabled.
Don't worry, you 'll know if they aren't enabled. Nothing else regarding the
wlan would work without the extensions. You can run `#/sbin/iwconfig' to make
sure about it. If wireless extensions are disabled, this means that you have to
read `Step I' even more thoroughly, especially the part about enabling Wireless
LAN (non-hamradio).  As you'll see from the given examples within the script,
whatever parameter you need to be set upon card insertion, you can add it there.
To see the state of your card when you plug it, you can always run iwconfig
(prior or post to setting up wireless.opts). iwconfig can also be used to set
values at will, and that's what these scripts actually do.



STEP IV: Loading the Driver
--------------------------------------------------------------------------------
If the drivers are compiled and installed properly, then upon card insertion the
driver will be automatically loaded, as well as any module that it requires.
For pcmcia devices, when inserting the card right after `make install'
(without restarting any service) it may seem that nothing happens. You have to 
run: `/etc/init.d/pcmcia restart' for changes to take effect, or load the driver
manually with `modprobe pcmfxxxx`.
For usb, make sure, before plugging in the card, that the appropriate host 
controller module has been loaded. Use lsmod to verify it.

Possible Complications:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
i) When I insert my pcmcia mac, my system crashes.
Try to reconfigure cardbus support, editing /etc/sysconfig/pcmcia.
(/etc/defaults/pcmcia for debian). Play with n value of the field
PCIC_OPTS="irq_mode=n". Alternate yenta_socket and i82365.
If still in trouble, send a report to the mailing list.

ii) When I insert my usb mac, the system crashes.
The most common reason for that, is the conflict with `usb-uhci' module.
This is the driver for the universal host controller interface. There are two
different architectures for usb v.1 controllers: usb-ohci and usb-uhci.
You can't do without that. Except of course your system uses ohci, but if it 
doesn't, you can't change that. Luckily, there is one more driver for uhci, 
the `uhci' module (instead of `usb-uhci'), known as the `alternate driver',
for that specific bus. It doesn't matter what brand your motherboard is. AFAIK,
wherever `usb-uhci' works, bare `uhci' also does. But if you desire to see your
wlan card working, and your system not crashing upon card insertion (or a couple
of seconds later), only `uhci' will do. What you have to do anyway is:
#lsmod
This will display this list of loaded modules. If usb-uhci is in there, use 
#rmmod usb-uhci 
to release it from your services. Then type:
#modprobe uhci	, to load the proper module.
Note that module names may vary a little, `-'s can be `_'s, or a postfix -hcd
may be present. In any case, you can distinguish `uhci' from `usb-uhci'.
In order to avoid doing this every single time your system starts and you need
to plug in your card, you have to edit `/etc/modules.conf' file and replace a
line like this: (you can easily find it with #grep -n "uhci" /etc/modules.conf)
alias usb-controller (or usb-interface or whatever)	usb-uhci
with a line like that:
alias usb-controller	uhci
Do I need to say that names may also vary? In the rare condition that your 
system is not configured to load a usb controller driver upon startup, you
may find no such line at all. 
Finally, if you are building your own kernel, remember to configure the ?hci 
driver to be built as a *module*. This may save you from potential crashes.
FYI, the conflict with `usb-uhci' driver is due to its inability to reset 
our device properly. This leads our device to a reset-but-not-reset state
from which it never recovers, and the system cannot determine that a device
has been plugged in.

iii) Nothing happens upon card insertion.
If your card is of pcmcia type, the commands `cardctl status' and
'cardctl ident' may help you figure out what's going on. Ejecting and 
reinserting the card may help under problematic controllers or slots.
Restart pcmcia services, watch the file /var/log/messages, lsmod to see if the
driver has been loaded and, if not, load it manually.



STEP V: Enabling Ethernet Interface
--------------------------------------------------------------------------------
The ethernet name of the device is atmlN, where N is 0,1... depending on how 
many atmelwlan devices you have installed. Those being experienced with the
drivers in the past, will remember it taking common ethN names. However,
changing name was important for the interface to be easier distinguished.
Since there is no premade network script for atmlN devices, a good practice 
would be to find ifcfg-eth0 and make a duplicate of it onto ifcfg-atml0 and so
on. You shall need to modify it, according to your local network configuration.
The directory containing such network scripts varies.
(it  is /etc/sysconfig/network-scripts/ (redhat) or /etc/sysconfig/network/
(suse), or /etc/find_it_yourself)
An example of how ifcfg-atml0 should look like, is this:
DEVICE=atml0	# working with "alias atml0 <your device driver>" in 
		# /etc/modules.conf for automatic loading
BOOTPROTO=dchp	# or `static', if you wish, followed by an IPADDR=... setting
ONBOOT=no	# had better get enabled when plugging in the card

Having configured your network scripts, run `/etc/init.d/network restart' 
and `ifconfig atml0 up' to activate the atml0 interface.

Running then `ifup atml0' will suffice to get an ip address, if your network 
services have been set up properly.

Note:
Several system scripts regarding network activities such as firewalling, 
virtual private networking, routing, etc, have been customized for ethN names.
To make your atmlN interface behave like an ethN, you have to add atmlN entries
to them, taking as examples the existing ethN ones.



STEP VI: Applications
--------------------------------------------------------------------------------
i) lvnet
Lvnet is a console, ncurses-faced utility to configure your wireless nic.
To avoid problems, you have to run it as root, under a real tty. (not an X one).
It provides five tabs: View Config, Advanced, Security, Configure Card and 
Site Survey. You can navigate through them using left and right arrow keys.
"View config" will display an output similar to running `#/sbin/iwconfig',
containing values that indicate the state of your device.
"Advanced" tab contains more specific-purpose parameters for advanced users.
"Security" lets you set WEP keys, level, transmission key and authentication 
type, in order to associate to an AP that requires encryption.
In "Configure Card" you can set almost every writable setting of the card.
Finally, in "Site Survey", you can scan for access points and connect to any one
of them, if you can authenticate your connection.
F1 key exits a tab or terminates the program, if not inside a tab.

ii) winter
Winter is an X application, made with wxWidgets (former wxWindows) that provides
a visual environment to configure and manage your card. To be able to build it,
you need to have wxGTK-4.2 or greater. It's functionality is similar to that of
lvnet, extended by very useful features such as profiles, localization and
support for more than one devices simultaneously.

iii) atmelup and fucd
These are both firmware upgrade tools, for console and X correspondingly.
The requirements of fucd are the same as those of winter, since they are both
powered by wxWidgets. Atmelup takes a single argument to run, which of course is
the .rom file containing the new firmware for upgrade. Do not ever use any other
file type. (fwr*.h are NOT conventional .rom files, so please do NOT use them)
Although a firmware upgrade is a simple matter of 3 minutes, great care must be
taken, for a single mistake can make your device totally, completely and
unrecoverably useless. Avoid running any wlan monitor app, since during the
upgrade, the card's drivers are unloaded. A known issue: In fucd, you cannot
separate two devices of identical type, when trying to select which one to
upgrade. The safest way in this case, is to unplug the one that does not need
upgrading, and rescan the usb busses, rather than trying to guess which one
comes first.


Possible Complications:
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
i) My system starts on X, but I insist on running lvnet. When trying to run it 
on a virtual terminal, it exits without any sign or warning. What shall I do?

<Ctrl>+<Alt>+<F1-6> switches to a system console. <Alt>+<F7> gets you back to X.
In a real console, you can run lvnet without problems concerning its appearance.
You can also try to maximize a virtual terminal, and see if lvnet runs.

ii) I can't start winter because of a stale lock.
This file prevents more than one instances of winter running at the same time. 
It is created when winter starts, and it is deleted when winter exits. However,
if the program crashes, (which will most probably happen if you detach your 
device while working with winter), the stale lock is not deleted. You can always
delete it manually.



Appendix I: Reporting Errors
--------------------------------------------------------------------------------
There are two mailing lists, hosted by sourceforge, that support atmelwlandriver
One for user questions, error reports, etc:
	[email]atmelwlandriver-users@lists.sourceforge.net[/email]
and one related to developer issues: 
	[email]atmelwlandriver-develop@lists.sourceforge.net[/email]

Things you need to specify when reporting an error to the users mailing list:
- Your linux kernel version
- The name of your distribution
- Your chipset id and the driver module that it uses, or should be able use.
- Your driver build configuration. Only the options you enabled are needed,
  ie. pcmcia - 502rfmd, debug.
- Your gcc version (if the error occured during driver compilation)
- The output of lsmod and lspci.
- Your usb or pcmcia controller and the name of the driver it uses.
- The error log, at the time that it happened. You may have to build the debug
  version of the drivers, in order to obtain a complete and descriptive error
  log, that 'll help us determine the nature of the problem. Also try to include
  the actions that were performed before the error occurred. OTAH, try to be
  specific: endless logs that contain useless information cause mailing
  pollution, thus they are not recommended.
- If there is a specific application facing problems, you could mention its
  whereabouts (ie. is it an Xapp or a console one? does it need some specific
  firmware or driver features?)


author: Titos Mpetsos (tmpetsos@patras.atmel.com)
Feel free to send any corrections, suggestions, reports...regarding this readme.
Many thanks to all you guys supporting the atmelwlandriver mailing lists.

[/I]

I know it's kind of long. I tried to look for the .config file that was mentioned in the readme (/usr/src/<kernel version #>/.config but I could never find it, even after searching the whole filesystem. I suspect I might have to boot into root and see, but I am not sure if that is necessary.

To poofyhairguy and kspr: I'll try your suggestions and see what happens. I hope this will work :).

---

### Post by poofyhairguy on 2005-07-29
Without build-essential installed, you can't "make"

---

### Post by Dural on 2005-07-29
Okay, I installed build-essential through Synaptic since apt-get wouldn't work (kept givng a E: Invalid Operation Build message). 

I don't have checkinstall in Synaptic for some strange reason, so I don't know whether using dpkg would be easier to use instead of going by the commands mentioned in the readme.

---

### Post by amohanty on 2005-07-30
I think checkinstall is in backports??? I am not sure.

Based on the README:
(NOTE: >> is the command prompt, type only whats after that)
>> make config
>> make
>> sudo make install OR 
>> sudo checkinstall 

That will install your drivers, then follow instructions in the README.

HTH
AM

---

### Post by Dural on 2005-07-30
[QUOTE=amohanty]I think checkinstall is in backports??? I am not sure.

Based on the README:
(NOTE: >> is the command prompt, type only whats after that)
>> make config
>> make
>> sudo make install OR 
>> sudo checkinstall 

That will install your drivers, then follow instructions in the README.

HTH
AM[/QUOTE]
 I typed in this command:
make config

And got this response:
make: ***No rule to make target 'config'. Stop.

Then I tried this command and added the name of the driver:
make config atmelwlandriver

And got the same response (make: ***No rule to make target 'config'. Stop.)


I tried a third time, including the address the driver folder was extracted (/home/<my user folder/atmelwlandriver), and it still refused to make the config file. 

I think I got some of the backports through the Unofficial Ubuntu Add-On CD, but I don't think it included checkinstall.

---

### Post by amohanty on 2005-07-30
Sorry my bad... I misread the README. Heres the corercted version:

Based on the README:
(NOTE: >> is the command prompt, type only whats after that)
>> make pcmcia, builonly=release

>> sudo make install OR
>> sudo checkinstall

>> depmod -aeq


Sorry again.

AM

---

### Post by Dural on 2005-07-31
[QUOTE=amohanty]Sorry my bad... I misread the README. Heres the corercted version:

Based on the README:
(NOTE: >> is the command prompt, type only whats after that)
>> make pcmcia, builonly=release

>> sudo make install OR
>> sudo checkinstall

>> depmod -aeq


Sorry again.

AM[/QUOTE]
 Tried the same intstructions in your post, but I still got the ***No rule to make target message. I don't know what else I can try. :(

---

### Post by Dural on 2005-07-31
I went to this site [](http://www.niemueller.de/projects/extrpms/) and found some instructions in the forums to convert a .rpm file of these drivers to .deb. Then, I used the sudo dpkg -i command to install them. Now, all I need to do is to figure out where to go next. After installing a .deb set for drivers, how do you activate them?

---

### Post by amohanty on 2005-07-31
>> depmod -aeq

This will rebuild your modules map.

>> lsmod
 This will list all loaded modules. Find the one that looks like yours. One you have it, look in /etc/modules and see if it isthere. If not insert the name at the end.

reboot.

HTH
AM

---

### Post by Dural on 2005-07-31
[QUOTE=amohanty]>> depmod -aeq

This will rebuild your modules map.

>> lsmod
 This will list all loaded modules. Find the one that looks like yours. One you have it, look in /etc/modules and see if it isthere. If not insert the name at the end.

reboot.

HTH
AM[/QUOTE]
 I typed in depmod -aeq and it seemed that the drivers had installed.The terminal showed the same command prompt, so I typed in lsmod, but I could not find the module in the list.  I found the drivers under the folders /lib/modules/2.6.10-5-386/kernel/drivers/net/wireless and /lib/hotplug/firmware. The files were named atmel.ko, atmel_pci.ko, and atmel_cs.ko, along with various binaries in the hotplug folder with the name atmel in them. However, when I typed in lsmod and lsusb, my adapter was still identified as an unknown USB device.

---

### Post by amohanty on 2005-07-31
You probably want to add
atmel
atmel_pci
atmel_cs

at the end of /etc/modules. Reboot and do:
>> lsmod | grep atmel

AM

---

### Post by Dural on 2005-07-31
I saw the modules text file, and I attempted to edit it but I do not have write access to the file. Is there a way to temporarily access the file as superuser or root?

---

### Post by amohanty on 2005-07-31
>> sudo gedit /etc/modules

It will prompt you for your password.

AM

---

