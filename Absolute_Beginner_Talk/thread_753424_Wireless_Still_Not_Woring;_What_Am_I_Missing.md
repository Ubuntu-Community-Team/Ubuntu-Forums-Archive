---
title: "Wireless Still Not Woring; What Am I Missing?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by nicolasqueen on 2008-04-12
Well, after getting help earlier to figure out how to use the "make" command I have installed madwifi, or at least I think I have. Here is my entire terminal window of my attempt. As you can see at the end, I still have no wireless but I have no errors that I can see. Can anyone help a newbie?

```
nickqueen@nickqueen-laptop:~$ cd Desktop
nickqueen@nickqueen-laptop:~/Desktop$ cd madwifi
nickqueen@nickqueen-laptop:~/Desktop/madwifi$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/nickqueen/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/nickqueen/Desktop/madwifi/ath/if_ath.o
  CC [M]  /home/nickqueen/Desktop/madwifi/ath/if_ath_pci.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath/ath_pci.o
  CC [M]  /home/nickqueen/Desktop/madwifi/ath_hal/ah_os.o
  HOSTCC  /home/nickqueen/Desktop/madwifi/ath_hal/uudecode
  UUDECODE /home/nickqueen/Desktop/madwifi/ath_hal/x86_64-elf.hal.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_hal/ath_hal.o
  CC [M]  /home/nickqueen/Desktop/madwifi/ath_rate/amrr/amrr.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/nickqueen/Desktop/madwifi/ath_rate/minstrel/minstrel.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/nickqueen/Desktop/madwifi/ath_rate/onoe/onoe.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/nickqueen/Desktop/madwifi/ath_rate/sample/sample.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/if_media.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_beacon.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_crypto.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_crypto_none.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_input.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_node.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_output.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_power.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_proto.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_scan.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_wireless.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_linux.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_monitor.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_rate.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_acl.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_scan_ap.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_scan_sta.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/nickqueen/Desktop/madwifi/net80211/ieee80211_xauth.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_wep.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_tkip.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_ccmp.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_acl.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_xauth.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_scan_sta.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/nickqueen/Desktop/madwifi/ath/ath_pci.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath/ath_pci.ko
  CC      /home/nickqueen/Desktop/madwifi/ath_hal/ath_hal.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_hal/ath_hal.ko
  CC      /home/nickqueen/Desktop/madwifi/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/nickqueen/Desktop/madwifi/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/nickqueen/Desktop/madwifi/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/nickqueen/Desktop/madwifi/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/ath_rate/sample/ath_rate_sample.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan_acl.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_acl.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan_ccmp.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_ccmp.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_scan_ap.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_scan_sta.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan_tkip.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_tkip.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan_wep.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_wep.ko
  CC      /home/nickqueen/Desktop/madwifi/net80211/wlan_xauth.mod.o
  LD [M]  /home/nickqueen/Desktop/madwifi/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/nickqueen/Desktop/madwifi/tools'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I..  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I..  wlanconfig.c
gcc -o ath_info -g -O2 -Wall ath_info.c
make[1]: Leaving directory `/home/nickqueen/Desktop/madwifi/tools'
nickqueen@nickqueen-laptop:~/Desktop/madwifi$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.22-14-generic 

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/nickqueen/Desktop/madwifi/ath'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_pci.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/nickqueen/Desktop/madwifi/ath'
make[1]: Entering directory `/home/nickqueen/Desktop/madwifi/ath_hal'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_hal.ko //lib/modules/2.6.22-14-generic/net
make[1]: Leaving directory `/home/nickqueen/Desktop/madwifi/ath_hal'
make[1]: Entering directory `/home/nickqueen/Desktop/madwifi/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
                make -C $i install || exit 1; \
        done
make[2]: Entering directory `/home/nickqueen/Desktop/madwifi/ath_rate/amrr'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_amrr.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/nickqueen/Desktop/madwifi/ath_rate/amrr'
make[2]: Entering directory `/home/nickqueen/Desktop/madwifi/ath_rate/onoe'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_onoe.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/nickqueen/Desktop/madwifi/ath_rate/onoe'
make[2]: Entering directory `/home/nickqueen/Desktop/madwifi/ath_rate/sample'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_rate_sample.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/nickqueen/Desktop/madwifi/ath_rate/sample'
make[2]: Entering directory `/home/nickqueen/Desktop/madwifi/ath_rate/minstrel'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
cp ath_rate_minstrel.ko //lib/modules/2.6.22-14-generic/net
make[2]: Leaving directory `/home/nickqueen/Desktop/madwifi/ath_rate/minstrel'
make[1]: Leaving directory `/home/nickqueen/Desktop/madwifi/ath_rate'
make[1]: Entering directory `/home/nickqueen/Desktop/madwifi/net80211'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
                f=`basename $i .o`; \
                install $f.ko //lib/modules/2.6.22-14-generic/net; \
        done
make[1]: Leaving directory `/home/nickqueen/Desktop/madwifi/net80211'
(export KMODPATH=/lib/modules/2.6.22-14-generic/net; /sbin/depmod -ae 2.6.22-14-generic)
make -C ./tools  install || exit 1
make[1]: Entering directory `/home/nickqueen/Desktop/madwifi/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info; do \
                install $i /usr/local/bin/$i; \
                strip /usr/local/bin/$i; \
        done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/home/nickqueen/Desktop/madwifi/tools'
nickqueen@nickqueen-laptop:~/Desktop/madwifi$ modprobe ath_pci
nickqueen@nickqueen-laptop:~/Desktop/madwifi$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

nickqueen@nickqueen-laptop:~/Desktop/madwifi$ 


```

---

### Post by Inxsible on 2008-04-12
What wireless card do you have?

Could you post the output of the following command```
lspci
```

---

### Post by nicolasqueen on 2008-04-12
Here goes:

```
nickqueen@nickqueen-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
0e:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
nickqueen@nickqueen-laptop:~$ 
```

---

### Post by brian_p on 2008-04-12
> **nicolasqueen said:**
> ```

0e:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)
 
```

I imagine you compiled the module from scratch because you are aware support for this chipset is not available? Make seems to have gone ok and modprobe doesn't complain so the module has been inserted. I'd expect interface ath0 to be in iwconfig's output.

```
sudo lsmod | grep ath
```

for the modules loaded.

```
rmmod <module_name>
```

to remove all of them. And try again.

I'm not really hopeful that will get you anywhere. The card is inserted and seated correctly?

---

### Post by nicolasqueen on 2008-04-12
I forgot to put my wireless chipset. Atheros AR5008X. Is this one not supported?

---

### Post by anewguy on 2008-04-12
There are posts about this same card, same rev number, in the forums for a variety of hardware - one if which is a Thinkpad laptop.  Madwifi is mentioned there, but their ultimate solution was to go back to ndiswrapper and the Windows drivers.  SO.......have you tried ndiswrapper?  What were the results?  Is ndiswrapper still installed on your system?

Provide those answers and I think we can move you along.  :)

---

### Post by vgrisham on 2008-04-12
And you might try the [Linuxant DriverLoader]("http://www.linuxant.com/driverloader/"). It's not free, but I bought their driver loader for my obstinate conexant modem and it worked very well.

---

### Post by moore.bryan on 2008-04-12
stick with madwifi... it's already in the "linux-restricted-modules" package; try installing that and then rebooting. i'd also suggest dropping network-manager for [wicd]("http://wicd.sourceforge.net/").
```
sudo aptitude install linux-restricted-modules
```

---

### Post by anewguy on 2008-04-12
The only reason ndiswrapper was mentioned is that there are posts on this forum and in the community forum concerning this chipset and the madwifi drivers, and with suggestions to use ndiswrapper with the Windows drivers instead.  Some of these posts revolve around not being able to get the wireless working with madwifi.  So, IF you find you are still unable to get it working with madwifi, I would strongly suggest ndiswrapper.  Some seem to think it is the "cheap" way out because it isn't using open-source drivers, but more to the point, if it gets you working after the other ways fail, what's so bad about that?

Good luck!  :)

---

### Post by nicolasqueen on 2008-04-13
> **anewguy said:**
> The only reason ndiswrapper was mentioned is that there are posts on this forum and in the community forum concerning this chipset and the madwifi drivers, and with suggestions to use ndiswrapper with the Windows drivers instead.  Some of these posts revolve around not being able to get the wireless working with madwifi.  So, IF you find you are still unable to get it working with madwifi, I would strongly suggest ndiswrapper.  Some seem to think it is the "cheap" way out because it isn't using open-source drivers, but more to the point, if it gets you working after the other ways fail, what's so bad about that?

Good luck!  :)

I've been looking at this and I'm a little confused. Understand this is all new to me and while I do have some backing in DOS and even very limited unix experience, this is all new to me.

---

### Post by anewguy on 2008-04-13
Well, with a Windows PC, the drivers for such things as your video card, your sound card and your wireless card were either automatically installed by Windows, installed by the OEM, or they came on a disk (possibly a download) that you installed yourself.  These things work a little more smoothly in Windows because all of the pieces are sort of forced to play well together due to everyone wanting to make a profit.

Then you move to the Linux world, which is based in the idea of freely distributable software, and things change.  Manufacturers aren't big on providing Linux drivers mainly because of the "free" aspect as well a smaller installed base.  So, you have to do somethings yourself, but most aren't difficult - in fact, most of the time the most difficult part is searching for instructions for your problem.

In your case, madwifi sort of "gives" you drivers for your wireless card.  It is now included in what are called the "restricted drivers" for Ubuntu.  They are called restricted because they are 3rd party software not controlled by the distribution of Linux you use.  As an example, if you have installed Ubuntu 7.10, and in a few weeks upgrade to Ubuntu 8, you may or may not have to reinstall the drivers again.

In your case, you should try enabling the restricted drivers first (you may have to install some of it via Synaptic package manager), since madwifi is included.  However, if you continue to have problems and just can't make them work, there is another approach called ndiswrapper.

Ndiswrapper allows you to use the Windows (I believe at this time non-Vista) drivers for your networking device, in this case your wireless adapter, in Linux.  You can check to see if you have ndiswrapper installed just by putting the following in a terminal window:

ndiswrapper -l <-- that's a lower case "L", for "list"

If no error is returned then it is installed.  Otherwise you can install it from the Synaptic package manager.

Once installed, you follow a pretty simple procedure:

copy your windows drivers to a path on your Linux hard drive

in a terminal, change your default directory to that path, the run ndiswrapper to install the driver.  There are a couple of other steps involved, and please note these are not "just do this" instructions here - you can find those in the many, many, many posts on wireless adapters on this forum.  You can also post back if you decide you want to try this and we can walk you through it.

Good Luck!  :)

---

### Post by moore.bryan on 2008-04-13
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
excellent explanation and suggestions... couldn't have put it better.

---

