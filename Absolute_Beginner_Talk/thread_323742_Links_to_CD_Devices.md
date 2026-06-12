---
title: "Links to CD Devices"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-22
I have two CD drives: hdc is CDrw and hdd is DVDrw.  In my /dev directory there are four links:  cdrom, cdrw, dvd, and dvdrw.  All four of them point to /dev/hdd.  I use hdc as my default drive for playing music.  I changed the links so that cdrom and cdrw point to /dev/hdc, but on reboot they are set back to hdd.  For some reason when I first installed amarok it played a disc in hdc, but subsequently it defaulted to hdd because of the link and I just changed the amarok configuration to default to hdc.  My question is: where (or how) and why are those links set as they are, and how can I change them permanently?

Thanks,
Buck

---

### Post by kidders on 2006-12-22
Hi there,

The contents of /dev are controlled by udev. If you'd like to mess around with your devices' symlinks, you can, but there's no particular reason to. The rules are in /etc/udev/rules.d/ although you should do some reading before you change anything!

---

### Post by Buck2348 on 2006-12-23
Thanks for your reply.  I didn't find anything that looked like needing changing.

Buck

---

### Post by Buck2348 on 2006-12-24
On second thought I googled the udev rules a little and then changed two lines in /etc/udev/rules.d/60-symlinks.rules from
```
ENV{ID_CDROM}=="?*",                           SYMLINK+="cdrom"
ENV{ID_CDROM_CD_RW}=="?*",		SYMLINK+="cdrw"
```
to
```
KERNEL=="hdc", SYMLINK+="cdrom"
KERNEL=="hdc", SYMLINK+="cdrw"
```

This works because I know which drive I want the "cdrom" and "cdrw" links to point to.  I still don't understand the general method used in the original rules file.  Doing a
```
sudo udevtest hdc     #and
sudo udevtest hdd
```
shows that both drives have the ids ID_CDROM and ID_CD_RW, (the dvd drive has also ids so identifying it) so that would seem to be ambiguous when the system is making the symlinks with the original rules code.  But for me at least the links were always made to hdd, which made any software accessing the drives using the names "cdrom" or "cdrw" default to the second drive, which I don't use much.

Thanks,
Buck

---

### Post by clubsoda on 2006-12-24
Same thing here, a classic BNB (break on next boot) situation - you can fix that link as much as you like but it keeps coming back.  I'm not sure I'd want to set those rules in stone though because I occasionally plug things around.

My *guess* is that each link gets set to the last-found compatible device, so if you want to ensure CDs are playable from your CD-RW drive it should probably be the slave device on the secondary channel.  Unfortunate really, because it's intuitively nicer to have hdc as the CD and hdd as the DVD.

By the way, when I run your command```
sudo udevtest hdc
```I get```
main: unable to open 'hdc'
```What's that about?

---

### Post by kidders on 2006-12-25
You probably need to use the full device path...

```
udevtest /block/hdc
```

---

### Post by clubsoda on 2006-12-26
Thanks kidders, that works.
I've yet to read the chapter where "block" is used in a path like that.  :mrgreen:

---

### Post by kidders on 2006-12-26
Sorry... I should've explained that one a bit better! The "device path" udevtest's man page refers to is a sysfs path.

---

### Post by dwblas on 2006-12-26
I just have the music player set to /dev/hdc(d) instead of /dev/cdrom.  Also, for backup that works just fine and I don't have to mess with symlinks.

---

### Post by kidders on 2006-12-26
Exactly :-) IDE devices have fairly predictable names (hda, hdb, hdc, etc.), so symlinks are largely aesthetic, and make no difference to anything.

Other things though, particularly USB devices, have less predictable names, which makes the ability to create symlinks with udev pretty handy.

---

### Post by Buck2348 on 2006-12-26
> **clubsoda said:**
> 
My *guess* is that each link gets set to the last-found compatible device, so if you want to ensure CDs are playable from your CD-RW drive it should probably be the slave device on the secondary channel.  Unfortunate really, because it's intuitively nicer to have hdc as the CD and hdd as the DVD.
That's my guess too.  Seems to me it would be better if it went to the first-found, or if the rule could be written to eliminate the ambiguity.
> By the way, when I run your command```
sudo udevtest hdc
```I get```
main: unable to open 'hdc'
```What's that about?
Very sorry--I just copied that command from an on-line article--don't really know anything about it.  But I should have been careful to quote it right.

Regards,
Buck

---

### Post by kidders on 2006-12-26
Hey again,

I just thought it might be worth clarifying that udev rules are applied to *all* matching devices. CDs are playable regardless of any symlinks that may or may not be created in /dev, and regardless of the IDE channel used.

---

### Post by Buck2348 on 2006-12-26
Understand.  Thank you.

Buck

---

### Post by clubsoda on 2007-01-06
No apologies necessary.  If my question was somewhat abrupt then I shall be the one to apologise - my intention was to be concise, not short.  All help is gratefully received, and let's face it, I need plenty!

I agree with what was said above about being able to steer applications to the CD drive of choice irrespective of the symlinks, although it's not always obvious how to do that.  [[Instructions for gxine here](http://www.ubuntuforums.org/showthread.php?p=1976288#post1976288)].

Thanks for making me aware of udev too, as this is my first clash with the 2.6 kernel.  I'm keen to try a udev solution, and found a useful page at [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html).  Selectively quoting from there:-> Default udev rules are stored in /etc/udev/rules.d/50-udev.rules. You may find it interesting to look over this file - it includes a few examples, and then some default rules proving a devfs-style /dev layout. However, you should not write rules into this file directly.

Files in /etc/udev/rules.d/ are parsed in lexical order, and in some circumstances, the order in which rules are parsed is important. In general, you want your own rules to be parsed before the defaults, so I suggest you create a file at /etc/udev/rules.d/10-local.rules and write all your rules into this file.
.
*<and later as an example>*
    KERNEL=="hdc", SYMLINK+="cdrom cdrom0"Indeed that may work for my current situation, but would break if, for example, I were to move my drives around at a later date.  It seems to be a bit tricky.  You can be specific down to individual devices but the rules will then fail if you plug in substitute devices.

Ideally, I'd like a rule which says "Make /dev/cdrom point to the least capable compatible device".  i.e. CD-ROM if it exists, otherwise DVD-ROM, otherwise CD-RW, otherwise DVD-RW.  I'm willing to study further, but if anyone would like to suggest some code, that'd be cool too.  :grin:

---

### Post by kidders on 2007-01-06
Hey there,

udev rules can be pretty arbitrarily complex, and include all sorts of information to help you select the right devices for your /dev nodes & symlinks. As has been noted, creating a symlink based on a selector that includes a path such as "/dev/sdc" is a bit pointless, but there are lots of other ways of finding the hardware you want.

At the moment, I'm using custom udev rules to put iPods at places like /dev/ipod1 based on product/manufacturer information, to give multiple keyboards & mouses predictable names (for device-specific key & button mapping) based on device UUIDs, and to stop the /dev entry for my UPS moving around, depending on what else is plugged in whenever I reboot (which is pretty important hehe). For me, **udevinfo** is a lifesaver ...

```
# udevinfo -a -p /sys/bus/usb/devices/1-1/

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:07.2/usb1/1-1':
    KERNEL=="1-1"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{configuration}==""
    ATTR{serial}=="QB0447335545  "
    ATTR{product}=="Back-UPS CS 650 FW:817.v2.I USB FW:v2"
    ATTR{manufacturer}=="American Power Conversion"
    ATTR{maxchild}=="0"
    ATTR{version}==" 1.10"
    ATTR{devnum}=="5"
    ATTR{speed}=="1.5"
    ATTR{bMaxPacketSize0}=="8"
    ATTR{bNumConfigurations}=="1"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceClass}=="00"
    ATTR{bcdDevice}=="0006"
    ATTR{idProduct}=="0002"
    ATTR{idVendor}=="051d"
    ATTR{bMaxPower}=="  0mA"
    ATTR{bmAttributes}=="e0"
    ATTR{bConfigurationValue}=="1"
    ATTR{bNumInterfaces}==" 1"

  looking at parent device '/devices/pci0000:00/0000:00:07.2/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{serial}=="0000:00:07.2"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.16-gentoo-r7 uhci_hcd"
    ATTRS{maxchild}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="c0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"

  looking at parent device '/devices/pci0000:00/0000:00:07.2':
    KERNELS=="0000:00:07.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{modalias}=="pci:v00008086d00007112sv00000000sd00000000bc0Csc03i00"
    ATTRS{local_cpus}=="1"
    ATTRS{irq}=="9"
    ATTRS{class}=="0x0c0300"
    ATTRS{subsystem_device}=="0x0000"
    ATTRS{subsystem_vendor}=="0x0000"
    ATTRS{device}=="0x7112"
    ATTRS{vendor}=="0x8086"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
```

In theory, I could use any of that information to identify whatever is at Bus 1 -> Device 1 today (but may have moved tomorrow), or one of the devices above it in the chain, uniquely or not, depending on what I want.

> Thanks for making me aware of udev too, as this is my first clash with the 2.6 kernel. I'm keen to try a udev solutionNo problem. :-) Tbh I was a little sceptical about udev when it first arrived ... I found it a bit daft. It's sorta grown on me though. Hehe.

**Edit:** There are a few rules you have to play by when tinkering with udev, regarding which combinations of device selectors you can use at any one time, the way in which matching udev rules are applied to devices, etc. Once you follow them (making liberal use of **udevcontrol reload_rules**!), you should have no trouble.

I hope this is helpful.

---

### Post by clubsoda on 2007-01-06
:shock: Whoa, thanks for that.
Looks like you're getting oodles of good stuff to separate USB devices.  My optical drives don't look so promising:-```
udevinfo -a -p /sys/bus/ide/devices/1.0

udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:07.1/ide1/1.0':
    KERNEL=="1.0"
    SUBSYSTEM=="ide"
    SYSFS{modalias}=="ide:m-cdrom"
    SYSFS{drivename}=="hdc"
    SYSFS{media}=="cdrom"

  looking at device '/devices/pci0000:00/0000:00:07.1/ide1':
    ID=="ide1"
    BUS==""
    DRIVER==""

  looking at device '/devices/pci0000:00/0000:00:07.1':
    ID=="0000:00:07.1"
    BUS=="pci"
    DRIVER=="PIIX_IDE"
    SYSFS{modalias}=="pci:v00008086d00007111sv00000000sd00000000bc01sc01i80"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="0"
    SYSFS{class}=="0x010180"
    SYSFS{subsystem_device}=="0x0000"
    SYSFS{subsystem_vendor}=="0x0000"
    SYSFS{device}=="0x7111"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""
```and very similar for /sys/bus/ide/devices/1.1.  Here's a diff of the output:-```
8,9c8,9
<   looking at device '/devices/pci0000:00/0000:00:07.1/ide1/1.0':
<     KERNEL=="1.0"
---
>   looking at device '/devices/pci0000:00/0000:00:07.1/ide1/1.1':
>     KERNEL=="1.1"
12c12
<     SYSFS{drivename}=="hdc"
---
>     SYSFS{drivename}=="hdd"
```I thought these rules could go right down to serial numbers.  Have I specified the correct system device path?

---

### Post by kidders on 2007-01-07
Unfortunately, there's a small distinction there that isn't necessarily obvious from the output you posted. Vendor 0x8086 -> Device 0x7111 maps to "Intel Corporation" -> "82371AB PIIX4 IDE". Basically, you've gotten the device info for your IDE bus. :-(

On my machine, I can do...

```
$ udevinfo -q all -n /dev/hda
P: /block/hda
N: hda
S: cdrom
S: cdrw
S: dvd
S: disk/by-path/pci-0000:00:0f.1-ide-0:0
E: ID_CDROM=1
E: ID_CDROM_CD_R=1
E: ID_CDROM_CD_RW=1
E: ID_CDROM_DVD=1
E: ID_CDROM_MRW=1
E: ID_CDROM_MRW_W=1
E: ID_CDROM_RAM=1
E: ID_TYPE=cd
E: ID_MODEL=AOPEN_COM5232AAH_PRO
E: ID_SERIAL=
E: ID_REVISION=1.05
E: ID_BUS=ata
E: ID_PATH=pci-0000:00:0f.1-ide-0:0
```

That might be closer to what you're after. I imagine, for instance, that you could use a selector like **ENV{ID_CDROM_DVD}=="1"** to place something at /dev/dvd, rather than /dev/cdrom ... but I've never tried to do something like that.

---

