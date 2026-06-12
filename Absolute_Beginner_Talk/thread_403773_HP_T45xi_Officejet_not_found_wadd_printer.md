---
title: "HP T45xi Officejet not found w/add printer"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by banksw on 2007-04-07
My HP printer  is not detected by 6.10.  The port is set to ECP in the device mgr.  When i run hp toolbox i get the following:

HP Linux Imaging and Printing System (ver. 1.6.9)
HP Device Manager ver. 6.2

Copyright (c) 2003-6 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 16HP Officejet6
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
firefox

I have installed all recommended packages but still it is a no show?
newbie walt

---

### Post by mikeyphi on 2007-04-08
Hi 

If that's a HP Officejet T45 you need drivers from here - [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_T45](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-OfficeJet_T45)

---

### Post by banksw on 2007-04-08
Thanks for the suggestion and yes i have both the following installed drivers:
 Multifunction device (copier/scanner/fax/etc).

To get its maximum quality, use the "hpijs" driver.

For basic printing functionality use the HPIJS driver . For advanced functionality such as printer status, maintenance features, scanning and photo card unload use the HPLIP driver (which includes HPIJS).

Stand-alone copying should just work, it does not need the PC.

.... and it sees the suggested(recommended) driver but unfortunately the system is not detecting my connected HP printer and therefore sees no PPD files?

---

### Post by 11hjpphty76lkjj on 2007-04-09
Can you run:

```
/usr/lib/cups/backend/hp

```
and post the output?

Be sure the printer is connected.

If this is a parallel printer also run:

```
lsmod | grep ppdev
```

and post that as well.

A

---

### Post by banksw on 2007-04-11
Thanks for the suggestion and it seems like the OS is not seeing the parallel printer.
The results are:

banksw@DellOptiplex:~$ lsmod | grep ppdev
banksw@DellOptiplex:~$ 

banksw@DellOptiplex:~$ /usr/lib/cups/backend/hp
direct hp:/no_device_found "Unknown" "hp no_device_found"
banksw@DellOptiplex:~$ 

This is Dell Optiplex GX400 and with earlier versions the printer was detected?

---

### Post by banksw on 2007-04-11
A bit more info and i think i have seen this comment else where:

When checking for the printer it detects two entries both on parallel port #1 one for an Epson and one for a Canon printer.  Only the HP is connected.

---

### Post by 11hjpphty76lkjj on 2007-04-11
Run 

```
modprobe ppdev
```

then restart hplip

```
sudo /etc/init.d/hplip restart
```

it should (in theory) work then.

you may need to add the ppdev module to your /etc/modules file. else it will not work again on reboot.

A

---

### Post by banksw on 2007-04-12
Thanks again for the suggestion but when i run this i get this:

banksw@DellOptiplex:~$ modprobe ppdev
FATAL: Error inserting ppdev (/lib/modules/2.6.17-11-generic/kernel/drivers/char/ppdev.ko): Operation not permitted

I do not see this pkg in the pkg mgr either?

---

### Post by banksw on 2007-04-12
When i do sudo modprobe ppdev it loads OK and now i can see the printer.  The test pages are not complete but at least I have the printer and greatly appreciate all the help !!!

---

### Post by 11hjpphty76lkjj on 2007-04-12
Great. :)

---

