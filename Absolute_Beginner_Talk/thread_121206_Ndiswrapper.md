---
title: "Ndiswrapper"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by StageMgr2Stars on 2006-01-24
Okay, so I am a linux newb and I am trying to get my wireless working. Dell Wireless Lan 1370. I am trying to use this "http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation"

but I cant even manage to get past the Prerequisites let alone trying to install ndiswrapper... seriously I am new to commands and I copy and paste whats there and nothing happens or I get errors... is there something else I need to do?

see:

courtneyscott@courtneyscott:~$ ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build
bash: kernel-version: No such file or directory
courtneyscott@courtneyscott:~$

I need to know what EXACTLY I have to type in to install it... I havent got a clue.


Thanks Folks


EDIT: when I type "ndiswrapper" into the terminal I get this: 

Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
courtneyscott@courtneyscott:~$ 


does that mean its already installed???

---

### Post by az on 2006-01-24
Go to the ndiswrapper source tree and do

sudo make uninstall
sudo apt-get install ndiswrapper-utils

You are good to go.  Ndiswrapper is already included in ubuntu - you don't have to compile it.

---

### Post by StageMgr2Stars on 2006-01-24
[QUOTE=azz]Go to the ndiswrapper source tree and do

sudo make uninstall
sudo apt-get install ndiswrapper-utils

You are good to go.  Ndiswrapper is already included in ubuntu - you don't have to compile it.[/QUOTE]


Kay.... how do I go the ndiswrapper source tree? What is a source tree?

---

### Post by carlosqueso on 2006-01-24
Actually, it sounds like you already have ndiswrapper installed.

Download the WINDOWS drivers for your card (probably in a zip file) and unzip the file.  Then go to the folder that you extracted the files and type ```
ndiswrapper -i <name of .inf file>
``` MAKE SURE to pay attention to capital letters--linux is CaSe SeNsItIvE.   Then type ```
sudo modprobe ndiswrapper
``` and it should work.   If it does, open up a terminal and type ```
sudo ndiswrapper -m
```  Hope that helps.

---

### Post by gosh on 2006-01-24
If you want to install ndiswrapper you also can use System->Administration->Synaptic Package Manager.

Then go to wiki.ubunut.com/HowToSetupNdiswrapper

---

### Post by az on 2006-01-25
[QUOTE=StageMgr2Stars]Kay.... how do I go the ndiswrapper source tree? What is a source tree?[/QUOTE]
Well, by following those instructions, you are installing ndiswrapper from source.  Have you done that?  Did you download a tarball (ndiswapper-xx-xx-xx.tar.gz?)

If you have not, nevermind.

Follow carlosqueso's advice.

---

### Post by StageMgr2Stars on 2006-01-26
[QUOTE=carlosqueso]Actually, it sounds like you already have ndiswrapper installed.

Download the WINDOWS drivers for your card (probably in a zip file) and unzip the file.  Then go to the folder that you extracted the files and type ```
ndiswrapper -i <name of .inf file>
``` MAKE SURE to pay attention to capital letters--linux is CaSe SeNsItIvE.   Then type ```
sudo modprobe ndiswrapper
``` and it should work.   If it does, open up a terminal and type ```
sudo ndiswrapper -m
```  Hope that helps.[/QUOTE]


Kay I typed in what you told me to and got this:

courtneyscott@courtneyscott:~$ ndiswrapper -i <bcmwl5.inf>
bash: syntax error near unexpected token `newline

The files (.inf and .sys) are on my desktop.

Hellllp

---

### Post by gosh on 2006-01-27
[QUOTE=StageMgr2Stars]Kay I typed in what you told me to and got this:

courtneyscott@courtneyscott:~$ ndiswrapper -i <bcmwl5.inf>
bash: syntax error near unexpected token `newline

The files (.inf and .sys) are on my desktop.

Hellllp[/QUOTE]

You should leave the < and > out.
~$ndiswrapper -i bcmwl5.inf

---

### Post by byen on 2006-01-27
First of all.. as AZZ has mentioned before ..ndiswrapper comes with the UBUNTU Install cd. And as for compiling it to work with your wireless card...here is a [how-to]("http://www.ubuntuforums.org/showthread.php?t=25683") that might do the trick!!!.
Note: It is written for Hoary but works for Breezy too!
Hope that helps! Goodluck!

---

