---
title: "Help with modems.."
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by tripleriver on 2007-05-02
hi,
i m having problems configuring any of my 2 modems.
[COLOR="Red"]Modem No. 1 Lucent winmodem with Agere Dsp.[/COLOR]
DId everything in Lucent page on [https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

here's what: 

$ sudo sh -c "echo ltserial >> /etc/modules"
$ sudo sh -c "echo ltmodem >> /etc/modules"
 

Now load the drivers for the first time:

  $ sudo modprobe ltserial
  $ sudo modprobe ltmodem

[COLOR="Red"]*When I did this said that; FATAL: module not found" for this step  *[/COLOR]

This should have created the device /dev/modem and you can now go on to configure your dialup connection.

No, I get an error about "FATAL: module not found" for this step :(

Note for "5.04 Hoary" users: Ubuntu 5.04 Hoary was shipped with kernel 2.6.10, which has some problems with these modules. To fix, change the grub boot commands /boot/grub/menu.lst as follows (pci=routeirq is new):

  ## ## Start Default Options ##
  ## default kernel options
  ## default kernel options for automagic boot options
  ## If you want special options for specifiv kernels use kopt_x_y_z
  ## where x.y.z is kernel version. Minor versions can be omitted.
  ## e.g. kopt=root=/dev/hda1 ro
  # kopt=root=/dev/hda1 ro pci=routeirq

Do not forget to update grub: $ sudo update-grub

[COLOR="Red"]*Again I get FATAL: module not found" for this step *[/COLOR]

Also when I tried to install martian could not load in modules. On $ make it was getting general errors at the end.

[COLOR="Red"]-Modem No. 2  External usb Diamond Supra Max[/COLOR]
Used scanModem which turn out nothing. Haven't been able to find out if it's a winmodem or not.

Having ubuntu 7.04

I would greatly appreciate any help for configuring any of the two and be able to connect!
thks!

---

### Post by lamalex on 2007-05-02
```
cat /etc/modules
```
ltserial
ltmodem

are in there. if they're not, add them and try starting from the step where you insert them

---

### Post by lamalex on 2007-05-02
also did you do this?
```

sudo apt-get install linux-restricted-modules-`uname -r`

```

if not, do it

---

### Post by tripleriver on 2007-05-03
the linux-resctricted- modules are installed.

here's some outputs that might give some idea\

$ wvdial

--> WvDial: Internet dialer version 1.56

--> Cannot open /dev/modem: No such file or directory

--> Cannot open /dev/modem: No such file or directory

--> Cannot open /dev/modem: No such file or directory



$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.

#

# This file contains the names of kernel modules that should be loaded

# at boot time, one per line. Lines beginning with "#" are ignored.


fuse

lp

ltserial

ltmodem

ltserial

ltmodem




/$ sudo modprobe ltserial
FATAL: Module ltserial not found.

/$ sudo modprobe ltmodem
FATAL: Module ltserial not found.

~$ wvdial -c
--> WvDial: Internet dialer version 1.56

--> Initializing modem.

--> Sending: ATZ

--> Sending: ATQ0

--> Re-Sending: ATZ

--> Modem not responding.


Also installed martian according to instructions.same above..

:confused:  and it's getting really hopeless to set up and frustrating going to other systems all the time to get in web. moreover i can't understand ubuntu structure. trying to use gnome-ppp but can't. is this already installed on the basic distribution or it has to be installed (& how)?

would appriciate step to step instuctions if possible.

is there a chance that the external modem may be easier? any ideas?

---

### Post by WallyT on 2007-06-19
This is exactly the problem that I'm having with my modem. I just recently upgraded from Dapper (via Edgy) to Feisty. My modem worked in both Dapper and Edgy after configuring. Now in Feisty, the modem is not detected by the dialup software. The system finds it without a problem, but I've tried pppconfig/pon, wvdial, and GnomePPP without sucess. Is there a solution that I'm missing on this forum or is it an issue that has no answer. Do I need to revert to a previous version to get my internet working again? Other choices such as buying a new modem, and getting broadband are not options at this time.

---

