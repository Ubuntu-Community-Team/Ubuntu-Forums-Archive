---
title: "laptop wireless not found!"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by sleeper414 on 2008-02-09
i know may folks have had troubles with ubuntu finding a wireless connection on laptops.
 i am no exception.

it will connect with no effort to wired, but it doesnt seem to be finding the wireless card.

this is an acer travelmate 2430

i would geuss there are "drivers" in synaptic or terminal to install?

oh ya, im running gutsy.

---

### Post by Presto123 on 2008-02-09
Look in System/Administration/Restricted Drivers Manager and see if it shows up.

Post back here whether or not it does.

---

### Post by sleeper414 on 2008-02-09
yes it does, i installed one before posting. there is one more, but it wouldnt let me install.

it simply says it isnt installed as soon as i click on the box...instant reject.

i also ran lspci in terminal

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by anewguy on 2008-02-09
Put your Windows drivers (non-Vista) - the.inf and .sys files it needs - on your desktop, then do the following:

Check via synaptic package manager that ndiswrapper and utils are installed - if not, you will need a wired connection to get them or an older LiveCD.

In a terminal window:

sudo ndiswrapper -l  <= lower case "L"

if anything is returned, removed them using the following until the list is empty:

sudo ndiswrapper -r xxxxx  <= where xxxxx is a name returned in the list command

cd ~/Desktop

sudo ndiswrapper -i xxxxxx.inf  <= lower case "i", where xxxxxx is the name of your drivers' .inf file - usually something like bcmwl5a for the bcm4318 series

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m


I think that should do it - let us know!:)

---

### Post by Presto123 on 2008-02-09
Ah, Broadcom...Everybody's favorite Devil Child.

LOL

(Just make sure you are on wired connection first when you try this.)

I'm unsure if you have already answered this or not, but when you are on a wired connection and click on the box to enable the card, is this where it is rejecting it? If you haven't already tried this: when it pops up asking for a driver, just select the internet from the options.

Some Broadcoms are better suited for Ndiswrapper...

---

### Post by sleeper414 on 2008-02-10
ok.
presto.
it says i need bcm43xx-fwcutter

but, i cant find it in synaptic.

where should i go to get this?

---

### Post by jan quark on 2008-02-10
try this guide it is for the broadcom 4311 but the fwcutter is the same

[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

I removed my broadcom card completely from my lappy today just as a remark  :)
and plugged in an usb wlan stick and I am happy now :):):):)

---

### Post by sleeper414 on 2008-02-10
modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Operation not permitted


i dont get it.

i also followed [http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)
this thread to the letter, now my network wont even show a wireless option.
all commands got some sort of reply saying somthing like "allready installed"

baffling.

---

### Post by jan quark on 2008-02-10
sleeper414

I can tell you that ndiswrapper works for broadcom cards or does not work
for me the broadcom card was a total disaster no ndiswrapper method worked
even the fwcutter method was flawed, heavy lags on internet, random disconnections, 

no joy

but try the fwcutter method perhaps it is passably stable for you

or just invest 25$ and buy another card saving yourself a lot of trouble

sorry if this is a uncommon solution, but I only speak because I have experienced it for myself

---

### Post by sleeper414 on 2008-02-10
i think all i need to do is install fwcutter, i have the tarball on my desktop, but when i extract it. nothing happens.....i just need to kn ow how to install the fwcutter and i think it will work.

---

### Post by sleeper414 on 2008-02-10
@ a newguy
--------------------
i ttried your method as well....
--------------here is what happened


chris@chris-laptop:~$ sudo ndiswrapper -l 
[sudo] password for chris:
bcmwl5 : invalid driver!
chris@chris-laptop:~$ cd ~/Desktop
chris@chris-laptop:~/Desktop$ sudo ndiswrapper -1 bcmwl5.inf
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
chris@chris-laptop:~/Desktop$ i
The program 'i' is currently not installed.  You can install it by typing:
sudo apt-get install iprint
You will have to enable component called 'universe'
bash: i: command not found
chris@chris-laptop:~/Desktop$ sudo apt-get install iprint
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package iprint
chris@chris-laptop:~/Desktop$

---

### Post by sleeper414 on 2008-02-10
ok i have inbstalled all restricted drivers, ndiswrapper etc...now, in the network manager there is NO wireless option.
????

---

### Post by rkd on 2008-02-10
sleeper414:

I don't know whether you noticed this, but in post #11, you made a typo that caused the ndiswrapper command not to work.

You entered:```
sudo ndiswrapper -1 bcmwl5.inf
```
The character after the minus sign should have been small letter "I", not the number "1". The command should have been:```
sudo ndiswrapper -i bcmwl5.inf
```When a command displays a description of how it is supposed to be used, that usually means that it didn't understand the options you typed. I know it isn't very clear that there was a problem, but that is the way many of the commands work -- they don't come straight out and say there was an error.

One way to avoid typos like that when you are trying to enter a command that you find in a post or HOWTO is to use the mouse to copy the command from the browser window and paste it into the Terminal window. I know you can't always do that, especially if you are reading the directions on a different computer than the one you are trying to fix. So when you can't copy and paste the command, be especially careful to type the command EXACTLY as it was shown.  Sometimes the font used makes it very difficult to distinguish between characters that look very similar, especially when the writer of the post didn't use the Code tag for the command. If you are caught in that situation, try copying the command line with the mouse, and paste it into an editor or word processor that uses Courier or another font that makes it easier to distinguish among similar characters. Then you'll have less chance of typing the command incorrectly.

So since that command in post #11 didn't work, it might be that the driver did not get installed (unless something else you tried managed to install it). So you could check to see whether it is installed by using the command:```
sudo ndiswrapper -l
```(That's a lowercase letter L after the minus.) If it shows bcmwl5.inf in the output, then the driver did get loaded. If it does not show bcmwl5.inf, then maybe it would help to redo the commands suggested by anewguy with the typo corrected.

---

