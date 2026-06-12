---
title: "DWL G122 on KUbuntu PPC... several issues with several driver"
date: 2005-12-01
forum: Apple PPC Users
---

### Post by lqbweb on 2005-12-01
In the first place sorry for my bad english :S 
 
 I'm trying to make work my new D-Link DWL-g122 on my ibook 12'' with Ubuntu 5.1.... First I'll try to compile and install your rt2x00 driver, it compile and install well but when I try to make a 'ifconfig rausb0 up' my cpu set to 100% and my computer become frozen..... and i think as SMP as PREEMPT are disabled in my kernel: 
 
 root@ibu:/boot# cat config-2.6.12-9-powerpc | grep SMP ; cat config-2.6.12-9-powerpc | grep PREEMPT 
 CONFIG_BROKEN_ON_SMP=y 
 # CONFIG_SMP is not set 
 # CONFIG_PREEMPT is not set 
 root@ibu:/boot# 
 
 
 
 So, look this I decide to try with ural driver. First and like I've read in the forum make: 
 
 root@ibu:/lib/modules/2.6.12-9-powerpc# rm -r net/ieee80211 
 root@ibu:/lib/modules/2.6.12-9-powerpc# 
 
 to del the previous version of the ieee80211 and depmod -a... 
 
 Then I dispose to compile and install ural driver: 
 
 
 root@ibu:/home/yo/Documentos/RT2500/ural-linux-0.8.2# make 
 mkdir -p ./symbols 
 for i in ./net80211 ./ural; do \ 
 (cd $i; make) || exit 1; \ 
 done 
 make[1]: Entering directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211' 
 make -C /lib/modules/2.6.12-9-powerpc/build SUBDIRS=/home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211 MODVERDIR=/home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/../symbols modules 
 make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-powerpc' 
 
 WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9-powerpc/Module.symvers 
 is missing; modules will have no dependencies and modversions. 
 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/if_media.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/rc4.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_crypto.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_input.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_node.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_output.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_proto.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_wireless.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_linux.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_crypto_none.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_acl.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_crypto_ccmp.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_crypto_tkip.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_crypto_wep.o 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/ieee80211_xauth.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_wep.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_tkip.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_ccmp.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_acl.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_xauth.o 
 Building modules, stage 2. 
 MODPOST 
 CC /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan.mod.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan.ko 
 CC /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_acl.mod.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_acl.ko 
 CC /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_ccmp.mod.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_ccmp.ko 
 CC /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_tkip.mod.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_tkip.ko 
 CC /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_wep.mod.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_wep.ko 
 CC /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_xauth.mod.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211/wlan_xauth.ko 
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-powerpc' 
 make[1]: Leaving directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211' 
 make[1]: Entering directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/ural' 
 make -C /lib/modules/2.6.12-9-powerpc/build SUBDIRS=/home/yo/Documentos/RT2500/ural-linux-0.8.2/ural MODVERDIR=/home/yo/Documentos/RT2500/ural-linux-0.8.2/ural/../symbols modules 
 make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-powerpc' 
 
 WARNING: Symbol version dump /usr/src/linux-headers-2.6.12-9-powerpc/Module.symvers 
 is missing; modules will have no dependencies and modversions. 
 
 CC [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/ural/if_ral.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/ural/ural.o 
 Building modules, stage 2. 
 MODPOST 
 CC /home/yo/Documentos/RT2500/ural-linux-0.8.2/ural/ural.mod.o 
 LD [M] /home/yo/Documentos/RT2500/ural-linux-0.8.2/ural/ural.ko 
 make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-powerpc' 
 make[1]: Leaving directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/ural' 
 root@ibu:/home/yo/Documentos/RT2500/ural-linux-0.8.2# 
 
 
 
 
 Aparently it make good.... Next step, make install: 
 
 
 
 root@ibu:/home/yo/Documentos/RT2500/ural-linux-0.8.2# make install 
 for i in ./net80211 ./ural; do \ 
 (cd $i; make install) || exit 1; \ 
 done 
 make[1]: Entering directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211' 
 test -d //lib/modules/2.6.12-9-powerpc/net || mkdir -p //lib/modules/2.6.12-9-powerpc/net 
 for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o; do \ 
 f=`basename $i .o`; \ 
 strip -S $f.ko; \ 
 cp $f.ko //lib/modules/2.6.12-9-powerpc/net; \ 
 done 
 make[1]: Leaving directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/net80211' 
 make[1]: Entering directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/ural' 
 test -d //lib/modules/2.6.12-9-powerpc/net || mkdir -p //lib/modules/2.6.12-9-powerpc/net 
 strip -S ural.ko 
 cp ural.ko //lib/modules/2.6.12-9-powerpc/net 
 make[1]: Leaving directory `/home/yo/Documentos/RT2500/ural-linux-0.8.2/ural' 
 root@ibu:/home/yo/Documentos/RT2500/ural-linux-0.8.2# 
 
 
 Let me continue... Then I try to load module but: 
 
 root@ibu:/home/yo/Documentos/RT2500/ural-linux-0.8.2# modprobe ural 
 FATAL: Error inserting ural (/lib/modules/2.6.12-9-powerpc/net/ural.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
 root@ibu:/home/yo/Documentos/RT2500/ural-linux-0.8.2# 
 
 
 
 
 
 I make one dmesg and: 
 
 [ 4256.201440] ural: disagrees about version of symbol ieee80211_chan2ieee 
 [ 4256.201447] ural: Unknown symbol ieee80211_chan2ieee 
 [ 4256.201646] ural: disagrees about version of symbol ieee80211_ioctl_siwretry 
 [ 4256.201654] ural: Unknown symbol ieee80211_ioctl_siwretry 
 [ 4256.201752] ural: disagrees about version of symbol ieee80211_ioctl_siwnickn 
 [ 4256.201760] ural: Unknown symbol ieee80211_ioctl_siwnickn 
 [ 4256.201867] ural: disagrees about version of symbol ieee80211_ioctl_siwscan 
 [ 4256.201875] ural: Unknown symbol ieee80211_ioctl_siwscan 
 [ 4256.201972] ural: disagrees about version of symbol ieee80211_ioctl_siwmode 
 [ 4256.201989] ural: Unknown symbol ieee80211_ioctl_siwmode 
 [ 4256.202085] ural: disagrees about version of symbol ieee80211_ioctl_getoptie 
 [ 4256.202092] ural: Unknown symbol ieee80211_ioctl_getoptie 
 [ 4256.202190] ural: disagrees about version of symbol ieee80211_ioctl_giwessid 
 [ 4256.202198] ural: Unknown symbol ieee80211_ioctl_giwessid 
 [ 4256.202293] ural: disagrees about version of symbol ieee80211_ioctl_giwscan 
 [ 4256.202300] ural: Unknown symbol ieee80211_ioctl_giwscan 
 [ 4256.202397] ural: disagrees about version of symbol ieee80211_crypto_encap 
 [ 4256.202405] ural: Unknown symbol ieee80211_crypto_encap 
 [ 4256.202560] ural: disagrees about version of symbol ieee80211_ioctl_siwessid 
 [ 4256.202568] ural: Unknown symbol ieee80211_ioctl_siwessid 
 [ 4256.202817] ural: disagrees about version of symbol ieee80211_ioctl_giwtxpow 
 [ 4256.202825] ural: Unknown symbol ieee80211_ioctl_giwtxpow 
 root@ibu:/home/yo/Documentos/RT2500/ural-linux-0.8.2# 
 
 There are more issues like those but I doesn't wrote it to abbreviate... 
 
 I've try to compile the new version of ieee80211 but it doesn't appear choose anything in ural execution... 
 
 Anyone know how can I make to run my DLink Stick? 
 
 
 Thanks....

---

### Post by daller on 2005-12-05
I'm sorry to disapoint you!

See here:

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards)

...depending on your revision, it will either work with ndiswrapper or not work at all!

The problem here is, that ndiswrapper can't run on PPC-machines!

---

