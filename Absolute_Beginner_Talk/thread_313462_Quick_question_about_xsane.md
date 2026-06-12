---
title: "Quick question about xsane"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by Jcarr_toonist on 2006-12-06
I set up my scanner a couple weeks ago, can't really remember what i did but it was a bit of a pain to get working. Anyways I went to scan something today and it said 

<qoute>
Failed to open device 'hp3900:libusb:003:002:' Access to resource denied.
</qoute>

I am hoping that I just forgot to give something access to certain resources when I was setting up the scanner and that it is an easy fix but I have no idea what to do.

thanks, if anyone can help.

---

### Post by Sef on 2006-12-06
1) Do you have an hp 3900 scanner?

2) Did you try and access the scanner through Applications > Graphics > Xsane Image Scanner?

---

### Post by Jcarr_toonist on 2006-12-06
Yeah I tried accessing it through xsane image scanner, kooka and gimp. It's a  hp4070 but I recall the sane website saying that the 3900 backend was right. 

I did some research after I posted this and I think I might need to chmod something. But I don't know what or how to find out.

---

### Post by marmaladejackson on 2007-03-11
I was having the same problem:

*gt68xx:libusb:001:003': invalid argument*

I installed some libraries through the synaptic universe, and no all I get is a "no devices avalible" message.  *lsusb* shows otherwise.  Anybody have any thoughts?

-B

---

### Post by Bachstelze on 2007-03-11
Can you access the scanner ar root with e.g. *sudo scanimage* ?

---

### Post by marmaladejackson on 2007-03-11
No.  I get the following:

[[B]gt68xx] Couldn't open firmware file (`/usr/share/sane/gt68xx/Cis3r5b1.fw'): No such file or directory
scanimage: open of device gt68xx:libusb:002:003 failed: Invalid argument[/B]

So I guess I'm missing a library of some sort.  Does it make any sense to you?

Thanks!
-B

---

### Post by Bachstelze on 2007-03-11
You're missing the firmware for your scanner. You'll need to grab it from an existing Windows installation or try to find one from Google.

---

### Post by marmaladejackson on 2007-03-11
Ah-ha!  Ok, That's what I'll start working towards.  Thanks!
-B

---

### Post by marmaladejackson on 2007-03-12
Ok, I was able to find the firmware file: Cis3r5b1.fw.  If anybody else needs this, PM me. 
If I *sudo scanimage*, The scanner starts to operate and  ASCII jibberish filles the terminal window.

If I attempt to use the scanner through the xsane gui I get:

**Failed to open device 'gt68xx:libsub:002:003': invalid argument.**

Am I missing a library?  If so, where do I find it?

Thanks again!

---

### Post by marmaladejackson on 2007-03-19
Anybody getting the same message above, try changing the permission of the firmware file.  That seemed to do the trick!

-B

---

### Post by alienexplorers on 2007-03-19
did you load the following files from synaptic:
libsane
libsane-extras
sane
sane-utils
xsane
xsane-common

---

### Post by MoebusNet on 2007-03-21
Did anyone here actually get their scanjet 4370 working? If so, how? There was a mention of firmware files, but I don't have the faintest idea what to do with them even if I can find them. If anyone cares to give some advice, it would be most welcome. Every time I need to use my scanner, I am having to remove my notebook Ubuntu hard drive, reinstall the old XP hard drive and use the scanner in XP. Sure would like to avoid that nonsense...

---

### Post by Bachstelze on 2007-03-21
The firmare is the last step, let's start from the beginning :p Did you *apt-get install sane-utils* ? If so, was your scanner detected with *sudo sane-find-scanner* ?

---

### Post by MoebusNet on 2007-03-23
I'm sorry to be so long getting back to you; I work in a different state than where I live. I'm at work now and since my scanner is at home it will be a week before I can plug it in. 

I have installed the following with Synaptic:
libsane
libsane-extras
sane
sane-utils
xsane
xsane-common

I downloaded and installed hp3900-sane_bin_0.7-1_i386.deb from Sourceforge.

lsusb showed:

$ lsusb

Bus 004 Device 004: ID 03f0:4105 Hewlett-Packard
Bus 004 Device 003: ID 0781:5406 SanDisk Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 001 Device 001: ID 0000:0000

when I looked 2 days ago; its not there now since the scanner isn't plugged in.

When I tried to run xsane I got the error message:

Failed to open device 'HP3900:libusb:004:002':
Access to resource has been denied

although the actual numbers in the message were slightly different.

I've been basically trying to use the procedures followed by kliljedahl on this forum for lack of better.

That's about all I can tell you until I get home. Thank you for your time and attention.

---

### Post by Kendaar on 2007-03-31
If you can access your scanner as root but not as normal users, you should create a new udev file, because automatically created /dev/bus/usb/xxx/yyy files are owned by root:root with 664 permission.

To do this (for example for an hp3900 scanner)
[LIST=1]
[*]create /etc/udev/hp3900-sane.rules with these lines
[FONT="Courier New"][INDENT]ACTION!="add", GOTO="hp3900_sanes_rules_end"
SUBSYSTEM!="usb_device", GOTO="hp3900_sanes_rules_end"

## hp_hp3900 backend
# Hewlet-Packard ScanJet 4070C
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="2405", MODE="664", GROUP="scanner"

LABEL="hp3900_sanes_rules_end"
[/INDENT][/FONT]
[*]link this file to /etc/udev/rules.d as 025_hp3900-sane.rules
[*]unplug your scanner
[*]wait for 5 seconds for USB to settle
[*]plug your scanner
[*]check your new devices ids (with scanimage -L)
[FONT="Courier New"][INDENT]device `hp3900:libusb:005:012' is a Hewlett-Packard RTS8822 chipset based flatbed scanner[/INDENT][/FONT]
[*]check /dev/bus/usb/xxx/yyy (where xxx=005 and yyy=012 in the example), which should be owned by root:scanner with 664 permission
[FONT="Courier New"][INDENT]ls -l /dev/bus/usb/005/012
crw-rw-r-- 1 root scanner 189, 523 2007-03-31 16:21 /dev/bus/usb/005/012[/INDENT][/FONT]
[/LIST]

This should work (at least it worked for me). Don't forget to download hp3900-sane_bin*.deb from sourceforge!

Good Luck

---

