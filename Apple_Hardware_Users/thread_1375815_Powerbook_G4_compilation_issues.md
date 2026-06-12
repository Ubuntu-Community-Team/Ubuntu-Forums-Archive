---
title: "Powerbook G4 compilation issues"
date: 2010-01-08
forum: Apple Hardware Users
---

### Post by sygard on 2010-01-08
Hi!

I recently installed Ubuntu 9.10 on my trusty old Powerbook G4 Titanium. All seems to work fine, but the built in Airport is WEP/Open only, not WPA. I have this Buffalo Wireless-N Nfiniti card which works fine on a x86 system (drivers fetched from [http://www.ralinktech.com/support.php?s=2]("http://www.ralinktech.com/support.php?s=2") it's the RT2870USB(RT2870/RT2770) chipset).
The issues begin when I try to compile the driver on the powerbook itself. make segfaults when ld'ing the driver object file **rt2870sta.o**, so I installed valgrind to try to analyze the situation, but it seems valgrind also segfaults, even when trying to run *valgrind --version*. *gdb* tells me nothing, either when running it on valgrind nor make.

Below follows the output of the make process:
```
make -C tools
make[1]: Entering directory `/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/Makefile
make -C /lib/modules/2.6.31-14-powerpc/build SUBDIRS=/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-powerpc'
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_aes.o
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_aes.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1072 bytes is larger than 1024 bytes
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_aes.c: In function &#8216;WscDecryptData&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_aes.c:1592: warning: the frame size of 1344 bytes is larger than 1024 bytes
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_aes.c: In function &#8216;WscEncryptData&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_aes.c:1522: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/mlme.o
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/mlme.c:4558: warning: the frame size of 1568 bytes is larger than 1024 bytes
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/action.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_aes.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rt_channel.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_profile.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_asic.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.o
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c:1711: warning: the frame size of 1320 bytes is larger than 1024 bytes
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c:1060: warning: the frame size of 1264 bytes is larger than 1024 bytes
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c:760: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c: In function &#8216;MlmeStartReqAction&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sync.c:579: warning: the frame size of 1072 bytes is larger than 1024 bytes
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/connect.o
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/connect.c:346: warning: the frame size of 1616 bytes is larger than 1024 bytes
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/wpa.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/ba_action.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtusb_io.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtusb_data.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/ee_prom.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/../../common/rtusb_dev_id.o
  LD [M]  /home/tormsl/Desktop/RT2870_LinuxSTA_V2.3.0.0/os/linux/rt2870sta.o
  Building modules, stage 2.
  MODPOST 1 modules
Segmentation fault
make[2]: *** [__modpost] Error 139
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-powerpc'
make: *** [LINUX] Error 2
```


Below follows gdb from valgrind:

```
tormsl@jotun:~$ gdb /usr/bin/valgrind.bin 
GNU gdb (GDB) 7.0-ubuntu
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "powerpc-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /usr/bin/valgrind.bin...done.
(gdb) run
Starting program: /usr/bin/valgrind.bin 
Executing new program: /usr/lib/valgrind/memcheck-ppc32-linux

Program received signal ?, Unknown signal.
0x38034e40 in _start ()
(gdb) backtrace
#0  0x38034e40 in _start ()
(gdb) q
A debugging session is active.

	Inferior 1 [process 2305] will be killed.

Quit anyway? (y or n) y
tormsl@jotun:~$ 
```

What do I do next?

Thanks.

---

