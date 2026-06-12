---
title: "compiz in xubuntu how?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by nexttry on 2008-02-22
compiz is that flahsy looking thing?

 i wrote sudo apt-get install compiz and i think it worked.
however i just remember that what i did when installing another program so im not sure what i did.

i use xubuntu 7,10 on a 1386.

so what should i do now?

thanks

---

### Post by sisco311 on 2008-02-22
in xubuntu compiz is not installed by default you can install it:

```
sudo aptitude install compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 python-compizconfig
```to run compiz press Alt+F2 and type: compiz --replace

go to Aplications -> Settings -> Advanced Desktop Effects Settings an select your plugins you want

to autostart compiz edit your session file:

```
gksu mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```and replace

> Client0_Command=xfwm4with
 > Client0_Command=compiz

---

### Post by nexttry on 2008-02-22
okay while im writing this im not sure what to do.

i have opened up the window and replaced but i dont know how to save???

---

### Post by sisco311 on 2008-02-22
press Ctrl+s or select Save option from the File menu

---

### Post by nexttry on 2008-02-22
ok i did save it and clicked around alittle in that settings window but nothing has changed
do i need to reboot or something?

---

### Post by sisco311 on 2008-02-22
open a terminal:

Applications -> Accessories -> Terminal

and type:
```
compiz --replace
```
press Enter.

post the output of the command.

---

### Post by nexttry on 2008-02-22
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
no /usr/bin/metacity found, exiting

---

### Post by sisco311 on 2008-02-22
edit back your session file to Client0_Command=xfwm4.

to run compiz you need to install the restricted driver of your video card.
Applications -> System -> Restricted Drivers Manager 


what type of video card do you have?

---

### Post by iwandi on 2008-02-22
I tryed this today on a freh system and i geht this.

[PHP]sudo aptitude install compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 python-compizconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for compiz-fusion-plugins-extra
No candidate version found for compiz-fusion-plugins-main
No candidate version found for libcompizconfig0
The following packages are BROKEN:
  python-compizconfig 
The following NEW packages will be installed:
  compizconfig-settings-manager 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 540kB of archives. After unpacking 3486kB will be used.
The following packages have unmet dependencies:
  python-compizconfig: Depends: libcompizconfig0 which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
[/PHP]

sources.list
[PHP]deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security multiverse
[/PHP]

---

### Post by sisco311 on 2008-02-22
> **iwandi said:**
> I tryed this today on a freh system and i geht this.

[php]sudo aptitude install compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 python-compizconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for compiz-fusion-plugins-extra
No candidate version found for compiz-fusion-plugins-main
No candidate version found for libcompizconfig0
The following packages are BROKEN:
  python-compizconfig 
The following NEW packages will be installed:
  compizconfig-settings-manager 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 540kB of archives. After unpacking 3486kB will be used.
The following packages have unmet dependencies:
  python-compizconfig: Depends: libcompizconfig0 which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
[/php]sources.list
[php]deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security multiverse
[/php]

go to the Applications -> System -> Software Sources -> Third Party Software and make sure that the cdrom entry is not checked.or comment out the first line in your source list with a #

than from the terminal:
```
sudo aptitude update
sudo aptitude safe-upgrade
```and try again to install compiz

---

### Post by nexttry on 2008-02-22
ok i switched back

i dont have any video card. i use the onboard.

will compiz not work ?

---

### Post by sisco311 on 2008-02-22
> **nexttry said:**
> ok i switched back

i dont have any video card. i use the onboard.

will compiz not work ?

depends.

please post the output of:
```
lspci
```
and
```
lshw
```

---

### Post by iwandi on 2008-02-22
i just seen it my self

th Installer deactivated som sources

now it is working :D

---

### Post by nexttry on 2008-02-22
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 651 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
----
and:
 description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 479MB
     *-cpu
          product: Intel(R) Celeron(R) CPU 2.50GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
          configuration: id=0
        *-cache
             description: L1 cache
             physical id: 0
             size: 8KB
     *-pci
          description: Host bridge
          product: 651 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32 module=sis_agp
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: 65x/M650/740 PCI/AGP VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS962 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 25
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-serial
             description: SMBus
             product: SiS961/2 SMBus Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             configuration: driver=sis96x_smbus latency=0 module=i2c_sis96x
        *-ide
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128 module=pata_sis
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.6
             bus info: pci@0000:00:02.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=32 maxlatency=11 mingnt=52
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 10
             bus info: pci@0000:00:10.0
             logical name: eth0
             version: 10
             serial: 00:0d:61:09:ed:31
             width: 32 bits
             clock: 33MHz

---

### Post by sisco311 on 2008-02-22
bad news. i googled your video card and found this:
> **3D Graphical Acceleration**

 Asus L3355M's video controller is: "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter", as you can easily check with the "lspci" utility.
 Let's start from saying that there are not Linux drivers for this chipset that allow hardware acceleration at the moment.
 This simply means no Beryl, no Compiz, no 3d desktop, no full speed GoogleEarth for you. At least for the moment.
 I know that is sad, but this is the truth.
 Anyway, there are other ways to beautify your desktop. Let's see some of them.
 to uninstall compiz:
```
sudo aptitude purge compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager libcompizconfig0 python-compizconfig
```

---

### Post by nexttry on 2008-02-22
well thanks anyway

---

