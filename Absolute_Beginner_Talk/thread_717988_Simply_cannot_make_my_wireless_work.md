---
title: "Simply cannot make my wireless work"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by TBomBM3789 on 2008-03-07
I've tried everything. I have built in wireless on my laptop by ACER and supported by atheros. When i used windows XP and Vista, they used atheros drivers available for download from the acer site. 

I first tried compiling mad wifi..... which installed okay but didn't work... what i mean is that when I go to the network menu, all that shows is wired connection and modem.... no wireless.


then I tried using NDIS wrapper to use the windows driver that worked with windows...... again installed okay..... didn't show up on the network menu.

i'd really appreciate anyone who can help.

---

### Post by Vadi on 2008-03-07
What does **iwconfig** in the terminal say?

---

### Post by TBomBM3789 on 2008-03-07
lo        no wireless extensions.

eth0      no wireless extensions.



hmm....

---

### Post by Vadi on 2008-03-07
Alright.

Do you know the exact model number of the card? Also, please post the putput of this command:

```
sudo lshw -C network
```

(in case you didn't know, you can select the stuff, right-click, and copy)

---

### Post by TBomBM3789 on 2008-03-07
Acer InviLink 54Mbps Wi-Fi IEEE 802.11b/g is all i could find. I have an acer aspire 5100 - 5455 laptop

that command brings up this:


  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:27:d8:9a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=10.5.8.105 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

---

### Post by TBomBM3789 on 2008-03-07
also brought up this (thought I copied all of it sorry)

  description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:27:d8:9a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=10.5.8.105 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

---

### Post by Vadi on 2008-03-07
Give this a try:

[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

?

---

### Post by ugm6hr on 2008-03-07
> **TBomBM3789 said:**
> 
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  

Notice there is no driver listed in your output for wifi (unlike wired).

Read this first: [http://ubuntuforums.org/showthread.p...05#post4259805](http://ubuntuforums.org/showthread.p...05#post4259805)

Then check in Windows what your card is identified as (i.e. is it AR5007EG?)

If so, it can be made to work (with ndiswrapper), but only after installation.

---

### Post by TBomBM3789 on 2008-03-07
not really how to try that first step mentioned 

~$ linux-restricted-modules-$(uname -r)
bash: linux-restricted-modules-2.6.22-14-generic: command not found

:~$ install linux-restricted-modules-$(uname -r)
install: missing destination file operand after `linux-restricted-modules-2.6.22-14-generic'
Try `install --help' for more information.

or was it to help me install it manually?

---

### Post by scottro on 2008-03-07
I would almost guarantee that you have the AR5007EG. 

There's a thread somewhere on the forums with a step by step about how to get it working using a patched MadWifi snapshot.  

Sigh, I can't find it but I summarized some of it for Fedora at 
[http://home.nyc.rr.com/computertaijutsu/rhwireless.html](http://home.nyc.rr.com/computertaijutsu/rhwireless.html)

I should update it with an Ubuntu section, but I never had trouble finding the link before.  

I'm assuming you don't have any ndiswrapper installed at this point, especially since we're not even positive I'm right about the card--if I am, then lspci will report it as 5006 but it's not.  If it's an Acer, and there's a sticker on the bottom, saying that it's AR5BXB63 then the 5007 is what you have. 
Note these instructions are for 32 bit systems and they taken from another post on these forums--if I could find that post, I'd direct you there.

sudo apt-get install build-essential

Blacklist the ath5k module--this might not be necessary, but won't hurt anything

rmmod ath5k

Open /etc/modprobe.d/blacklist and add this line to the end

blacklist ath5k

Download the patched madwifi snapshot.

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

Decompress and untar it, then cd into it.  

tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
sudo make
sudo make install
sudo modprobe ath_pci

Now, see if it worked

iwconfig

See if you now have an ath0

If so, you're probably in good shape and can doublecheck with 

iwlist ath0 scan

That should show you any networks around.  You can probably then join your preferred network using NetworkManager. 

Sigh, if the person who first put up the instructions sees this, please accept my sincere thanks by the way--your post is what enabled me to get it working in Fedora. 

Note that each time your kernel is upgraded, you'll have to reinstall it.
cd  madwifi-ng-r2756+ar5007
make uninstall
make clean
make install 
modprobe ath_pci

Hopefully, eventually Atheros will release enough information so that it will become part of the MadWifi package and you won't have to do that each time you upgrade the kernel.

---

### Post by TBomBM3789 on 2008-03-07
yup i do have the 5007..... i'm going to try your instructions... hope they work

---

### Post by TBomBM3789 on 2008-03-08
ERROR: Module ath5k does not exist in /proc/modules

also how do i edit files inside the file system? every time i try to save changes it says I don't have the privilage to do so. I'm the only user on this system.

---

### Post by scottro on 2008-03-08
Ok, I shouldn't write these things when sleep deprived, though I'm still sleep deprived.

If there's no ath5k, that's fine.  I believe I had it on one of my installs, but that might be the alpha.  (Or, I could be thinking of Fedora, where that module does exist and has to be blacklisted.)

That's fine, just skip that step. 
As for saving changes, I think you would have to use whatever editor you use, for example, gedit, with sudo.  For example, sudo gedit /etc/modprobe.d/blacklist.

However, if it says that module doesn't exist, I think it can be ignored and you can just go to the next stop.  

I've been extremely busy this week, meaning not enough sleep--so post again if something else isn't clear.

---

### Post by ugm6hr on 2008-03-08
> **scottro said:**
> As for saving changes, I think you would have to use whatever editor you use, for example, gedit, with sudo.  For example, sudo gedit /etc/modprobe.d/blacklist.


Agreed, although gksudo is strictly correct:

```
gksudo gedit /*full_path_to_file_to_be_edited*
```

If you prefer to browse to the file and double-click to edit:

```
gksudo nautilus
```

---

### Post by TBomBM3789 on 2008-03-08
hmmmm its still not working. did i do anything wrong here?

tristan@tristans-laptop:~$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--04:14:23--  [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz.3'
Resolving snapshots.madwifi.org... 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,003,237 (3.8M) [application/x-gzip]

100%[====================================>] 4,003,237    173.00K/s    ETA 00:00

04:14:44 (196.58 KB/s) - `madwifi-ng-r2756+ar5007.tar.gz.3' saved [4003237/4003237]

tristan@tristans-laptop:~$ tar zxvf madwifi-ng-r2756+ar5007.tar.gz
madwifi-ng-r2756+ar5007/
madwifi-ng-r2756+ar5007/THANKS
madwifi-ng-r2756+ar5007/scripts/
madwifi-ng-r2756+ar5007/scripts/madwifi-unload
madwifi-ng-r2756+ar5007/scripts/if_ath_hal_generator.pl
madwifi-ng-r2756+ar5007/scripts/get_arch.mk
madwifi-ng-r2756+ar5007/scripts/find-madwifi-modules.sh
madwifi-ng-r2756+ar5007/scripts/make-release.bash
madwifi-ng-r2756+ar5007/scripts/madwifi-indent
madwifi-ng-r2756+ar5007/regression/
madwifi-ng-r2756+ar5007/regression/ccmp/
madwifi-ng-r2756+ar5007/regression/ccmp/test_ccmp.c
madwifi-ng-r2756+ar5007/regression/tkip/
madwifi-ng-r2756+ar5007/regression/tkip/test_tkip.c
madwifi-ng-r2756+ar5007/regression/wep/
madwifi-ng-r2756+ar5007/regression/wep/test_wep.c
madwifi-ng-r2756+ar5007/BuildCaps.inc
madwifi-ng-r2756+ar5007/ath/
madwifi-ng-r2756+ar5007/ath/if_athvar.h
madwifi-ng-r2756+ar5007/ath/if_ath_hal_macros.h
madwifi-ng-r2756+ar5007/ath/if_ath_hal_wrappers.h
madwifi-ng-r2756+ar5007/ath/if_ath_pci.c
madwifi-ng-r2756+ar5007/ath/Makefile.kernel
madwifi-ng-r2756+ar5007/ath/if_athioctl.h
madwifi-ng-r2756+ar5007/ath/if_ath_pci.h
madwifi-ng-r2756+ar5007/ath/if_ath_hal.h
madwifi-ng-r2756+ar5007/ath/version.h
madwifi-ng-r2756+ar5007/ath/if_ath_ahb.c
madwifi-ng-r2756+ar5007/ath/Makefile
madwifi-ng-r2756+ar5007/ath/if_ath.c
madwifi-ng-r2756+ar5007/ath/if_ath_ahb.h
madwifi-ng-r2756+ar5007/tools/
madwifi-ng-r2756+ar5007/tools/man/
madwifi-ng-r2756+ar5007/tools/man/wlanconfig.8
madwifi-ng-r2756+ar5007/tools/man/athkey.8
madwifi-ng-r2756+ar5007/tools/man/athctrl.8
madwifi-ng-r2756+ar5007/tools/man/80211debug.8
madwifi-ng-r2756+ar5007/tools/man/athdebug.8
madwifi-ng-r2756+ar5007/tools/man/athchans.8
madwifi-ng-r2756+ar5007/tools/man/athstats.8
madwifi-ng-r2756+ar5007/tools/man/ath_info.8
madwifi-ng-r2756+ar5007/tools/man/80211stats.8
madwifi-ng-r2756+ar5007/tools/athctrl.c
madwifi-ng-r2756+ar5007/tools/athdebug.c
madwifi-ng-r2756+ar5007/tools/80211stats.c
madwifi-ng-r2756+ar5007/tools/wlanconfig.c
madwifi-ng-r2756+ar5007/tools/athstats.c
madwifi-ng-r2756+ar5007/tools/ath_info.c
madwifi-ng-r2756+ar5007/tools/wireless_copy.h
madwifi-ng-r2756+ar5007/tools/athchans.c
madwifi-ng-r2756+ar5007/tools/athkey.c
madwifi-ng-r2756+ar5007/tools/Makefile
madwifi-ng-r2756+ar5007/tools/80211debug.c
madwifi-ng-r2756+ar5007/ath_hal/
madwifi-ng-r2756+ar5007/ath_hal/uudecode.c
madwifi-ng-r2756+ar5007/ath_hal/ah_osdep.h
madwifi-ng-r2756+ar5007/ath_hal/ah_os.h
madwifi-ng-r2756+ar5007/ath_hal/Makefile.kernel
madwifi-ng-r2756+ar5007/ath_hal/ah_target.inc
madwifi-ng-r2756+ar5007/ath_hal/opt_ah.h
madwifi-ng-r2756+ar5007/ath_hal/ah_os.c
madwifi-ng-r2756+ar5007/ath_hal/Makefile
madwifi-ng-r2756+ar5007/patch-kernel/
madwifi-ng-r2756+ar5007/patch-kernel/Config.in
madwifi-ng-r2756+ar5007/patch-kernel/README
madwifi-ng-r2756+ar5007/patch-kernel/Kconfig
madwifi-ng-r2756+ar5007/patch-kernel/install.sh
madwifi-ng-r2756+ar5007/patch-kernel/Configure.help.patch
madwifi-ng-r2756+ar5007/net80211/
madwifi-ng-r2756+ar5007/net80211/ieee80211_crypto.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_rate.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_var.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_linux.h
madwifi-ng-r2756+ar5007/net80211/if_media.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_crypto.c
madwifi-ng-r2756+ar5007/net80211/ieee80211.h
madwifi-ng-r2756+ar5007/net80211/if_media.c
madwifi-ng-r2756+ar5007/net80211/if_ethersubr.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_scan.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_rate.c
madwifi-ng-r2756+ar5007/net80211/if_llc.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_wireless.c
madwifi-ng-r2756+ar5007/net80211/ieee80211.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_radiotap.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_node.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_crypto_tkip.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_input.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_scan.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_output.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_crypto_ccmp.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_power.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_debug.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_monitor.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_scan_ap.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_crypto_none.c
madwifi-ng-r2756+ar5007/net80211/Makefile.kernel
madwifi-ng-r2756+ar5007/net80211/ieee80211_ioctl.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_beacon.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_linux.c
madwifi-ng-r2756+ar5007/net80211/if_athproto.h
madwifi-ng-r2756+ar5007/net80211/version.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_node.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_xauth.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_monitor.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_power.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_acl.c
madwifi-ng-r2756+ar5007/net80211/Makefile
madwifi-ng-r2756+ar5007/net80211/ieee80211_crypto_wep.c
madwifi-ng-r2756+ar5007/net80211/ieee80211_scan_sta.c
madwifi-ng-r2756+ar5007/net80211/_ieee80211.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_proto.h
madwifi-ng-r2756+ar5007/net80211/ieee80211_proto.c
madwifi-ng-r2756+ar5007/COPYRIGHT
madwifi-ng-r2756+ar5007/ath_rate/
madwifi-ng-r2756+ar5007/ath_rate/onoe/
madwifi-ng-r2756+ar5007/ath_rate/onoe/onoe.c
madwifi-ng-r2756+ar5007/ath_rate/onoe/Makefile.kernel
madwifi-ng-r2756+ar5007/ath_rate/onoe/onoe.h
madwifi-ng-r2756+ar5007/ath_rate/onoe/Makefile
madwifi-ng-r2756+ar5007/ath_rate/minstrel/
madwifi-ng-r2756+ar5007/ath_rate/minstrel/minstrel.h
madwifi-ng-r2756+ar5007/ath_rate/minstrel/minstrel.c
madwifi-ng-r2756+ar5007/ath_rate/minstrel/minstrel.txt
madwifi-ng-r2756+ar5007/ath_rate/minstrel/Makefile.kernel
madwifi-ng-r2756+ar5007/ath_rate/minstrel/Makefile
madwifi-ng-r2756+ar5007/ath_rate/sample/
madwifi-ng-r2756+ar5007/ath_rate/sample/sample.c
madwifi-ng-r2756+ar5007/ath_rate/sample/sample.h
madwifi-ng-r2756+ar5007/ath_rate/sample/Makefile.kernel
madwifi-ng-r2756+ar5007/ath_rate/sample/Makefile
madwifi-ng-r2756+ar5007/ath_rate/amrr/
madwifi-ng-r2756+ar5007/ath_rate/amrr/amrr.c
madwifi-ng-r2756+ar5007/ath_rate/amrr/amrr.h
madwifi-ng-r2756+ar5007/ath_rate/amrr/Makefile.kernel
madwifi-ng-r2756+ar5007/ath_rate/amrr/Makefile
madwifi-ng-r2756+ar5007/ath_rate/Makefile
madwifi-ng-r2756+ar5007/include/
madwifi-ng-r2756+ar5007/include/compat.h
madwifi-ng-r2756+ar5007/include/sys/
madwifi-ng-r2756+ar5007/include/sys/queue.h
madwifi-ng-r2756+ar5007/Makefile.inc
madwifi-ng-r2756+ar5007/kernelversion.c
madwifi-ng-r2756+ar5007/README
madwifi-ng-r2756+ar5007/Makefile.kernel
madwifi-ng-r2756+ar5007/INSTALL
madwifi-ng-r2756+ar5007/SNAPSHOT
madwifi-ng-r2756+ar5007/contrib/
madwifi-ng-r2756+ar5007/contrib/madwifi.spec.in
madwifi-ng-r2756+ar5007/contrib/madwifi.spec
madwifi-ng-r2756+ar5007/Makefile
madwifi-ng-r2756+ar5007/hal/
madwifi-ng-r2756+ar5007/hal/ah_devid.h
madwifi-ng-r2756+ar5007/hal/COPYRIGHT
madwifi-ng-r2756+ar5007/hal/public/
madwifi-ng-r2756+ar5007/hal/public/ap30.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/i386-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/ap30.inc
madwifi-ng-r2756+ar5007/hal/public/i386-elf.inc
madwifi-ng-r2756+ar5007/hal/public/mips-le-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/ap51.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/sparc-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/xscale-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/xscale-le-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/alpha-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/wackelf.c
madwifi-ng-r2756+ar5007/hal/public/ap43.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/sparc64-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/armv4-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/ap30.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/alpha-elf.inc
madwifi-ng-r2756+ar5007/hal/public/ap61.inc
madwifi-ng-r2756+ar5007/hal/public/mipsisa32-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/powerpc-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/mipsisa32-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/sparc64-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/mips1-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/sh4-le-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/arm9-le-thumb-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/mips1-le-elf.inc
madwifi-ng-r2756+ar5007/hal/public/powerpc-be-eabi.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/powerpc-be-eabi.inc
madwifi-ng-r2756+ar5007/hal/public/mips-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/powerpc-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/powerpc-be-eabi.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/mips1-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/mips1-le-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/sh4-le-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/powerpc-le-eabi.inc
madwifi-ng-r2756+ar5007/hal/public/xscale-le-elf.inc
madwifi-ng-r2756+ar5007/hal/public/armv4-le-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/powerpc-le-eabi.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/x86_64-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/mipsisa32-le-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/sh4-le-elf.inc
madwifi-ng-r2756+ar5007/hal/public/arm9-le-thumb-elf.inc
madwifi-ng-r2756+ar5007/hal/public/powerpc-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/mips1-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/alpha-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/arm9-le-thumb-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/mips-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/mips-le-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/ap43.inc
madwifi-ng-r2756+ar5007/hal/public/mips-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/ap51.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/mipsisa32-le-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/ap61.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/armv4-le-elf.inc
madwifi-ng-r2756+ar5007/hal/public/armv4-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/i386-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/armv4-le-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/mips1-le-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/x86_64-elf.inc
madwifi-ng-r2756+ar5007/hal/public/mipsisa32-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/ap51.inc
madwifi-ng-r2756+ar5007/hal/public/sparc-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/armv4-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/mips-le-elf.inc
madwifi-ng-r2756+ar5007/hal/public/xscale-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/mipsisa32-le-elf.inc
madwifi-ng-r2756+ar5007/hal/public/sparc-be-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/powerpc-le-eabi.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/xscale-be-elf.inc
madwifi-ng-r2756+ar5007/hal/public/ap61.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/x86_64-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/public/ap43.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/sparc64-be-elf.hal.o.uu
madwifi-ng-r2756+ar5007/hal/public/xscale-le-elf.opt_ah.h
madwifi-ng-r2756+ar5007/hal/ah_soc.h
madwifi-ng-r2756+ar5007/hal/README
madwifi-ng-r2756+ar5007/hal/version.h
madwifi-ng-r2756+ar5007/hal/ah.h
madwifi-ng-r2756+ar5007/hal/ah_desc.h
madwifi-ng-r2756+ar5007/release.h
tristan@tristans-laptop:~$ cd madwifi-ng-r2756+ar5007
tristan@tristans-laptop:~/madwifi-ng-r2756+ar5007$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tristan/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/tools'
tristan@tristans-laptop:~/madwifi-ng-r2756+ar5007$ sudo make install
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tristan/madwifi-ng-r2756+ar5007 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 14 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
sh scripts/find-madwifi-modules.sh -r 2.6.22-14-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/ath'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_pci.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/ath'
make[1]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_hal'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_hal.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_hal'
make[1]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
                make -C $i install || exit 1; \
        done
make[2]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/amrr'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_amrr.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/amrr'
make[2]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/onoe'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_onoe.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/onoe'
make[2]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/sample'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_sample.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/sample'
make[2]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/minstrel'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_minstrel.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate/minstrel'
make[1]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/ath_rate'
make[1]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/net80211'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
                f=`basename $i .o`; \
                install $f.ko //lib/modules/2.6.22-14-generic/net; \
        done
make[1]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/net80211'
(export KMODPATH=/lib/modules/2.6.22-14-generic/net; /sbin/depmod -ae 2.6.22-14-generic)
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/tools'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/tools'
make -C ./tools  install || exit 1
make[1]: Entering directory `/home/tristan/madwifi-ng-r2756+ar5007/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info; do \
                install $i /usr/local/bin/$i; \
                strip /usr/local/bin/$i; \
        done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
install ../scripts/madwifi-unload /usr/local/bin/madwifi-unload
make[1]: Leaving directory `/home/tristan/madwifi-ng-r2756+ar5007/tools'
tristan@tristans-laptop:~/madwifi-ng-r2756+ar5007$ sudo modprobe ath_pci
tristan@tristans-laptop:~/madwifi-ng-r2756+ar5007$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tristan@tristans-laptop:~/madwifi-ng-r2756+ar5007$ iwlist ath0 scan
ath0      Interface doesn't support scanning.

tristan@tristans-laptop:~/madwifi-ng-r2756+ar5007$

---

### Post by TBomBM3789 on 2008-03-08
when you type in sudo modprobe ath_pci, it doesnt show up anything right?

because when I typed it, i got this 

tristan@tristans-laptop:~$ sudo modprobe ath_pci
tristan@tristans-laptop:~$

---

### Post by scottro on 2008-03-08
Correct--it only shows something if there's a problem.  

You can check afterwards with 

lsmod |grep ath 

and it should show ath_pci and a few other things.

---

### Post by TBomBM3789 on 2008-03-08
yes it does

 lsmod |grep ath
ath_pci                98336  0 
wlan                  206660  1 ath_pci
ath_hal               192720  1 ath_pci


yet im still not getting wireless...... wonder whats going wrong.

---

### Post by scottro on 2008-03-08
Ok, fear not.  We're making progress.  That's what you wanted to see.

I'm going out for a bit, so I'll try to anticipate what might happen next--hrrm, bad move, as the saying goes, How do you make God laugh?  Tell him your plans.   But anyway...

Please try doing 

iwconfig

See if you get any response for either wlan0 or ath0. 

Also, try iwlist scan

and see if you get any indication that there are wireless networks in your area. 

If the answer to the second one, especially, is positive, then we're almost there.  If not, then please try a reboot and try those two commands again. 

If the result is negative, and still negative after the reboot, please do

dmesg |grep HAL

see if there's some sort of HAL error, either error 13 or error 3.  (Or any other, but those are the most common ones.)

You can also try 
dmesg |grep ath

Now, I don't know how you usually connect to a wireless network, but if you're running Gnome (the default) and the reboot shows these networks, then there's a good chance it will then work.

---

### Post by TBomBM3789 on 2008-03-08
tristan@tristans-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tristan@tristans-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

tristan@tristans-laptop:~$ dmesg |grep HAL
[   15.296000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
tristan@tristans-laptop:~$ dmesg |grep ath
[   15.084000] ath_hal: module license 'Proprietary' taints kernel.
[   15.084000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   15.288000] ath_pci: 0.9.4.5 (0.9.3.2)
tristan@tristans-laptop:~$



yes im running GNOME

---

### Post by scottro on 2008-03-08
Ok, let's try to take this from the top.

Is ndiswrapper still installed? 
Did you remove the ndiswrapper?
Did you remove the other versions of MadWifi?

If you did remove ndiswrapper, did you first do ndiwrapper -e net5211 (or whatever driver you used) to uninstall the driver before removing ndiswrapper?

All these are important, we have to make sure other versions are uninstalled. 

So, let's start with ndiswrapper, since looking at this thread, it looks as if you installed that first. 

Did you uninstall it, and if so, did you remember to first remove the driver that ndiswrapper installed? 

If no, we have to start with that. 

Secondly, you had installed MadWifi before.  Did you uninstall it before trying this version?  If not, how did you install that, with the source code (doing something similar to what we did ) or with apt-get install?

Once you're sure both of those have removed (as well as the net5211 driver you would have installed with ndiswrapper--or the other driver for that card, net5416 or something, reboot once.  Yeah, I know it's WIndows like but let's be sure.   (If you're a little stuck on uninstalling these, post, and we'll figure it out.)

Also, please confirm--you are running 32 bit Ubuntu, correct?  You've confirmed that it actually is the AR5007EG card, either through seeing that sticker on the bottom or using Windows Device Manager. 

Also, as many instructions for both ndiswrapper and MadWifi have you blacklisting various modules, let's make sure that none of the ones we want are blacklisted.  Please do 

tail /etc/modprobe.d/blacklist 

and make sure you don't see ath_pci.

So, lets assume you were able to do all of the above without incident. 
Go back into the directory for the Madwifi+ar5007 directory and please run the following again.  (However, don't bother with this till all of the above has been taken care of.)  

Then

sudo make uninstall
sudo make clean
sudo make
sudo make install 

(you don't have to show the output unless there's an error--the output from last time seemed OK.)

Then, we try again.  I think it's worth the trouble since I've been able to, with the MadWifi snapshot, get this working on various and sundry distributions, including of course, Ubuntu, so it should really work.

modprobe ath_pci

Double check that it's there.

lsmod |grep ath

Then try the iwconfig again.  Again, if it doesn't work, do the reboot and then the dmesg |grep HAL. 

Something is off, and my guess is that something else was installed first and not uninstalled.  I know that when I was first getting this card to work, I tried a bunch of things, and I think--though I'm not positive--that forgetting to uinstall something else first was my problem. 

By the way, you deserve compliments on your patience with this.  Many people just say, Oh the heck with it, Linux doesn't work right.  

So hang in there, and let's see if we can get it working.  

However, please confirm that it is the AR5007EG and that you are running 32 bit Ubuntu, not 64 bit.  :)

---

