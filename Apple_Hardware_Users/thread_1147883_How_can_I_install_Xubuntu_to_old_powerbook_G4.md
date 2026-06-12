---
title: "How can I install Xubuntu to old powerbook G4?"
date: 2009-05-03
forum: Apple Hardware Users
---

### Post by nintennuendo on 2009-05-03
I've got an old powerbook G4 I want to use for web browsing and IMing when my good computer is otherwise occupied.  I downloaded the xubuntu powerpc disc for 9.04 but with regular live and with live video=oflay or something, i just get a black screen and then some weird effects respectively.

do I need the alternate CD?  Is there any way I can use a usb stick?  I don't have anymore blank CDs and I really don't want to go get some more just for this.

The powerbook has around 512 megs of ram and some 500 megahurtses of CPUs.  If not Xubuntu, what other linux can I use on the pbook?

---

### Post by sms0611 on 2009-05-04
Hi,

  I am running Ubuntu 8.04 on a powermac G4 (quicksilver). During my many install-test-reinstall-test..... phase I have written copious notes on what to do (in case I need to do it again).

If you would like to PM me with an email address I will send you a copy of these notes. They will walk you through the installation procedure and some of the post-installation procedures (to get everything working properly) with this version of Ubuntu.

Although these are written for a powermac they should also, with a little tweaking depending on the graphics/sound card work on the powerbook.

---

### Post by nintennuendo on 2009-05-04
Just post it here

---

### Post by sms0611 on 2009-05-04
Will need to edit it to get it to post but will do.

What graphics/sound cards do you have ?

---

### Post by nintennuendo on 2009-05-04
whatever comes with the classic powerbook G4...

ATI Mobility Radeon with 16MB of SDRAM, AGP 4x   if wikipedia is to be believed.

Addition:  I went and bought some cds, burn the alternative boot disk installer for Xubuntu 9.04 for PPc and it will not boot no matter what I do.  What now?

---

### Post by sms0611 on 2009-05-05
OK. Here goes, I hope you can make some sense of this and that it helps, let me know one way or the other.

Best of luck,

Steve

```

**Installing UBUNTU 8.04 (Hardy Heron) on PowerMac G4**

**Standard Instalation**

Download and burn CD iso

Put CD in Internal Drive (Disconnect any external CD/DVD drives and printers. Wire connect to network router)
Reboot

Stage 1 Boot (c)
Booting CDROM…

boot: (install-powerpc) (hyphen key next to 0)

Select Language (English)
Select Country (other, Spain) *(set to yours)*

Detect Keyboard (No)
Origin of keyboard (Sweden) *(set to yours)*
Keyboard layout (Sweden – Macintosh) *(set to yours)*

Cofigure Network
(eth0: Apple Computer Inc. UniNorth GMAC (Sun GEM))

Hostname (ubuntu) *(set to yours)*
Time zone (Madrid) *(set to yours)*

Partitioning (Guided - use entire disk) Be sure you really want to do this as there is no way back.

Select disk to partition (IDE1 master (hda))

Write changes to disk (yes)

Now wait whilst the install takes place

Full name for new user (Steve) *(set to yours)*
Username for account(steve) *(set to yours)*
Pasword(********) *(set to yours)*
Re-enter password(********) *(set to yours)*
HTTP proxy()

Download language support(yes)

Now wait whilst software installs (takes a long time)

System clock to UTC (yes)

Take out CD
Installation Complete(Continue)

**Expert Installation**

Download and burn CD iso
Put CD in Internal Drive (Disconnect any external CD/DVD or printers. Wire connect to network)
Reboot

Stage 1 Boot (c)
Booting CDROM…

boot: (expert-powerpc) (hyphen key next to 0)

1)	Choose language 
a.	English
b.	Other
c.	Spain *(set to yours)*
d.	En-US.UTF-8 *(set to yours)*
e.	En-GB.UTF-8 *(set to yours)*
f.	En-gb *(set to yours)*
g.	En-gb.ISO-8859-15 *(set to yours)*

2)	Configure the Keyboard
a.	Apple
b.	Sweden *(set to yours)*
c.	Sweden-Macintosh *(set to yours)*
d.	AltGr replacement (Both Logo keys)
e.	Compose Key (Right Alt)
f.	Encoding (UTF-8)
g.	Character Set (Latin 1)
h.	Font (VGA)
i.	Size (8)
j.	Virtual consoles tty1,tty2

3)	Detect and mount CD-ROM
a.	Usb-storage (continue)
b.	PC Card Services (Yes)
c.	PCMCIA (continue)
d.	(continue)

4)	Load debconf preconfig file

5)	Load installer components
a.	Choose-mirror
b.	Download-installer
c.	Continue

6)	Detect network Hardware
a.	Start card services (yes)

7)	Configure the network
a.	Eth0: Apple…..
b.	Auto configure (yes)
c.	Hostname (ubuntu)
d.	Domain name (MSHOME)

8)	Choose a Mirror
a.	Protocol (http)
b.	Mirror (UK)
c.	Archive mirror (ports.ubuntu.com)
d.	Proxy (continue)

9)	Download installer components
a.	(continue)

10)	Configure the clock
a.	Use NTP (yes)
b.	NTP Server (ntp.ubuntu.com)
c.	Madrid

11)	Detect Disks
a.	Card services (yes)
b.	(CONTINUE)

12)	Partition Disks
a.	(Guided – use entire disk)
b.	(IDE master (hda)…)
c.	All files in one partition
d.	Write changes (yes) (too late to go back now)

13)	Install base system
a.	Kernel (linux-powerpc)

14)	Set up users
a.	Shadow passwords (no)
b.	Root login (NO)
c.	Name (steve) *(set to yours)*
d.	Account (steve) *(set to yours)*
e.	Password(********) *(set to yours)*
f.	Verify(********) *(set to yours)*

15)	Configure package manager
a.	Mirror (yes)
b.	Protocol(http)
c.	Country(UK)
d.	Mirror(ports.ubuntu.com)
e.	Proxy()
f.	Restricted software(yes)
g.	Universe(yes)
h.	Multiverse(yes)
i.	Backport(yes)

16)	Select and Install software
a.	Language support(yes)

17)	Install yaboot
a.	Partition (/dev/hda2)
b.	Boot (continue)

18)	Finish Installation
a.	Set clock to UTC(yes)
b.	(continue)


Done system installed and working.
 
**Set up Graphics Card.**

If system boots up but you do not get the Gnome desktop then you have an Xorg graphics problem.

Press ctrl+alt+F1 (this should start a terminal, if it does not the install did not work)

Login: steve *(set to yours)*
Password: ******** *(set to yours)*
Start by removing any startup modules relating to your graphics card

sudo nano /etc/modules

mine looks like this (snd-powermac is needed later to get the sound working)

airport
apm_emu
loop
sbp2
fuse
snd-powermac


One thing to bear in mind.
The BUSID of the graphics card
use lspci to find it

0000:00:10.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev a1)

it´s the 00:10.0 bit in front but this is in hex so translates to 00:16.0 in my case in xorg.

cd  /etc/X11 (note capital X)

sudo cp xorg.conf  xorg.conf.orig
sudo nano xorg.conf (i’ve not put in the comments from the Start of the file just the important bits)

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "apple"
Option "XkbLayout" "se"
Option "XkbVariant" "mac"
Option "XkbOptions" "lv3:win_switch,compose:ralt"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
BusID "PCI:0:16:0"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Save the file and exit.
Now restart GNOME using

sudo /etc/init.d/gdm restart

type: ctrl-alt-f7 (to switch back to GNOME at any time)

if you still have a black screen have a look at the xorg log file in

/var/log/Xorg.0.log (note capital X)

look for any lines starting (EE) (NI) or (??) this should point to whats going wrong.

Here are a couple of usefull articles which may help if things aren’t going well

http://www.debianuniverse.com/readonline/chapter/04
http://www.linuxforums.org/forum/ubu...age-128-a.html
 
**Set up automatic logon**

System->administration->login window
	Users
	Automatic login (select account name)

To edit files

sudo nano filename
or
gksudo gedit filename

**Add sound card module**
 
In /etc/modules
snd-powermac

 in /etc/rc.local
 amixer sset ‘Auto Mute’ off
 amixer sset ‘PC Speaker’ on

**Add Video and Sound**

Install VLC + ALSA plugin

Install latest ALSA version ALSA v.1.0.19

Go to the following page and at the end of the post you will see a list of files

http://ubuntuforums.org/showthread.php?t=1046137

The following is the one you want

AlsaUpgrade-1.0.x-rev-1.16.tar

Then almost follow the posted advice

Short Alsa-Upgrade script install instructions:
1. download the script and save it somewhere (click on the file)
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.x-rev-1.16.tar
4. sudo ./AlsaUpgrade-1.0.x-rev-1.16.sh -di

the -di stands for download and install which (unfortunately) is missing from the original post

This will take at least 15 minutes so go and get a beer or a cup of coffee.
When the script is finished

Run alsaconf

**Add file sharing**

Install samba-server

Modify 
/etc/hosts
add 192.168.0.191 ubuntu.MSHOME ubuntu

/etc/network/interfaces
change iface … dchp to static
add (with values from ifconfig and netstat –rn)
address nnn.nnn.n.nnn
netmask nnn.nnn.nnn.n
broadcast nnn.nnn.n.nnn
gateway nnn.nnn.n.n
network nnn.nnn.n.n

/etc/samba/smb.conf 
add Share definitions

```

---

### Post by mkvnmtr on 2009-05-05
I just booted the live disk for 9.04 on my G4 Ibook. I used the option live-nosplash-powerpc and it booted and looked like everything worked. The same option should be on the xubuntu disk. I haven't tried to install I really want to upgrade to keep all my apps but was unable to upgrade the normal way. I am burning the alt install disk and think I will try to upgrade from it. If that doesn't work I will try the live disk. I really don't stand to loose anything but a little time. I have my home on another partition.

---

### Post by nintennuendo on 2009-05-05
So the problem either way with any disc is after a while, the screen goes psychadelic and shows some trippy colors.  I think its still doing things, but I just can't see.  Its not a glitch or something, i think it just might be the mac.  they almost look like magnet-caused errors if it wasn't screenwide and so.. odd.  Any ideas?

---

### Post by stream303 on 2009-05-06
That powerbook has enough horsepower and ram to be useful for sure.

Two issues really to tackle:  at the second-stage yaboot boot: prompt , are you adding kernel parameters to force the system to bypass the splash screen, which has been known to mess with cards even before they get to X:

```
Linux nosplash
```

You may even want to try an additional parameter:

```
Linux nosplash video=ofonly
```

Now you should at least see the boot stanza fly by, but you may still end up with bad graphics.

If so, you'll need to find a working xorg.conf file for that powerbook and edit /etc/X11/xorg.conf appropriately.

It would help if you pinned down the exact model so others might be able to help you out:

It looks to be this one:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_500.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_500.html)

So you would concentrate on getting an ATI, specifically the Rage 128 card going.  In the past, the R128 driver was the choice, but I haven't kept up with the ATI driver recommendations.

---

### Post by nintennuendo on 2009-05-06
[http://www.youtube.com/watch?v=P4WzM62CVWg](http://www.youtube.com/watch?v=P4WzM62CVWg)


Thats what it looks like booting up.  Sorry for the bad lighting.  Nothing I could do about it.

---

### Post by Semperfive on 2010-06-05
Mine does the exact same thing. Did you find a fix?

---

### Post by sha.goyjo on 2010-06-05
Seeings as you have the same graphics card as me (iBookg4), you should probably try this in your /etc/yaboot.conf:

```

Linux video=radeonfb radeon.modeset=0

```

I tried video=ofonly, and couldn't boot, just like you. I tried a lot of things. Right now, the KMS that ubuntu has decided is the "right path" is not quite ready yet. It's buggy, and IMO, DRI2 isn't quite worth it :-) . Tell us if that works. Moving the graphics to userspace is often a good choice regardless.

---

