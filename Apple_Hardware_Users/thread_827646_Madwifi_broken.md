---
title: "Madwifi broken"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by Stu09 on 2008-06-13
Feeling triumphant after getting my iSight to work after following the guide. It was only that I went to come back here and post about my success that I realised I was no longer able to connect to my wifi :(

I concluded that the wifi wasn't loading, so I tried to load it myself
```
stuart@MacBook:~$ sudo modprobe ath_pci 

FATAL: Error inserting ath_pci (/lib/modules/2.6.24-18-generic/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

This is what dmesg says
```
[  272.564122] ath_pci: disagrees about version of symbol _ath_hal_attach

[  272.564132] ath_pci: Unknown symbol _ath_hal_attach

[  272.564363] ath_pci: disagrees about version of symbol ath_hal_process_noisefloor

[  272.564367] ath_pci: Unknown symbol ath_hal_process_noisefloor

[  272.565330] ath_pci: disagrees about version of symbol ath_hal_computetxtime

[  272.565334] ath_pci: Unknown symbol ath_hal_computetxtime

[  272.565941] ath_pci: disagrees about version of symbol ath_hal_mhz2ieee

[  272.565944] ath_pci: Unknown symbol ath_hal_mhz2ieee

[  272.566335] ath_pci: Unknown symbol _ath_hal_detach

[  272.567734] ath_pci: Unknown symbol ath_hal_print_decoded_register

[  272.569075] ath_pci: disagrees about version of symbol ath_hal_init_channels

[  272.569079] ath_pci: Unknown symbol ath_hal_init_channels

[  272.569668] ath_pci: disagrees about version of symbol ath_hal_getwirelessmodes

[  272.569672] ath_pci: Unknown symbol ath_hal_getwirelessmodes

```
I set it up using the guide on the wiki and it was working happily up until I recompiled my uvcvideo to make isight work and rebooted :confused:

---

### Post by kestaz on 2008-06-13
It seems like you changed kernel version or upgraded ? It can be or not ..

Just try to recompile you madwifi drivers. go to madwifi directory:

make clean
make
make install
modprobe ath_pci

As i think maybe you upgraded ubuntu packeges(it install new kernels too) 
.. 

Maybe i am wrong.. :confused: but you can check it ..

---

### Post by Stu09 on 2008-06-13
Ok I tried the recompile. No joy, it looked good until the modprobe. It showed the same error as above.

---

### Post by Ilove2023 on 2008-06-13
I think you have to unload the module first... There is a script in madwifi/script to do that (sudo ./madwifi-unload, i think)

---

### Post by Stu09 on 2008-06-13
Beautiful! worked like a charm. 
Thanks guys :mrgreen:

---

### Post by flavio newbie on 2008-06-13
excuse me but my script doesnt run (madwifi unload)

root@flavio-laptop:/home/flavio# cd Desktop/
root@flavio-laptop:/home/flavio/Desktop# cd madwifi-0.9.4/
root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4# make clean
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
		make -C $i clean; \
	done
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath'
rm -f *~ *.o *.ko *.mod.c .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath'
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_hal'
rm -f *~ *.o *.ko *.mod.c uudecode .*.cmd
rm -f .depend .version .*.o.flags .*.o.d
rm -rf .tmp_versions
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_hal'
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i clean; \
	done
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr'
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe'
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample'
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel'
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate'
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/net80211'
rm -f *~ *.o *.ko *.mod.c
rm -f .depend .version .*.o.flags .*.o.d .*.o.cmd .*.ko.cmd
rm -rf .tmp_versions
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/net80211'
make -C ./tools  clean
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/tools'
rm -f athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info core a.out
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/tools'
rm -rf .tmp_versions
rm -f *.symvers svnversion.h
root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/flavio/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/ath/if_ath.o
make install
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/flavio/Desktop/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /home/flavio/Desktop/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_proto.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_scan.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_wireless.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_linux.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_monitor.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_rate.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_acl.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_scan_ap.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_scan_sta.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/ieee80211_xauth.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_wep.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_tkip.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_ccmp.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_acl.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_xauth.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_scan_sta.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/flavio/Desktop/madwifi-0.9.4/ath/ath_pci.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath/ath_pci.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/ath_hal/ath_hal.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_hal/ath_hal.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_acl.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_acl.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_ccmp.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_ccmp.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_scan_ap.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_scan_sta.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_tkip.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_tkip.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_wep.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_wep.ko
  CC      /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_xauth.mod.o
  LD [M]  /home/flavio/Desktop/madwifi-0.9.4/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/tools'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I..  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I..  wlanconfig.c
gcc -o ath_info -g -O2 -Wall ath_info.c
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/tools'
root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4# make install
sh scripts/find-madwifi-modules.sh 2.6.24-16-generic 

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
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install ath_pci.ko //lib/modules/2.6.24-16-generic/net
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath'
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_hal'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install ath_hal.ko //lib/modules/2.6.24-16-generic/net
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_hal'
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate'
for i in amrr/ onoe/ sample/ minstrel/; do \
		make -C $i install || exit 1; \
	done
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install ath_rate_amrr.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/amrr'
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install ath_rate_onoe.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/onoe'
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
install ath_rate_sample.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/sample'
make[2]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
cp ath_rate_minstrel.ko //lib/modules/2.6.24-16-generic/net
make[2]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate/minstrel'
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/ath_rate'
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/net80211'
test -d //lib/modules/2.6.24-16-generic/net || mkdir -p //lib/modules/2.6.24-16-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
		f=`basename $i .o`; \
		install $f.ko //lib/modules/2.6.24-16-generic/net; \
	done
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/net80211'
(export KMODPATH=/lib/modules/2.6.24-16-generic/net; /sbin/depmod -ae 2.6.24-16-generic)
modprobe ath_pci
make -C ./tools  install || exit 1
make[1]: Entering directory `/home/flavio/Desktop/madwifi-0.9.4/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig ath_info; do \
		install $i /usr/local/bin/$i; \
		strip /usr/local/bin/$i; \
	done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/home/flavio/Desktop/madwifi-0.9.4/tools'
root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4# modprobe ath_pci
root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4# sudo iwpriv ath0 bgscan 0
ath0      no private ioctls.

root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4# 











root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4/scripts# sudo ./madwifi-unload
sudo: ./madwifi-unload: command not found
root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4/scripts# 









im a real absolute beginner

---

### Post by Kajaste on 2008-06-16
maybe this will help [http://ubuntuforums.org/showthread.php?t=798485](http://ubuntuforums.org/showthread.php?t=798485)

---

### Post by cyberdork33 on 2008-06-16
> **flavio newbie said:**
> root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4/scripts# sudo ./madwifi-unload
sudo: ./madwifi-unload: command not found
root@flavio-laptop:/home/flavio/Desktop/madwifi-0.9.4/scripts#It seems that whatever script you are trying to run doesn't exist. What guide are you following? It looks like your system compiled the driver just fine.

---

