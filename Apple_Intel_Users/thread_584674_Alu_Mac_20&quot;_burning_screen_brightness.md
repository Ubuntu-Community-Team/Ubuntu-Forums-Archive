---
title: "Alu Mac 20&quot; burning screen brightness"
date: 2007-10-21
forum: Apple Intel Users
---

### Post by Paindistributor on 2007-10-21
I've installed ubuntu gutsy 7.10 on my new 20" alu imac and the first thing that really is pain for my eyes is the burning bright screen.

I checked some tools that might help:

- the brightness tool in ubuntu -> doesn't do anything
- pommed (v1.10) -> no imac support, unknown model
- xbacklight -> "No outputs have backlight property"

Booting osx and adjusting the brightness does not have any effect to the ubuntu screen settings. It always use the highest brightness setting for the screen.

We need a fix for this. I'd like to get some infos about this - perhaps i can create a patch.

Some infos might help:

Is there a working solution for the "old" (not the alu one) imac? And what software currently works, if any?

Hope to get this issue fixed :cool:

---

### Post by cyberdork33 on 2007-10-21
I do not even have an option to adjust screen brightness on mine.

---

### Post by FunkyM on 2007-10-22
I think someone with coding experience has to try the Macbook Pro backlight code (from mactel or HAL addon) to poke the right register of the ATI card. I agree this is an ugly issue and needs a fix fast.

---

### Post by FunkyM on 2007-10-25
I can now confirm I got a working solution to this (on Alu 24" RadeonHD 2600):
[http://felipe-alfaro.org/blog/2006/09/11/basic-backlight-support-for-macbook-pro/](http://felipe-alfaro.org/blog/2006/09/11/basic-backlight-support-for-macbook-pro/)

Above code works, thus only a matter of time to implement that as HAL addon.

---

### Post by Paindistributor on 2007-10-25
That is nice :)

I'll check the code on my imac...

---

### Post by crazybrit4967 on 2007-10-28
Can anyone give me step by step instructions on doing this?  I don't know how to use that C code.

---

### Post by crazybrit4967 on 2007-10-28
Okay, I got it working.  I installed build-essential, libpstreams-dev, and z88dk (not sure if the last two are necessary, sorry), removed the spaces in the #include lines (changing "stdio .h" to "stdio.h", etc) and then typed ```
gcc bl1.c -o "backlight"
``` into a terminal.   I also copied the new file to /usr/bin, then I just have to type "sudo backlight [number from 1 to 15]"

---

### Post by mauro on 2007-10-29
Really works!!! (iMac 20' Aluminum)
And this is the executable, if someone needs...

---

### Post by FunkyM on 2007-10-29
I created a HAL addon based on this, can someone with the 20" Mac where this works give me the output of this:
```
lshal | grep "system.product"
```
Thanks!

---

### Post by mauro on 2007-10-29
> **FunkyM said:**
> I created a HAL addon based on this, can someone with the 20" Mac where this works give me the output of this:
```
lshal | grep -P "system.product"
```
Thanks!

mauro@yama:~$ lshal | grep -P "system.product"
grep: The -P option is not supported

mauro@yama:~$ lshal | grep "system.product"
  smbios.system.product = 'iMac7,1'  (string)
  system.product = 'iMac7,1 1.0'  (string)

Is this what you need?

---

### Post by FunkyM on 2007-10-29
Yes thanks! Do you have a 20" version? In that case I'd need the output of this:
```
lshal | grep "  system."
```
(Just remove the line with the "uuid" if you like.)

---

### Post by aboeing on 2007-10-30
acyuta@linuX:~/apps$ lshal | grep "system.product"
  smbios.system.product = 'iMac5,1'  (string)
  system.product = 'iMac5,1 1.0'  (string)

---

### Post by AlainJLEB on 2008-04-14
Hi there,

This has worked for me also on my alumni iMac 24

```
lshal | grep " system"
  system.chassis.manufacturer = 'Apple Inc.'  (string)
  system.chassis.type = 'All In One'  (string)
  system.firmware.release_date = '07/25/07'  (string)
  system.firmware.vendor = 'Apple Inc.'  (string)
  system.firmware.version = '    IM71.88Z.007A.B01.0707251237'  (string)
  system.formfactor = 'unknown'  (string)
  system.hardware.product = 'iMac7,1'  (string)
  system.hardware.serial = 'W87428AAX89'  (string)
  system.hardware.uuid = '4458278E-8F17-A844-ACEB-A7D7E5178C63'  (string)
  system.hardware.vendor = 'Apple Inc.'  (string)
  system.hardware.version = '1.0'  (string)
  system.kernel.machine = 'i686'  (string)
  system.kernel.name = 'Linux'  (string)
  system.kernel.version = '2.6.22-14-generic'  (string)
  system.product = 'iMac7,1 1.0'  (string)
  system.vendor = 'Apple Inc.'  (string)
```

Thanks

---

