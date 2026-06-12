---
title: "Building linux-wlan-ng"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by bruzer on 2007-06-27
:(I have just installed Ubuntu on my laptop and gotten all functions working except my Wifi. I have a Prizm3 usb chip set that I looked up on-line. The site I was referred to told me to download this file.

linux-wlan-ng-0.2.8.tar.bz2

The READ ME file says that I have to "build" linux-wlan-ng. What does this mean and how do I do this?

Thank You

Ronnie Bruzer

Here is a copy of the READ ME file if that will help:

* README
*
* Copyright (C) 2001 AbsoluteValue Systems, Inc.  All Rights Reserved.
* --------------------------------------------------------------------
*
* linux-wlan
*
*   The contents of this file are subject to the Mozilla Public
*   License Version 1.1 (the "License"); you may not use this file
*   except in compliance with the License. You may obtain a copy of
*   the License at [http://www.mozilla.org/MPL/](http://www.mozilla.org/MPL/)
*
*   Software distributed under the License is distributed on an "AS
*   IS" basis, WITHOUT WARRANTY OF ANY KIND, either express or
*   implied. See the License for the specific language governing
*   rights and limitations under the License.
*
*   Alternatively, the contents of this file may be used under the
*   terms of the GNU Public License version 2 (the "GPL"), in which
*   case the provisions of the GPL are applicable instead of the
*   above.  If you wish to allow the use of your version of this file
*   only under the terms of the GPL and not to allow others to use
*   your version of this file under the MPL, indicate your decision
*   by deleting the provisions above and replace them with the notice
*   and other provisions required by the GPL.  If you do not delete
*   the provisions above, a recipient may use your version of this
*   file under either the MPL or the GPL.
*
* --------------------------------------------------------------------
*
* Inquiries regarding the linux-wlan Open Source project can be
* made directly to:
*
* AbsoluteValue Systems Inc.
* [email]info@linux-wlan.com[/email]
* [http://www.linux-wlan.com](http://www.linux-wlan.com)
*
* --------------------------------------------------------------------
*
* Portions of the development of this software were funded by 
* Intersil Corporation as part of PRISM(R) chipset product development.
*
* --------------------------------------------------------------------

=======================================================================
Description:
The linux-wlan package is a linux device driver and subsystem
package that is intended to provide the full range of IEEE 802.11 MAC
management capabilities for use in user-mode utilities and scripts.
The package currently supports the Intersil 802.11b Prism2, Prism2.5, 
and Prism3 reference designs for PCMCIA, PCI, and USB.  Additionally,
the package includes support for PLX9052 based PCI to PCMCIA adapter
with a few different PCMCIA cards.

For a list of elements that are still undone, see the TODO file in 
this directory

=======================================================================
License:
See the COPYING and LICENSE files.

=======================================================================
Top level directory for linux-wlan-ng:
./add-ons	- additional programs that are not build from the 
                  top level make file
./doc		- source distribution documentation
./etc		- scripts used at run-time
./man		- man pages
./scripts	- contributed scripts that may do useful things
./src		- source code for various components

=======================================================================
Build Instructions:

NOTE: You may not need to build at all.  Binary packages are
available for various distributions.  See the FAQ for where to go.

NOTE: This release supports building four different drivers:

   prism2_cs	Driver for Prism2.x & Prism3  PCMCIA cards.
   prism2_pci	Driver for Prism2.5 (ISL3874) based _native_ PCI cards.
   prism2_plx	Driver for Prism2.x PCMCIA cards when used with 
		a PLX9052 PCI/PCMCIA adapter.
   prism2_usb   Driver for Prism2.x USB adapters.


Prerequisites:

To build linux-wlan-ng you will need:
   - Configured kernel source code for the kernel you are running.  
     Ideally, this will be the resulting tree after building your own 
     kernel.  Configured means that you have at least run 'make config',
     'make menuconfig', or 'make xconfig'.  If you are trying to build
     linux-wlan-ng for a previously existing kernel binary (one you did 
     not build yourself), look for help on the mailing lists because it 
     can be tricky.  I always run against kernels I've built myself, so I'm 
     not much help in this area.
   - The good David Leffler identified that if you are having difficulty
     with *_netlink_* symbols, you may have a problem with 'make clean' in
     the kernel tree.  Do a 'make mrproper' followed by 'make config' 
     and the rest of the kernel build process.  'make mrproper' does
     a more thorough cleaning of the kernel tree.  For more info, look
     for David's comments in the linux-wlan-user mailing list.
   - If you are building a driver for a PCMCIA card, you will also need
     the configured PCMCIA source code for the pcmcia_cs subsystem you
     are currently running.

Building linux-wlan-ng:

1)  untar the package using the command:

    tar zxvf linux-wlan-ng-X.Y.Z.tar.gz

2)  Make sure you have configured kernel and (optionally) pcmcia sources on 
    your system.  Note that if you are _only_ building the prism2_pci,
    prism2_plx, or prism2_usb drivers you don't need the pcmcia-cs 
    source tree.

3)  To configure the linux-wlan-ng package, run 'make config'.  The 
    following set of questions will be asked. The default answer is in
    braces (e.g. []).  Just press <Enter> to select the default answer:

   - "Build Prism2.x PCMCIA Card Services (_cs) driver? (y/n) [y]: "
        Select "y" if you want to build the Prism PCMCIA driver.
        If you select "n", the PCMCIA related questions below
        will not be asked.

   - Build Prism2 PLX9052 based PCI (_plx) adapter driver? (y/n) [y]: 
        Select "y" if you want to build the Prism driver for 
        PLX PCI9052 PCI/PCMCIA adapter based solutions.

   - Build Prism2.5 native PCI (_pci) driver? (y/n) [y]: 
        Select "y" if you want to build the Prism driver for 
        Prism2.5 ISL3874 based native PCI cards.  This includes
        PCI add-in cards and the mini-pci modules included in some
        notebook computers (but not all, some use internal USB modules).

   - Build Prism2.5 USB (_usb) driver? (y/n) [y]: 
        Select "y" if you want to build the Prism driver for 
        Prism2.5 ISL3873 based USB adapters.  This includes
        USB add-on modules and the internal modules included in some
        notebook computers.

   - Linux source directory [/usr/src/linux]: 
        The config script will attempt to automagically find your kernel
        source directory.  If found, the kernel source source directory
        will be presented as the default selection.  If the default
        selection is wrong, you may correct it here.

   - pcmcia-cs source dir [/usr/src/pcmcia-cs-3.1.29]: 
        If the "_cs" driver is selected above, the configure script will
        attempt to present a reasonable default for the pcmcia source
        directory.  If the presented directory is incorrect, you may
        change it here.  If the "_cs" driver is not selected, this
        prompt will not appear.

   - PCMCIA script directory [/etc/pcmcia]: 
        If the "_cs" driver is selected, this prompt allows you to 
        change the location where the pcmcia scripts will be installed.
        Only do this if you have installed the rest of the pcmcia_cs
        scripts to a non-default location.

   - Alternate target install root directory on host []:   
        This prompt allows you to specify an alternative root directory
        for the install process.

   - Module install directory [/lib/modules/2.2.20]: 
        Select where you want the driver modules to be installed.  The
        script constructs a default location using the output of uname.
        If you have not yet installed the kernel you will run linux-wlan
        with, and the new kernel has a different version string, you will
        need to change this value.

   - Prefix for build host compiler? (rarely needed) []: 
        When cross-compiling or using different compilers for kernel and
        user-mode software, it is sometimes (but rarely) necessary to 
        specify a different compiler prefix to use when compiling the 
        _tools_ that are built to run on the build host during the 
        linux-wlan-ng build process.

   - Build for debugging (see doc/config.debug) (y/n) [y]: 
        This option enables the inclusion of debug output generating
        statements in the driver code.  Note that enabling those statements
        requires the inclusion of insmod/modprobe command line arguments
        when loading the modules.  See the document doc/config.debug
        for more information.


5)  To build the package, run 'make all'

6)  To install the package, run 'make install' (as root).

=======================================================================
Configuring:

NOTE:  linux-wlan-ng does not fully implement the wireless extensions
       interface.  This means that you can't use iwconfig and its kin to 
       set things up.  Instead, read on!

As of linux-wlan-ng 0.1.16-pre5, the configuration and launch scripts have
been largely re-written.  pcmcia/rc/hotplug now all use a common library 
of routines and use the same set of configuration files.

Now, everything relevant exists in /etc/wlan/*

/etc/wlan/wlan.conf:

	This file maps between wlan devices and network IDs, and contains
	the names of all devices that should be initialized by the hotplug
	and rc scripts.

/etc/wlan/wlancfg-*

	These files are per-network configurations.  This makes it easy to 
	switch between different SSIDs and the various settings they may
	require, like WEP keys and whatnot.

The bare minimum you need to do to configure your system after a fresh driver
install:

0)  Nothing whatsoever.  out-of-the-box, the driver will attempt to associate
    with any access point within range.

However, we highly recommend setting up a configuration specifically for
your network, using the following method:

0)  This example assumes your network name/SSID is "MyHomeNetwork"
1)  cp /etc/wlan/wlancfg-DEFAULT /etc/wlan/wlancfg-MyHomeNetwork
2)  edit /etc/wlan/wlan.conf and change the SSID_wlan0 line to:
	SSID_wlan0="MyHomeNetwork"
3)  edit /etc/wlan/wlancfg-MyHomeNetwork, and make any necessary changes 
    necessary to support your network, such as WEP and whatnot.

------------------------------
FOR PCMCIA USERS:
A)  Edit /etc/pcmcia/network.opts file to set up your IP settings. 
    Note: for a station, the SSID you're connecting to will be appended to the 
    current pcmcia scheme name.  You can use this to have different
    IP setups for different wireless LANs you connect to (e.g. home vs. work).

    Note2:  This only applies if you are using a stock pcmcia-cs 
    package.  Most (if not all) distros use their own mechanisms for 
    configuring pcmcia network interfaces, and thus 
    /etc/pcmcia/network.opts may not even be present.

B)  Restart pcmcia-cs with the command:

    /etc/rc.d/init.d/pcmcia restart

C) Insert the card.  For most cards, a solid LED indicates that the 
    SSID you specified was found, a bss was joined, and the firmware 
    completed the authenticate and associate processes.

D) Run ifconfig and route to determine if your IP and route settings are
    listed as you wanted them.  It's also a good idea to look at the file
    /etc/resolv.conf to see if your nameserver address has been set up 
    correctly.

------------------------------
FOR PCI, PLX, OR USB USERS:
A) You must make sure that the drivers get loaded at boot time and that the 
   necessary initialization takes place.  The simplest way to do this is
   to add the following commands to your rc.local file:

     modprobe prism2_pci   [or prism2_usb/prism2_plx]
     wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
     wlanctl-ng wlan0 lnxreq_autojoin ssid=<your APs SSID> authtype=opensystem
     ifconfig wlan0 <yourIP> netmask <yourNetmask> broadcast <yourBroadcast>
     route add default gw <yourGateway>

   Also, don't forget to set up your resolv.conf to point at your DNS server.

B) Alternatively, you can use the rc.wlan script, which ties into the 
   /etc/wlan/* configuration files mentioned above.

   We currently don't create the softlink from the runlevel directories to
   the wlan startup script due to differences in distributions, but the
   scripts are redhat-aware, and can be extended to hook into other tools
   easily.  (patches welcome!)  Just make sure it is brought up early in 
   the process, namely, before the the network interfaces are brought up. 

C) Add an alias for wlan0 in /etc/modules.conf.  For example, a usb 
   interface on wlan0 would be set up as:

   alias wlan0 prism2_usb

   Substitute prism2_plx or prism2_pci as appropriate.

------------------------------
FOR USB USERS:

A) Make sure your kernel usb support is running
B) Plug in the Prism2.x USB device
C) Run 'modprobe prism2_usb prism2_doreset=1' to load the driver into memory.
D) Run 'wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable' to initialize the
   driver+MAC functions.
E) Run 'wlanctl-ng wlan0 lnxreq_autojoin ssid=<your ssid> authtype=opensystem'
   to enable the MAC in Infrastructure Station mode.
F) Run 'ifconfig wlan0 <your IP address>'

Or, you can use the provided hotplug scripts, if your distribution has
hotplug support.  :) 

IMPORTANT: Due to an issue with some versions of the Prism USB firmware,
the driver usually needs to perform a port reset.  

Some combinations of usb low-level drivers, kernel releases, and
hardware don't like this, and usually end up generating a kernel OOPS.
newer kernels are much better in this regard.  In particular, Intel usb
controllers are the most trouble-prone.

The OOPS is due to bugs in the linux USB core, and newer kernels
(2.4.19 and later) behave much better in this regard.

However, the good news is that primary firmware 1.1.2 seems to resolve
the need for the port reset to begin with.  Contact your vendor to
request this update.

Also, using the 'Alt. UHCI' controller driver (uhci.o) is broken with 
kernels older than 2.4.22 due to a bug in the controller driver.

---

### Post by bruzer on 2007-06-28
OK, so I looked in my Synaptic Manager and Linux-wlan-ng is infact installed, but my computer still isn't recognizing my wireless.

What are my options/What's next?

---

### Post by Seisen on 2007-06-28
What is the name of the wireless card?

---

### Post by bruzer on 2007-06-29
Don't know. Here is what I can tell you just by reading the other posts. I hope it helps.

Thanks for your time!

bruzer@Hunk-O-Junk:~$ Ispci
bash: Ispci: command not found
bruzer@Hunk-O-Junk:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P/KN266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
bruzer@Hunk-O-Junk:~$ lspci -n
00:00.0 0600: 1106:3156
00:01.0 0604: 1106:b091
00:0a.0 0607: 1217:6972
00:10.0 0c03: 1106:3038 (rev 80)
00:10.1 0c03: 1106:3038 (rev 80)
00:10.2 0c03: 1106:3038 (rev 80)
00:10.3 0c03: 1106:3104 (rev 82)
00:11.0 0601: 1106:3177
00:11.1 0101: 1106:0571 (rev 06)
00:11.5 0401: 1106:3059 (rev 50)
00:11.6 0780: 1106:3068 (rev 80)
00:12.0 0200: 1106:3065 (rev 74)
01:00.0 0300: 5333:8d04
bruzer@Hunk-O-Junk:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:12:66:e1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.2 ip=192.168.1.44 latency=32 maxlatency=8 mingnt=3 multicast=yes
       resources: ioport:d800-d8ff iomemory:dffffe00-dffffeff irq:11
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by az on 2007-06-29
You need to enter your WEP key differently.  

EDIT:  The smileys make the following look terrible on the forum.  Take a look at the original wiki page.

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

Quote:
[I]Whether you use network-admin or manually edit /etc/network/interfaces, make sure you enter the WEP key as xx:xx:xx:xx:xx, that is, with colons between every two hex digits. Note that using network-admin to enter the WEP key does not work out-of-the-box in Ubuntu 6.06. See  bug #37451 for a patch for this. Without the patch, you'll have to add these lines to your wlan0 configuration in /etc/network/interfaces: 

wireless_mode managed
wireless_enc on
wlan_ng_key0 xx:xx:xx:xx:xx
Then unplug your device and reinsert again, and the network should come up by itself. 

[/I]

---

### Post by bruzer on 2007-06-29
I don't know how or where to input this information. And is the Key0 my security key?

---

### Post by bruzer on 2007-06-29
I tried entering /etc/network/interfaces and this is what I get.

bruzer@Hunk-O-Junk:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied

So, looking at other posts, I tried installing build essentials and I get this:

bruzer@Hunk-O-Junk:~$  sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 667kB/7906kB of archives. After unpacking 33.0MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-libc-dev 2.6.20-16.29
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.29_i386.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.29_i386.deb:) Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


What am I doing wrong???

I went into the actual file and found this;

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


Can I just edit it here???

---

### Post by az on 2007-06-29
sudo nano /etc/network/interfaces

---

### Post by bruzer on 2007-06-30
[B]I just want to start by thanking you for your time AZ.

Now, I feel a little like a tool, but I don't know what to do now that I got to this page.[/B]

"sudo nano /etc/network/interfaces"

**Do I copy and paste this info in?**
wireless_mode managed
wireless_enc on
wlan_ng_key0 xxxxxx
[B]
Where do I put this patch?[/B]
--- linux-wlan-ng-pre-up.orig	2006-02-04 15:58:51.000000000 +0100
+++ linux-wlan-ng-pre-up	2006-03-30 23:23:46.000000000 +0200
@@ -35,6 +35,17 @@
 }
 trap cleanup 0
 
+# Translate some variable names from wireless-tools to make
+# linux-wlan-ng more compatible with e.g. gnome-system-tools
+# The new variables are only set if previously unset
+: ${IF_WLAN_NG_KEY0:=$IF_WIRELESS_KEY}
+if [ -n "$IF_WIRELESS_KEY" ]
+then
+	: ${IF_WIRELESS_ENC:=on}
+	: ${IF_WIRELESS_MODE:=managed}
+fi
+# End of translating hacks
+
 if [ -z "$IF_WIRELESS_MODE" ]; then
 	IF_WIRELESS_MODE="ad_hoc"
 fi 

**And finally, where do I get my WEP key?**

---

### Post by bruzer on 2007-07-01
bump

---

### Post by az on 2007-07-01
> **bruzer said:**
> [B]I just want to start by thanking you for your time AZ.

wireless_mode managed
wireless_enc on
wlan_ng_key0 xxxxxx


**And finally, where do I get my WEP key?**

The xxxxxx is your WEP key.  You enter it with colons in between each two digits.  Your WEP key is what you told your wireless access point to use for encryption.

---

### Post by bruzer on 2007-07-01
**[SIZE="2"][FONT="Comic Sans MS"][SIZE="3"]AZ! You are the man right now. I have the WEP Key![/SIZE][/FONT][/SIZE]**

[B]
[SIZE="2"]Do I copy and paste this info into my network interfaces window, do I write a new page and save, or is there another option?[/B][/SIZE]
wireless_mode managed
wireless_enc on
wlan_ng_key0 XX:39:4C:53:XX
[B][SIZE="2"]
Where do I put this patch?[/SIZE][/B]
--- linux-wlan-ng-pre-up.orig 2006-02-04 15:58:51.000000000 +0100
+++ linux-wlan-ng-pre-up 2006-03-30 23:23:46.000000000 +0200
@@ -35,6 +35,17 @@
}
trap cleanup 0

+# Translate some variable names from wireless-tools to make
+# linux-wlan-ng more compatible with e.g. gnome-system-tools
+# The new variables are only set if previously unset
+: ${IF_WLAN_NG_KEY0:=$IF_WIRELESS_KEY}
+if [ -n "$IF_WIRELESS_KEY" ]
+then
+ : ${IF_WIRELESS_ENC:=on}
+ : ${IF_WIRELESS_MODE:=managed}
+fi
+# End of translating hacks
+
if [ -z "$IF_WIRELESS_MODE" ]; then
IF_WIRELESS_MODE="ad_hoc"
fi

---

### Post by bruzer on 2007-07-01
Can someone walk me through installing prism2_usb.ko and p80211.ko patches. I can't get the authorization to replace the files.

---

### Post by bruzer on 2007-07-01
bump

---

### Post by az on 2007-07-01
forget about the patch.  As for that /etc/network/interfaces,

You paste that into the stanza:

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless_enc on
wlan_ng_key0 XX:39:4C:53:XX

---

### Post by bruzer on 2007-07-01
So this is how it should read:



auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless_mode managed
wireless_enc on
wlan_ng_key0 35:39:4C:53:39


GREAT!!! I'm sorry that was so painful, but I hope it helps some other Ubuntu rookie.

---

### Post by bruzer on 2007-07-01
**AZ!!! If I was single,... and gay,... and a whole slew of other craziness, I would kiss you right now. I'm wireless people!**

Thanks,
Ronnie Bruzer[FONT="Georgia"][SIZE="5"][/SIZE][/FONT]

---

