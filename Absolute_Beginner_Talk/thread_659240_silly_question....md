---
title: "silly question..."
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-05
propably because i'm not very familiar with computer engineering i have a  question:
when a device is interacting with the pc like a  modem router/wifi/mouce whatever.... ,some of them need a driver and other do not.
propably when it needs a driver ,this is provided by the ubuntu database(i guess..)
but when it has build in driver in what level can automaticaly interact with ubuntu?

is there any way to check it out?

---

### Post by ubuntu-freak on 2008-01-05
Not sure what you mean exactly. Every device needs a driver in one form or another. Some are preinstalled by Debian/Ubuntu and others are installed during installation when Ubuntu detects the specification of your hardware. Others need installing or compiling as you start plugging different devices into your USB sockets. 
  
Are you looking for a way to monitor how devices are detected when you plug them in? You can use the terminal I think (On my phone so can't check). 

Nathan

---

### Post by yelvington on 2008-01-05
Ubuntu includes a large collection of drivers for most common hardware items, such as mice, display cards, monitors and network cards. In most cases there are standards through which devices can identify themselves on the USB bus, PCI bus, etc., and if a device can be supported, Linux will load the appropriate driver to enable it.

But many new devices appear every year, and some manufacturers are very bad about Linux support (to the point of active hostility). There's always a chance that some item like my wife's Lexmark printer will turn out to be a doorstop.

Right now the biggest area where you're likely to run into trouble is wi-fi networking. Many devices are detected and Linux works great, but if yours doesn't happen to be supported, your best bet is to head to the store and buy a replacement. Sometimes it's possible to use Windows drivers through the Linux NDISwrapper utility, but such setups tend to be less stable than real Linux drivers.

---

### Post by HermanAB on 2008-01-05
Linux is modular.  You can  always see what modules (including device drivers) are installed with 'lsmod'.  Modules can be loaded/unloaded on demand, without restarting the system.

---

### Post by someoneouthere on 2008-01-05
for example lets say that a device is allready installed how can i check out the permissions that the particular device has like write-read/send-recieve and where it is doing that...?

---

### Post by zipperback on 2008-01-05
> **someoneouthere said:**
> propably because i'm not very familiar with computer engineering i have a  question:
when a device is interacting with the pc like a  modem router/wifi/mouce whatever.... ,some of them need a driver and other do not.



All your devices have drivers.

The most commonly used hardware drivers are included by default in Ubuntu.

However, sometimes you have to download and build the drivers from source, while others offer a binary only version of their driver. A binary only version of a driver, is considered to be a closed source driver, and it is generally avoided when possible, however sometimes there is no other option for it.

If you have a piece of hardware that works for you with a default installation of Ubuntu, then it means that support for your hardware (* the driver ) has been included in the distribution.

The following commands are useful to determine what kinds of modules are being used, and what kind of hardware is being recognized by your system.

```

lsmod

lspci

lsusb

```

lsmod will show you the modules in use on your system.
lspci will show you the pci based devices in your system.
lsusb will show you the usb based devices in your system.

For more information on these commands you can read over their man pages.

```

man lsmod

man lspci

man lsusb

```

If you have additional questions, please feel free to ask.

- zipperback
:popcorn:

---

### Post by someoneouthere on 2008-01-05
ok because i have no expierience on these things so i cannot actualy undenstand the all the output in terminal... 
lets say i want to check out the preferences-properties of the modem router
so how do i proceed?

---

