---
title: "please help setting up my mouse"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by blodorn on 2007-10-31
I am very new to linux. I have Xubuntu 7.10, and a Razer Deathadder mouse. I found this website [http://bu3sch.de/deathadder.php](http://bu3sch.de/deathadder.php) and downloaded deathaddercfg-004.tar.bz2 After extracting the file, I read the README (pasted below) and installed the dependencies, but after that I do not understand how to set it up.

```
== Razer DeathAdder Mouse configuration tool ==

This is a configuration utility for the Razer DeathAdder on Linux systems.
You can control the LEDs, scanning resolution and frequency and profiles
with this tool. In future things like firmware upload are also planned.

= DEPENDENCIES =

 o libusb
 o libconfig

To install the dependencies on Debian or Ubuntu Linux, do
   apt-get install libusb-dev libconfig0-dev

libusb can be found at:
   [http://libusb.sourceforge.net/](http://libusb.sourceforge.net/)

libconfig (and libdebug, on which libconfig depends) can be found at:
   [http://oasis.frogfoot.net/code/](http://oasis.frogfoot.net/code/)

= BUILDING =

Simply invoke "make" in the extracted sourcecode tree.

= INSTALLING =

  make install

If you want to install it to a special directory prefix, do
  make install PREFIX=/foo/bar

= UDEV / AUTOMATIC CONFIGURATION =

The file "udev-deathadder.rules" in this package contains example rules
on how to handle automatic configuration through udev.
Note that you _must_ pass --no-rebind when calling deathaddercfg from udev.
Otherwise it might result in an infinite autoconfig-loop.
On Ubuntu Linux you need to
   cp udev-deathadder.rules /etc/udev/rules.d/01-deathadder.rules
to install the rules. Note that you might have to adjust the RUN path in
the .rules file, if you used another PREFIX for make install.

= DISTRIBUTIONS =

To create a proper binary distribution package, make sure a default
configuration file is installed to /etc/deathadder.cfg . You can use
the example file example_config.cfg from this package as a starting
point. You should also install a proper udev autoconfig rule to
your udev rules. See udev-deathadder.rules for an example rule.
```

---

### Post by blodorn on 2007-10-31
If some would could please help me do what these instructions are telling me to do, I would very much appreciate it. This is what I do not understand. What is the extracted source code tree? Do I need to do "make" and "make install"? What does it mean "On Ubuntu Linux you need to
cp udev-deathadder.rules/etc/udev/rules.d/01-deathadder.rules
to install the rules."?

---

### Post by Dominaduro on 2007-10-31
by "tree"

they just mean go to the directory (in a terminal) where the source code is. Then just type "make" and hit enter. You should probably type "./configure" first otherwise you won't know why "make" is complaining (if it does).

"make install" just installs it after it's done building (which you might want to have root privileges to do, u will prolly need to enter a password otherwise you might get some Permission Denied's).

---

### Post by Maestro23 on 2007-10-31
You will need **build-essential **installed first. Open a terminal:

> sudo apt-get install build-essential

If you need root privileges, you will need to use the** sudo **command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by blodorn on 2007-10-31
I succeeded in building, installing it to the default dir /usr/local/bin, and putting the rules file into /etc/udev/rules.d

```
#
# Example configuration file for the
# Razer DeathAdder configuration tool
#

# define default parameters for all detected DeathAdder mice
glowlogo	= true
glowwheel	= true
resolution	= 1800	# DPI
frequency	= 1000	# Hz

# Optionally you can define mouse-specific configuration values
# These values will override default values above
#mouse0 = {
#	# You must specify an ID to identify the mouse in the system
#	# You can use the USB busid. These are the two IDs found in
#	# /proc/bus/usb. The first number is the proc directory number.
#	# The second number is the device filename number in that dir.
#	id		= { "busid", "001-006" }
#	# However, using the busid is dangerous, as it may change
#	# over hotplug events.
#	# You can also specify a USB-Vendor-ID:USB-Product-ID pair.
#	# See lsusb to get the ID value pair.
#	# Note that the config is applied to all connected mice with this ID pair.
#	id		= { "devid", "1532:0007" }
#
#	glowlogo	= false
#	glowwheel	= false
#	resolution	= 900	# DPI
#	frequency	= 1000	# Hz
#}

#mouse1 = {
#	id		= { "devid", "cafe:babe" }
#	glowlogo	= true
#	glowwheel	= true
#	resolution	= 450	# DPI
#	frequency	= 500	# Hz
#}

```

Do I need to imput those values into 01-deathadder.rules (below)? Or some other file?

```
# Configure the Razer DeathAdder mouse
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="1532", SYSFS{idProduct}=="0007", RUN+="/usr/local/bin/deathaddercfg --no-rebind -C"
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="1532", SYSFS{idProduct}=="0003", RUN+="/usr/local/bin/deathaddercfg --no-rebind -t krait -C"

```

I want these values:

```
glowlogo	= false
glowwheel	= false
resolution	= 1800	# DPI
frequency	= 1000	# Hz
```

---

### Post by blodorn on 2007-10-31
I tried putting it in the 01-deathadder.rules and it did not work. Any info on how to use my mouse would be appreciated.

---

### Post by IsKall on 2008-02-24
Any success on driver installation on your deathadder?

---

