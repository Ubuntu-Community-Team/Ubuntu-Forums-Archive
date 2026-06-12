---
title: "HELP !!... Still using M$ .....modem problems :("
date: 2005-08-08
forum: Absolute Beginner Talk
---

### Post by its_jon on 2005-08-08
Just got my pack of 10 ubuntu disks delivered.

Popped ubuntu onto my slave drive (disabled primary ide0)

Its working fine.......except.

I can't get onto the net ..... Im assuming the problem is my Sagem 'fast 800' usb modem.......

I downloaded the Linux driver pack from Sagem which appears to have some debian named files inside it.........

My trouble is this........ What the hell do I do with it?......as a newbie to Linux how do I install anything! let alone a hardware driver........


cheers!

---

### Post by PeP on 2005-08-08
[QUOTE=its_jon]
my Sagem 'fast 800' usb modem.......

[/QUOTE]

arghhhhhhh.. I hate this one! ](*,) 

you need to either install eagle-usb and launch eagle config
or if you prefer the last driver version wich is not provided by ubuntu, install
linux-headers (from the cd) and then use the tarball you'll download on this page:
[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230)
with windows (...)

good luck.

---

### Post by its_jon on 2005-08-08
[QUOTE=PeP]arghhhhhhh.. I hate this one! ](*,) 

you need to either install eagle-usb [/QUOTE]

From where and how

[QUOTE=PeP]and launch eagle config[/QUOTE]

From where and how


[QUOTE=PeP]
or if you prefer the last driver version wich is not provided by ubuntu, install
linux-headers (from the cd) and then use the tarball you'll download on this page:
[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230)
with windows (...)

[/QUOTE]

You've lost me now

---

### Post by KingBahamut on 2005-08-08
apt-get install eagle-usb-modules-source eagle-usb-data eagle-usb-utils

Then fill out the nessecary information.

---

### Post by its_jon on 2005-08-08
[QUOTE=KingBahamut]apt-get install eagle-usb-modules-source eagle-usb-data eagle-usb-utils

Then fill out the nessecary information.[/QUOTE]

Sorry guy's this it ricky for me at the moment as im loking at M$ at the moment and not Linux.

"apt-get install eagle-usb-modules-source eagle-usb-data eagle-usb-utils"

'apt' stands for ? ...... is this the name of the hard drive in Linux or the root ?
Like C;/windows/system etc?
aka apt-get install eagle-usb- etc?

---

### Post by PeP on 2005-08-08
[QUOTE=its_jon]Sorry guy's this it ricky for me at the moment as im loking at M$ at the moment and not Linux.

"apt-get install eagle-usb-modules-source eagle-usb-data eagle-usb-utils"

'apt' stands for ? ...... is this the name of the hard drive in Linux or the root ?
Like C;/windows/system etc?
aka apt-get install eagle-usb- etc?[/QUOTE]

apt is the real valuable thing ubuntu/debian provides to you.
It is an unified program to search, install, upgrade, or remove something or everything running on your computer.

eg type in a terminal :
sudo apt-get update 
it updates the software list on your computer.
then 
apt-get upgrade
upgrade every package (program/library/documentation ...) on your computer
yes I mean it selects what's upgradable, downloads it , configure it and install it.


use synaptics if you are a newbee, its almost the same with a gui.

good luck.

PS: [www.google.com/linux](www.google.com/linux) is your friend and will answer many many many basic questions like this.
PPS: if you have a friend running ubuntu, ask him for a little demo / tour on the system, if not ... search for a newbee user guide, theres is one on the site.

---

### Post by its_jon on 2005-08-08
Thanks gu'y.... I will bot back into Linux and have a look about.....

Im sure I have seen the terminal in the menu's is the 'synaptics' possibly a system tool as well...

synaptics ,,, is that possibly a french term for something obvious as its based on debian ?

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=its_jon]
Im sure I have seen the terminal in the menu's is the 'synaptics' possibly a system tool as well...

synaptics ,,, is that possibly a french term for something obvious as its based on debian ?[/QUOTE]

[https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29](https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29)

---

### Post by crispingatiesa on 2005-08-08
[QUOTE=KingBahamut]apt-get install eagle-usb-modules-source eagle-usb-data eagle-usb-utils

Then fill out the nessecary information.[/QUOTE]

He can't do that , doesn't have net access from Ubuntu! That's precisely the problem, right?

---

### Post by xmastree on 2005-08-08
[QUOTE=crispingatiesa]He can't do that , doesn't have net access from Ubuntu! That's precisely the problem, right?[/QUOTE] :idea: 
Is there a way he could download the necessary files in Windows, put them somewhere ubunto can see them, and somehow tell apt-get to look there for them?

Maybe by making some sort of local repository?
Just a thought...

---

### Post by its_jon on 2005-08-09
as fortune has it, I do have a CDRW drive ;)

---

### Post by its_jon on 2005-08-09
Ok , I got eagle-usb installed via synaptics.  \\:D/ 



It asked for my hosts name, then connection details, then some more connection style detail that completely confuzed me so I skipped the step (assuming I could configue this later).....so, that it installed.

I can't connect to the net  :neutral:

Tried a reboot, I checked that the package appeared in the synaptic lists...which it does 'eagle-usb'
So I assumed the connection details required updating, adding to or correcting.........

Now, where do I do that?




A sugestion for the development team.::-

Set up two new shortcuts in the menu's and scrap the term 'synaptics'
The word 'synaptics' if utterly confuzing to a english speaking newbie and not 'human' at all.
Replace it with 2 links to the same location (location = synaptics tool)

Call one 'package installer'
Call the second 'driver installer'

easy  :smile:

---

### Post by its_jon on 2005-08-09
erm...... Im assuming I am doing something wrong here. ?

I installed the eagle drivers, launch firefox and nothing happence except 'google cant be found' or whatever.
The modem appears to be switched off...... I know the drivers are installed......how do I make firefox use the drivers to talk to the modem....or indeed, where are the connection options.

I know its unfortunate that I have the Sagem USB modem which it seems causes many people this problem,,,,,, I really want Linux to work for me, last time I tried Linux was mandrake approx 4 year ago.....got a net connection with it but on the whole I found it clunky and was unable to work out how to install stuff......ubuntu up to now appears to be what I need as I have over the past years started to use OOo and firefox.....even little bits of gimp work.....
All I have to work out is this phupping net connection.

---

### Post by its_jon on 2005-08-09
Well, As im also searching the forum for answers to my problem im constantly in and out of windows to check for more solutions.

Found some root commands on the forum and got the terminal to report that the modem is not getting the correct driver response???

any ideas?

---

### Post by PeP on 2005-08-09
some questions:

who is your internet provider?

did you have to enter some informations like your isp, and even usename/password

type lsmod, deos the eagle modules appears among the others?

what happens when you plug your modem/ boot your computer? diodes blinking? nothing? ...

If I remember well, the diodes should be blinling for a moment during the loading and then both of them should remain on.

if you can post the result of eaglediag (a usb key will help you a lot ...):
in a terminal type eaglediag

you might find more help/documentation on eagle-usb.org,

---

### Post by its_jon on 2005-08-09
Provider is Tiscali.

Modem blinks with windows then both light light up.

with Linux, no blinking then only one light.

I have entered ISP connection deatails first when the automated insteller thingy (whatever irs called) searched then installed the eagle usb drivers.....I re-entered these details via a root terminal.

Im set to UK01

encrypt - no

ET01 is now ACTIVATED and set to DHLP

I willl get a result from eaglediag and post.....hey ho, boot back to linux

---

### Post by its_jon on 2005-08-09
does this help me?

[IMG]http://myweb.tiscali.co.uk/design_jon/MR2/snap.jpg[/IMG]

---

### Post by PeP on 2005-08-09
it seems like the firmware isn't uploaded correctly into the modem ...
IIRC to do that the command was eaglectrl -s (makes the modem blink ... then waits for syncro)

so i propose you to:
first try to re-run eagleconfig it tries to reaload the driver.

then post the output of eaglestat, eaglediag if it changed and eaglectrl -s

you should copy all of theses in a text file (middle button of the mouse to copy and paste, instead of providing a screenshot for each.)

---

### Post by its_jon on 2005-08-09
I think this is what your asking for????

:/home/john # eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.0.0     Chipset: Eagle0
Vendor ID : 0x1110     Product ID : 0x9031   Rev: 0x200b
USB Bus : 002    USB Device : 002        Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:70:9c:d1
Tx Rate           0  Rx Rate           0
FEC               0  Margin            0  Atten             0 dB
VID-CPE           0  VID-CO            0  HEC               0
VPI               0  VCI               0  Delin          GOOD
Cells Tx          0  Cells Rx          0
Pkts Tx           0  Pkts Rx           0
OAM               0  Bad VPI           0  Bad CRC           0
Oversiz.          0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

:/home/john #

eaglediag
Diagnostic (1.13 2004/08/29) driver eagle-usb 20050710221432
# System Information
Linux  2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
3.1
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
used : 3.3.4 (Debian 1:3.3.4-9ubuntu5)
# module loaded ?        [ OK ]
# modem operational ?    [ KO ]
# Config vpi/vci/encapsulation/isp :  26 6 (pppoa) UK01
# pppd launched ?        [ KO ]
# ping IP ?              [ KO ]
# test DNS resolution ?  [ KO ]
Complete diagnostic has been saved on /var/log/eagle-usb/eagle_diag_20050710221432.txt
Please keep only relevant data and remove personal informations.

eaglectrl -s
Can't find any PRE or POST firmware devices.
Is your device plugged in ?





Its all gibberish to me. :s

---

### Post by PeP on 2005-08-09
[QUOTE=its_jon]
eaglectrl -s
Can't find any PRE or POST firmware devices.
Is your device plugged in ?

Its all gibberish to me. :s[/QUOTE]

the device is not detected, post the last few lines of
 dmesg 
afer you've unplugged and replugged the usb cable.
post also the result of 
 lsmod
please.

---

### Post by its_jon on 2005-08-09
dmesg ?  :confused:  :confused:  :confused:  lsmod ?

---

### Post by SSTwinrova on 2005-08-09
Just type in each of those commands and copy/paste whatever the computer spits back out at you  :)

---

### Post by PeP on 2005-08-09
[QUOTE=its_jon]dmesg ?  :confused:  :confused:  :confused:  lsmod ?[/QUOTE]

in a terminal type 
dmesg
then hit enter, it gives you information about some kernel events, including those that happens when you plug/unplug an usb device.

in a terminal type
lsmod
then hit enter, it shows the kernel modules that  are loaded, you should have modules for usb, hotplug and the eagle-usb one

they are other usefull command which might help for drivers issues like lsusb (shows usb devices), lshw  (infos on your hardware, lspci (show some parts of our hardware), lshal ...

to help you I am seeking some information about the state of your system (does it makes sense ?) so I require you to use a terminal and seek this info manually.

---

### Post by its_jon on 2005-08-09
any of this any use?



ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:02.3[A] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:02.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:02.3: irq 11, pci mem 0xcffff000
ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
usb 2-1: new full speed USB device using ohci_hcd and address 2
CSLIP: code copyright 1989 Regents of the University of California
PPP generic driver version 2.4.2
[eagle-usb] driver V2.0.0 loaded
[eagle-usb] New USB ADSL device detected, waiting for DSP code...
[eagle-usb] Interface 0 accepted.
[eagle-usb] created proc entry at : /proc/driver/eagle-usb/002-002
usbcore: registered new driver eagle-usb
Linux Tulip driver version 1.1.13 (May 11, 2002)
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 11 (level, low) -> IRQ 11
tulip0:  MII transceiver #1 config 1000 status 786d advertising 05e1.

tulip                  46112  0
eagle_usb             120512  0
ppp_async              10752  0
ppp_generic            27668  1 ppp_async
slhc                    7040  1 ppp_generic
crc_ccitt               2176  1 ppp_async
ohci_hcd               19848  0
usbcore               107384  3 eagle_usb,ohci_hcd
i2c_sis96x              5380  0
i2c_sis630              7436  0
i2c_core               21264  2 i2c_sis96x,i2c_sis630
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
sis_agp                 8068  1
agpgart                31784  1 sis_agp
analog                 10784  0

Bus 002 Device 002: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn)
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
0000:00:0b.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:00:0f.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
0000:00:11.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

---

### Post by PeP on 2005-08-09
> [eagle-usb] driver V2.0.0 loaded
ok everything works as it should, but the eagle module doesn't do its job or the eagle utils are lost.

-> if 
eaglecrtl -w 
then wait ...
then try
eaglectrl -d
then
eaglectrl -s
doesn't makes the both diodes blink and then stay on,
 you must change the utilities and the module : they are both outdated and uneffective

I had previously to do that , that's why I posted the link above in my first reply.

download the last version (2.3.2 instead of 2.0.0 ...) from:
[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb230)

from the page:
 > 
 To compile :
 ./configure
 make uninstall
 make
 make install
 eagleconfig
 Then eaglectrl -w ; startadsl # and pray ;-)

> 
To start, you will need :
 
 kernel-source : take the same version as the one given for your kernel by uname -r, you'll then have a link /usr/src/linux to your kernel-source
 gcc : be sure - mostly on Debian ;-) - to take the one used for your kernel, just compare cat /proc/version ; gcc -v (have a look at FaqDiag (interwiki) for more details)
 be sure to have bash and gawk as well, and make and lsusb
 packages bc, automake and autoconf may be required (it will complain automatically about aclocal missing - if it's the case - at compilation, take latest versions)


so install first  linux-source-2.6.10-5-386 (in theory the headers should be enough ...) 
install also gcc ,automake, autoconf and gawk

---

### Post by xmastree on 2005-08-10
I know this isn't the solution you're looking for, but...

Does your computer have a serial port? There are dozens of external modems on ebay.

[**[COLOR=DarkSlateBlue]this one[/COLOR]**](http://cgi.ebay.co.uk/DIAMOND-Supraexpress-56e-Pro-external-Modem-with-s-w_W0QQitemZ6790136945QQcategoryZ3692QQrdZ1QQcmdZViewItem) for example. Currently running at £1.50...

I guess since the explosion of dsl everywhere, there may be a lot of cheap modems for sale.

[[COLOR=DarkSlateBlue]More here[/COLOR]](http://search.ebay.co.uk/external-modem_Peripherals_W0QQcatrefZC12QQfromZR40QQfsooZ1QQfsopZ1QQsacatZ16163QQsatitleZQ22externalQ20modemQ22)

---

### Post by its_jon on 2005-08-10
[QUOTE=PeP]
-> if 
eaglecrtl -w 
then wait ...
then try
eaglectrl -d
then
eaglectrl -s
linux-source-2.6.10-5-386 (in theory the headers should be enough ...) 
install also gcc ,automake, autoconf and gawk[/QUOTE]

eek...... its good to know that we know what my problem is but you have to understand that the above is very much in at the deep end for me. I diddnt expect to be getting into compiling kernals and stuff so soon....thats why I waited so long for linux to refine itself (from a newbie's point of view)......I just missed out on the DOS days as well so I have no background in typed commands (other than nightmare talkthroughs on the telephone to a technical advisor at £5 a second.
Thats one thing XP did finally eleminate, the BSOD.

Will boot back with the instructions transfered to floppy and see what happens next, thanks for the ongoing support

---

### Post by its_jon on 2005-08-10
OK..... this is where im at.


Downloaded the 2.3.2 eagle file. Its on the Linux desktop, unpacked.

Have uninstalled the prior Eagle drivers via the synaptic thing.


Attempted typed comands and to update Linux to version 2.3.2 and synaptic tool (which does not recognise the new version, only the old version files - even when I put the old files in the bin)


PLease assume im really stupid....... can someone talk me through the process almost pixel by pixel.......If I have to type something, where is it typed, at what time and after having done what first etc..... I am 100% new to typed commands

If I could take these files I have downloaded, put them into a new folder, rename that folder to something the synaptic tool would understand?????????? ....would that be more simple?

---

### Post by PeP on 2005-08-10
step by step:
in windows downlaod the driver
[http://baud123.free.fr/eagle-usb/eagle-usb-2.3/eagle-usb-2.3.2.tar.bz2](http://baud123.free.fr/eagle-usb/eagle-usb-2.3/eagle-usb-2.3.2.tar.bz2)
it is a tar.bz2 archive containing the source code


in synaptics you install from the cd :
build-essentials
gawk
automake 
autoconf
linux-headers-2.6.10-5-386


you uninstall anything eagle related...


in a terminal unpack the archive:
```

tar -xjvf eagle-usb-2.3.2.tar.bz2

```
move to the created folder
```

cd eagle-usb-2.3.2

```
then in this folder you perform
> 
 ./configure
 make uninstall
 make
sudo make install

this will compile and install your driver.if you have any error during this, post the last lines of the output, (-edit you won't have any, I tried it all just for you: it works fine)

then you configure it and launch it:
```

 eagleconfig
 eaglectrl -w ; startadsl 

```

---

### Post by mozz10844 on 2005-08-11
when i try and install it,it says
 install:         no input file selected.

im also a n00b to linux :razz:

---

### Post by its_jon on 2005-08-12
Stilll having no luck........

I will keep checking back to see if ubuntu provide a fix to download, other than that I guess I will have to wait and see if the modem is supported in the next release.

Shame, its a very popular modem as well :/

---

### Post by PeP on 2005-08-12
[QUOTE=its_jon]Stilll having no luck........

I will keep checking back to see if ubuntu provide a fix to download, other than that I guess I will have to wait and see if the modem is supported in the next release.

Shame, its a very popular modem as well :/[/QUOTE]

just post the first error message (the configuration (./configure) / compilation (make) /installation (sudo make install)  scripts gives a lot of output, scroll around the last line to find any error)

---

### Post by its_jon on 2005-08-12
./configure does nothing, just get an error message.... bad command or something :(

---

### Post by PeP on 2005-08-12
[QUOTE=its_jon]./configure does nothing, just get an error message.... bad command or something :([/QUOTE]

this is very unlikely  :| 

are build-essantials automake and autoconf installed?
are you in the good directory (eagle-usb-2.3.2 )?? ./configure is a local script.
can you post the full output?

---

### Post by sneax on 2005-08-27
i think he can download those files as .deb packages (what they basicaly are) into a directory, then
- access them from linux just browsing hd's if that's possible if not
- put them on a usbflashdrive and then simple do dpkg -i for every *.deb package

right?

---

### Post by gamesmad on 2005-11-02
Im having the same problem with this modem, but its no problem getting files from Windows to Ubuntu, I just mount my windows partition....

Will

---

### Post by Arwen on 2007-06-09
Hello guys!
First of all I must say I am a noob.I tried to do a little bit of all stuff above.I would appreciate if anyone took a look at these 'dmesg' results:

[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=e5a224a1-aab0-48d2-bd61-9ecb07778713 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262064) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000faa60
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000503 MSFT 0x00000097) @ 0x000000003ffb0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x06000503 MSFT 0x00000097) @ 0x000000003ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000503 MSFT 0x00000097) @ 0x000000003ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000503 MSFT 0x00000097) @ 0x000000003ffc0040
[    0.000000] ACPI: DSDT (v001  75V80 75V80000 0x00000000 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000003ffb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 262064) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262064
[    0.000000] On node 0 totalpages: 261967
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1085 pages reserved
[    0.000000]   DMA zone: 2858 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3526 pages used for memmap
[    0.000000]   DMA32 zone: 254442 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e6000
[    0.000000] Nosave address range: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bee00000)
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 257300
[    0.000000] Kernel command line: root=UUID=e5a224a1-aab0-48d2-bd61-9ecb07778713 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   13.907470] Console: colour VGA+ 80x25
[   13.908696] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.909477] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   13.909589] Checking aperture...
[   13.909601] Calgary: detecting Calgary via BIOS EBDA area
[   13.909604] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   13.935089] Memory: 1020124k/1048256k available (2217k kernel code, 27744k reserved, 1162k data, 304k init)
[   14.011555] Calibrating delay using timer specific routine.. 6008.00 BogoMIPS (lpj=12016014)
[   14.011635] Security Framework v1.0.0 initialized
[   14.011644] SELinux:  Disabled at boot.
[   14.011680] Mount-cache hash table entries: 256
[   14.011954] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   14.011958] CPU: L2 cache: 2048K
[   14.011961] CPU 0/0 -> Node 0
[   14.011963] using mwait in idle threads.
[   14.011965] CPU: Physical Processor ID: 0
[   14.011967] CPU: Processor Core ID: 0
[   14.011979] CPU0: Thermal monitoring enabled (TM1)
[   14.011996] SMP alternatives: switching to UP code
[   14.012522] Early unpacking initramfs... done
[   14.349683] ACPI: Core revision 20060707
[   14.349929] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   14.393568] Using local APIC timer interrupts.
[   14.426872] result 12499663
[   14.426874] Detected 12.499 MHz APIC timer.
[   14.427488] SMP alternatives: switching to SMP code
[   14.427790] Booting processor 1/2 APIC 0x1
[   14.438891] Initializing CPU#1
[   14.519063] Calibrating delay using timer specific routine.. 6000.24 BogoMIPS (lpj=12000486)
[   14.519079] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   14.519082] CPU: L2 cache: 2048K
[   14.519086] CPU 1/1 -> Node 0
[   14.519088] CPU: Physical Processor ID: 0
[   14.519090] CPU: Processor Core ID: 0
[   14.519103] CPU1: Thermal monitoring enabled (TM1)
[   14.519487]               Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   14.523103] Brought up 2 CPUs
[   14.523306] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[   14.523309] time.c: Detected 2999.950 MHz processor.
[   14.630875] migration_cost=15
[   14.631371] Time: 18:37:36  Date: 05/09/107
[   14.631420] NET: Registered protocol family 16
[   14.631531] ACPI: bus type pci registered
[   14.631542] PCI: Using configuration type 1
[   14.636975] ACPI: Interpreter enabled
[   14.636979] ACPI: Using IOAPIC for interrupt routing
[   14.638413] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.638420] PCI: Probing PCI hardware (bus 00)
[   14.639757] Boot video device is 0000:01:00.0
[   14.639820] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.653831] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   14.661090] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   14.661360] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   14.661628] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   14.661891] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.662213] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.662479] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.662751] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.663026] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   14.663131] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.663145] pnp: PnP ACPI init
[   14.668065] pnp: PnP ACPI: found 13 devices
[   14.668135] PCI: Using ACPI for IRQ routing
[   14.668139] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.668242] NET: Registered protocol family 8
[   14.668245] NET: Registered protocol family 20
[   14.668268] PCI-GART: No AMD northbridge found.
[   14.669285] PCI: Bridge: 0000:00:01.0
[   14.669287]   IO window: disabled.
[   14.669293]   MEM window: faa00000-feafffff
[   14.669297]   PREFETCH window: cff00000-efefffff
[   14.669319] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.669369] NET: Registered protocol family 2
[   14.710977] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   14.711330] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   14.713700] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.715464] TCP: Hash tables configured (established 131072 bind 65536)
[   14.715471] TCP reno registered
[   14.727120] checking if image is initramfs... it is
[   15.360576] Freeing initrd memory: 7304k freed
[   15.373963] audit: initializing netlink socket (disabled)
[   15.373997] audit(1181414256.440:1): initialized
[   15.374310] VFS: Disk quotas dquot_6.5.1
[   15.374345] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.374432] io scheduler noop registered
[   15.374435] io scheduler anticipatory registered
[   15.374437] io scheduler deadline registered
[   15.374455] io scheduler cfq registered (default)
[   15.374566] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   15.405722] Real Time Clock Driver v1.12ac
[   15.405795] Linux agpgart interface v0.102 (c) Dave Jones
[   15.405799] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.405954] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.406777] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   15.406977] mice: PS/2 mouse device common for all mice
[   15.407783] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.408124] input: Macintosh mouse button emulation as /class/input/input0
[   15.408168] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   15.408173] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   15.408513] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   15.409688] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.409694] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.409864] TCP cubic registered
[   15.409876] NET: Registered protocol family 1
[   15.410027] ACPI: (supports S0 S1 S3 S4 S5)
[   15.410075]   Magic number: 11:166:645
[   15.410186]   hash matches device ptyda
[   15.410317] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.410433] Freeing unused kernel memory: 304k freed
[   15.434064] input: AT Translated Set 2 keyboard as /class/input/input1
[   16.616617] Capability LSM initialized
[   16.658468] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU1PM] [20060707]
[   16.658735] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [   AMI] OemTableId [  CPU2PM] [20060707]
[   16.658770] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   16.658778] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   17.248898] usbcore: registered new interface driver usbfs
[   17.248951] usbcore: registered new interface driver hub
[   17.278080] usbcore: registered new device driver usb
[   17.278451] SCSI subsystem initialized
[   17.286173] libata version 2.20 loaded.
[   17.290927] sata_via 0000:00:0f.0: version 2.1
[   17.290962] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   17.290988] sata_via 0000:00:0f.0: routed to hard irq line 5
[   17.291082] ata1: SATA max UDMA/133 cmd 0x000000000001d400 ctl 0x000000000001d002 bmdma 0x000000000001c400 irq 20
[   17.291134] ata2: SATA max UDMA/133 cmd 0x000000000001cc00 ctl 0x000000000001c802 bmdma 0x000000000001c408 irq 20
[   17.291154] scsi0 : sata_via
[   17.330776] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   17.333679] USB Universal Host Controller Interface driver v3.0
[   17.342568] Floppy drive(s): fd0 is 1.44M
[   17.370993] FDC 0 is a post-1991 82077
[   17.496059] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.662135] ATA: abnormal status 0x7F on port 0x000000000001d407
[   17.672414] ATA: abnormal status 0x7F on port 0x000000000001d407
[   17.685067] ata1.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   17.685075] ata1.00: ATA-7: Maxtor 6V300F0, VA111630, max UDMA/133
[   17.685078] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   17.697056] ata1.00: ata_hpa_resize 1: sectors = 586114704, hpa_sectors = 586114704
[   17.697061] ata1.00: configured for UDMA/133
[   17.697080] scsi1 : sata_via
[   17.903642] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   17.913841] ATA: abnormal status 0x7F on port 0x000000000001cc07
[   17.913989] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
[   17.915554] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
[   17.915809] eth0: VIA Rhine II at 0x1e800, 00:13:8f:29:e1:70, IRQ 23.
[   17.916525] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   17.916698] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   17.916716] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   17.917113] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[   17.917176] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfebff800
[   17.917185] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.917883] usb usb1: configuration #1 chosen from 1 choice
[   17.917919] hub 1-0:1.0: USB hub found
[   17.917928] hub 1-0:1.0: 8 ports detected
[   18.024326] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   18.024339] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   18.024509] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   18.024534] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d800
[   18.025146] usb usb2: configuration #1 chosen from 1 choice
[   18.025178] hub 2-0:1.0: USB hub found
[   18.025188] hub 2-0:1.0: 2 ports detected
[   18.131563] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   18.131580] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   18.131611] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   18.131639] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000dc00
[   18.131752] usb usb3: configuration #1 chosen from 1 choice
[   18.131784] hub 3-0:1.0: USB hub found
[   18.131791] hub 3-0:1.0: 2 ports detected
[   18.239416] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   18.239428] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   18.239453] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   18.239476] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e000
[   18.239583] usb usb4: configuration #1 chosen from 1 choice
[   18.239611] hub 4-0:1.0: USB hub found
[   18.239618] hub 4-0:1.0: 2 ports detected
[   18.347304] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   18.347318] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   18.347342] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[   18.347364] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000ec00
[   18.347469] usb usb5: configuration #1 chosen from 1 choice
[   18.347497] hub 5-0:1.0: USB hub found
[   18.347505] hub 5-0:1.0: 2 ports detected
[   18.456706] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   18.456730] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   18.456744] VP_IDE: chipset revision 6
[   18.456746] VP_IDE: not 100% native mode: will probe irqs later
[   18.456760] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   18.456770]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   18.456782]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[   18.456790] Probing IDE interface ide0...
[   18.476468] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[   18.476513] sda: Write Protect is off
[   18.476524] sda: Mode Sense: 00 3a 00 00
[   18.476575] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.476732] SCSI device sda: 586114704 512-byte hdwr sectors (300091 MB)
[   18.476762] sda: Write Protect is off
[   18.476766] sda: Mode Sense: 00 3a 00 00
[   18.476806] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.476820]  sda: sda1 sda2
[   18.517727] sd 0:0:0:0: Attached scsi disk sda
[   18.521953] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.695417] Attempting manual resume
[   18.695422] swsusp: Resume From Partition 8:2
[   18.695424] PM: Checking swsusp image.
[   18.695593] PM: Resume from disk failed.
[   18.723157] kjournald starting.  Commit interval 5 seconds
[   18.723172] EXT3-fs: mounted filesystem with ordered data mode.
[   18.826724] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   18.874754] hda: WDC WD800BB-00JHC0, ATA DISK drive
[   19.023718] usb 2-1: configuration #1 chosen from 1 choice
[   19.266265] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   19.423336] usb 2-2: configuration #1 chosen from 1 choice
[   19.546158] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   19.550907] Probing IDE interface ide1...
[   19.673843] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   19.832131] usb 3-1: configuration #1 chosen from 1 choice
[   20.417188] hdc: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[   21.088766] ide1 at 0x170-0x177,0x376 on irq 15
[   25.224311] eth0: link down
[   26.387411] NET: Registered protocol family 17
[   26.868042] agpgart: Detected VIA VT3314 chipset
[   26.878348] agpgart: AGP aperture is 128M @ 0xf0000000
[   27.035795] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.038255] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.064823] input: PC Speaker as /class/input/input2
[   27.226283] hda: max request size: 128KiB
[   27.226381] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   27.226463] hda: cache flushes supported
[   27.226523]  hda: hda1 hda2 hda3
[   27.326201] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   27.326214] Uniform CD-ROM driver Revision: 3.20
[   27.380374] parport: PnPBIOS parport detected.
[   27.380521] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   27.458549] [ueagle-atm] driver ueagle 1.4 loaded
[   27.495864] Linux video capture interface: v2.00
[   27.551879] usb 3-1: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9022) : Eagle II pots
[   27.673738] usb 3-1: reset full speed USB device using uhci_hcd and address 2
[   27.675793] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   27.803886] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   27.804037] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   27.832609] usb 3-1: [ueagle-atm] pre-firmware device, uploading firmware
[   27.832642] usb 3-1: [ueagle-atm] loading firmware ueagle-atm/eagleII.fw
[   27.832662] usbcore: registered new interface driver ueagle-atm
[   27.864535] usb 3-1: [UEAGLE-ATM] firmware is not available
[   28.002386] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   28.362428] usbcore: registered new interface driver gspca
[   28.362436] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   28.396925] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.05
[   28.397024] usbcore: registered new interface driver zc0301
[   28.556972] fuse init (API version 7.8)
[   28.568987] lp0: using parport0 (interrupt-driven).
[   28.624431] Adding 996020k swap on /dev/disk/by-uuid/faa1e6cc-aa1e-447e-8854-50e92f381f3f.  Priority:-1 extents:1 across:996020k
[   28.779666] EXT3 FS on sda1, internal journal
[   31.440309] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   31.505142] NTFS volume version 3.1.
[   31.649143] NTFS volume version 3.1.
[   37.156287] ibm_acpi: ec object not found
[   37.312354] No dock devices found.
[   37.390641] Using specific hotkey driver
[   38.238213] input: Power Button (FF) as /class/input/input4
[   38.238262] ACPI: Power Button (FF) [PWRF]
[   38.238357] input: Power Button (CM) as /class/input/input5
[   38.238385] ACPI: Power Button (CM) [PWRB]
[   38.314686] pcc_acpi: loading...
[   43.916311] ppdev: user-space parallel port driver
[   44.864773] Bluetooth: Core ver 2.11
[   44.864856] NET: Registered protocol family 31
[   44.864859] Bluetooth: HCI device and connection manager initialized
[   44.864862] Bluetooth: HCI socket layer initialized
[   44.910312] Bluetooth: L2CAP ver 2.8
[   44.910320] Bluetooth: L2CAP socket layer initialized
[   45.047582] Bluetooth: RFCOMM socket layer initialized
[   45.047616] Bluetooth: RFCOMM TTY layer initialized
[   45.047620] Bluetooth: RFCOMM ver 1.8
[   60.167604] NET: Registered protocol family 10
[   60.167782] lo: Disabled Privacy Extensions
[   60.167862] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  117.750399] ISO 9660 Extensions: Microsoft Joliet Level 1
[  117.765782] ISOFS: changing to secondary root
[  750.091610] usb 3-1: USB disconnect, address 2
[ 1130.876230] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1130.908917] ISO 9660 Extensions: RRIP_1991A
[ 2612.000709] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2612.034508] ISO 9660 Extensions: RRIP_1991A
[ 2745.604266] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2745.636751] ISO 9660 Extensions: RRIP_1991A
[ 2782.151159] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2782.183806] ISO 9660 Extensions: RRIP_1991A
[ 2817.807547] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2817.860041] ISO 9660 Extensions: RRIP_1991A
[ 3062.386735] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 3062.438492] ISO 9660 Extensions: RRIP_1991A
[ 3560.247856] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 3560.397875] usb 3-1: configuration #1 chosen from 1 choice
[ 3560.399840] usb 3-1: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9022) : Eagle II pots
[ 3560.511608] usb 3-1: reset full speed USB device using uhci_hcd and address 3
[ 3560.662492] usb 3-1: [ueagle-atm] pre-firmware device, uploading firmware
[ 3560.662548] usb 3-1: [ueagle-atm] loading firmware ueagle-atm/eagleII.fw
[ 3560.667679] usb 3-1: [UEAGLE-ATM] firmware is not available
[ 3658.699895] usb 3-1: USB disconnect, address 3
[ 4044.305792] capifs: Rev 1.1.2.3
[ 4131.235538] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 4131.385565] usb 3-1: configuration #1 chosen from 1 choice
[ 4131.388554] usb 3-1: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9022) : Eagle II pots
[ 4131.503284] usb 3-1: reset full speed USB device using uhci_hcd and address 4
[ 4131.654169] usb 3-1: [ueagle-atm] pre-firmware device, uploading firmware
[ 4131.654217] usb 3-1: [ueagle-atm] loading firmware ueagle-atm/eagleII.fw
[ 4131.659900] usb 3-1: [UEAGLE-ATM] firmware is not available
[ 4359.475426] usb 1-7: new high speed USB device using ehci_hcd and address 7
[ 4359.608157] usb 1-7: configuration #1 chosen from 1 choice
[ 4359.698888] usbcore: registered new interface driver libusual
[ 4359.709997] Initializing USB Mass Storage driver...
[ 4359.710149] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4359.710236] usb-storage: device found at 7
[ 4359.710241] usb-storage: waiting for device to settle before scanning
[ 4359.710246] usbcore: registered new interface driver usb-storage
[ 4359.710252] USB Mass Storage support registered.
[ 4364.706280] usb-storage: device scan complete
[ 4364.707520] scsi 2:0:0:0: Direct-Access     USB2.0   Mobile Disk      1.00 PQ: 0 ANSI: 2
[ 4364.710362] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[ 4364.712344] sdb: Write Protect is off
[ 4364.712353] sdb: Mode Sense: 00 00 00 00
[ 4364.712359] sdb: assuming drive cache: write through
[ 4364.714594] SCSI device sdb: 4030464 512-byte hdwr sectors (2064 MB)
[ 4364.715218] sdb: Write Protect is off
[ 4364.715223] sdb: Mode Sense: 00 00 00 00
[ 4364.715229] sdb: assuming drive cache: write through
[ 4364.715237]  sdb: sdb1
[ 4364.854353] sd 2:0:0:0: Attached scsi removable disk sdb
[ 4364.854431] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 4462.830476] usb 3-1: USB disconnect, address 4
[ 4544.535652] usb 1-7: USB disconnect, address 7

---

### Post by quinnten83 on 2007-06-09
OK, he can't get on the internet, so he can't download from the repositories...

---

### Post by Arwen on 2007-06-11
Hello again!
I'm sorry for being an annoyance but is there anyone that can tell us what exactly do we have to do to make that modem work?There are so many people having trouble with that,there must be a manual or sth about it,:?:
What I want to know is the specific steps to install the drivers(modules)..I've messed my pc up trying with all kinds of commands that usually end up to errors and half-installed drivers which I don't know to uninstall completely.I also did the 'dmesg' command but I have no idea what it shows:(

I would really appreciate any response as I've been trying to have internet in my ubuntu-kubuntu5.10-next 6.06-and know ubuntu 7.04 for a year,wandering round in forums for help.I hope I'll make it work someday(and that the fact that the modem is Annex B-I have an ISDN line-doesn't cause problems to the installation) and finally get rid of damn XP! :-P

Thank you,

   Arwen

---

### Post by myle on 2007-11-18
He can try:
[http://ubuntuforums.org/showpost.php?p=2548455&postcount=3](http://ubuntuforums.org/showpost.php?p=2548455&postcount=3)

---

