---
title: "[SOLVED] yaboot error"
date: 2008-05-23
forum: Apple Hardware Users
---

### Post by rossmc92 on 2008-05-23
Every time I try to install Ubuntu 8.04 on my g4 powerpc the same yaboot error appears. I am told that yaboot has failed to install but I have the option to try again. When I try again the same thing happens. I think it's got something to do with having yaboot already installed from a previous Xubuntu installation, can someone confirm this and if so, what can I do to solve this problem?

---

### Post by oswaldkelso on 2008-05-23
My experiances may help [http://www.my2bits.org/?p=49](http://www.my2bits.org/?p=49)

see what your openfirmware path is

#ofpath /dev/hda

it should look something like this:

device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:

if your drive is not hda enter the correct name hdb sda etc

look at your yaboot.conf file and see if the path is correct

#nano /etc/yaboot.conf


If not back it up and edit it.

#cd /etc ; cp yaboot.conf yaboot.confbackup


Then bless the yaboot file

# ybin -v

if all goes well yaboot will be blessed with Holy penguin pee and   hay presto linux boots.

Edit: If you have osx installed and can start linux with the Alt key on boot. You could reset openfirmware to osx. Just restart with the Alt key held down edit yaboot and run ybin -v this way ensures the there is only one yaboot as osx will have overwritten any others.

# fdisk -l

 will show you your partitions. your yaboot.conf should point to the boot partition shown there.

---

### Post by stream303 on 2008-05-23
> **rossmc92 said:**
> Every time I try to install Ubuntu 8.04 on my g4 powerpc the same yaboot error appears. I am told that yaboot has failed to install but I have the option to try again.

Are you trying to install to an external firewire drive?

Oswaldkelso has some great advice, and when you come across this error don't stop when it brings you back to the menu.  Just accept the error, and then step through the rest of the menus to finish the installation - then you go back manually to edit your yaboot.conf

---

### Post by rossmc92 on 2008-05-23
> **stream303 said:**
> Are you trying to install to an external firewire drive?

Oswaldkelso has some great advice, and when you come across this error don't stop when it brings you back to the menu.  Just accept the error, and then step through the rest of the menus to finish the installation - then you go back manually to edit your yaboot.conf

No, I'm not trying to install an external firewire drive and I did skip this error, both times. I'm also to nooby to understand much of what your asking. Your asking me to edit yaboot.conf but how do I do this? Where do I find it?

---

### Post by stream303 on 2008-05-24
Which machine is it?
[http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html](http://www.everymac.com/systems/apple/powermac_g4/index-powermac-g4.html)

Is this unit second-hand or do you know the history of any hardware changes made to it?

Did the previous Xubuntu installation actually work?

Are you trying to dual-boot, or are you devoting the machine to Ubuntu?  If you are devoting it solely to Ubuntu, and not trying to preserve any previous installations, at guided partitioning, tell it to "use whole disk".  Of course this will wipe out everything, so backup your data!

This machine might also be one of the dual-hd drive machines, which have been known to be finicky but let's find out...

---

### Post by oswaldkelso on 2008-05-24
> **rossmc92 said:**
> No, I'm not trying to install an external firewire drive and I did skip this error, both times. I'm also to nooby to understand much of what your asking. Your asking me to edit yaboot.conf but how do I do this? Where do I find it?

A few questions:

are you dual booting with osx? If so you can over write your yaboot.conf.

in osx: system-preferences > startup-disk > select your osx disk and restart from your linux cd and install.

If you dual boot linux with another distro:

you can edit your other distros yaboot.conf file and bless it to make it work. Then select your distro of choice on boot.


If you have no os installed so a blank hard drive and can wipe it. I would use an osx disk or mac os disk, (if you have one) or [debian net install cd]("http://www.debian.org/CD/netinst/") to erase the hard drive. Then try reinstalling again. This way there is no left over yaboot.conf files confusing the install. 

Some distros are better than others with some hardware. 

for example my scsi card is not recognised by openfirm ware, I have osx on that drive and can not select my linux distros with the alt key on boot. if I put osx on a normal drive I can. PITA. On my g4 fedora and yellowdog found the scsi ofpath. slackintosh ubuntu and debian failed to report the ofpath correctly though debian and ubuntu did work when selecting x from yaboot
## to get the open firmware path for my scsi drive I booted into yellowdog and ran

[root@localhost ~]# ofpath /dev/sda2
/pci@f2000000/ADPT,29160@13/@0:2

I digress.

Fill me in with a bit more info so it's clear where your starting from. If you get stuck just post back and I or some one will  walk you through it.

---

### Post by rossmc92 on 2008-05-25
Sorry everyone for the slow respond I'm just putting and end to this post because I accidentally deleted osx (so yes I was trying to dual boot) and now I'm using Ubuntu 8.04. Already It's got problems:

1. No sound. It doesn't seem to be detecting my sound card at all. The volume icon at the top right has that red circle with the slash through it and when trying to unmute it or change volume I get the following error: No volume control gstreamer plugins and/or devices found.

2. I soon found out you can't get the offical Adobe Flash Player for powerpc and havent been able to find much reliable third-party ones.

As usual, any help is greatly appreciated.

---

### Post by frog_pilot on 2008-05-25
the sound-issue
open your modules file with root privileges by executing the following in a terminal ```
sudo gedit /etc/modules
```


It should look like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

apm_emu
loop
sbp2
therm_windtunnel
fuse
```


add the line
```
snd-powermac
```


save+exit+reboot

Voila


the flash issue:

you need to install "gnash"

by opening SYSTEM > ADMINISTRATION > SYNAPTIC

search by name for gnash and mark everything related to it for install.

For youtube and the like you might be willing to install java. look for the medibuntu repository at [www.medibuntu.org](www.medibuntu.org). There you will find further reference for adding multimedia support nad java.

---

### Post by rossmc92 on 2008-05-25
> **frog_pilot said:**
> the sound-issue
open your modules file with root privileges by executing the following in a terminal ```
sudo gedit /etc/modules
```


It should look like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

apm_emu
loop
sbp2
therm_windtunnel
fuse
```


add the line
```
snd-powermac
```


save+exit+reboot

Voila


the flash issue:

you need to install "gnash"

by opening SYSTEM > ADMINISTRATION > SYNAPTIC

search by name for gnash and mark everything related to it for install.

For youtube and the like you might be willing to install java. look for the medibuntu repository at [www.medibuntu.org](www.medibuntu.org). There you will find further reference for adding multimedia support nad java.

Thanks a lot everything works great. I would thank you but I'm nooby and don't know how to. BTW how do I mark this as solved?

---

### Post by frog_pilot on 2008-05-25
thanks with the star-button beneath the post (besides quote etc.)

solved with "thread tools" above the text boxes :)

---

