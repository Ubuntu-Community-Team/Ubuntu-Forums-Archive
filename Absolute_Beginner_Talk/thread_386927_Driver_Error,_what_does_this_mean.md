---
title: "Driver Error, what does this mean?"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-03-17
Hello,

I am installing a wireless driver (linux one) so not using Ndiswrapper.  Instructions say this:
```

< Installation >
Running the scripts can finish all operations of building up modules from source code and start the nic:

	(1)Build up the driver from the source code
         	./makedrv

    	(2)Load the driver module to kernel and start up nic
    		./wlan0up
           (if "insmod: error inserting 'r8180.ko': -File exists." met,
	        ./wlan0rmv
		./wlan0down
		./wlan0up
	    should be OK.
	   )
	(3)Refer to < Set wireless lan MIBs > to set Wireless LAN specific parameters.

```

So I untar to a directory and I ran the first command.  It went through its series of steps then I ran command #2 (wlan0up)

Please note I tried without sudo and with sudo.

```
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8180.ko': -1 Operation not permitted
SIOCSIFFLAGS: Permission denied
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ 
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ sudo ./wlan0up
Password:
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8180.ko': -1 Unknown symbol in module
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ 
```

What am I doing wrong?

---

### Post by dstew on 2007-03-17
Per instructions, if ismod error occurs, try:

./wlan0rmv
./wlan0down
./wlan0up

---

### Post by brandoncolorado on 2007-03-17
Sorry, should have been more specific.  I tried those too.  Is it possible that I need something installed (headers or something else I don't really understand) prior?

---

### Post by Bachstelze on 2007-03-17
Please paste what you get when running the first one - the actual driver build. Also, don't forget *sudo*.

---

### Post by brandoncolorado on 2007-03-18
Sorry about the delay in response:

```
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ sudo ./makedrv
Password:
ieee80211/
ieee80211/ieee80211_tx.c
ieee80211/Modules.symvers
ieee80211/ieee80211_softmac_wx.c
ieee80211/LICENSE
ieee80211/ieee80211_rx.c
ieee80211/ieee80211_crypt_tkip.c
ieee80211/ieee80211_crypt.h
ieee80211/ieee80211_crypt_ccmp.c
ieee80211/ieee80211_module.c
ieee80211/Makefile
ieee80211/.tmp_versions/
ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
ieee80211/.tmp_versions/ieee80211-rtl.mod
ieee80211/ieee80211.h
ieee80211/ieee80211_softmac.c
ieee80211/README
ieee80211/ieee80211_wx.c
ieee80211/ieee80211_crypt_wep.c
ieee80211/ieee80211_crypt.c
rtl818x-0.1/
rtl818x-0.1/r8180_wx.h
rtl818x-0.1/r8180_wx.c
rtl818x-0.1/r8180_rtl8225.h
rtl818x-0.1/r8180_rtl8255.h
rtl818x-0.1/AUTHORS
rtl818x-0.1/r8180_max2820.c
rtl818x-0.1/r8180.h
rtl818x-0.1/r8180_max2820.h
rtl818x-0.1/tags
rtl818x-0.1/r8180_sa2400.h
rtl818x-0.1/r8180_93cx6.c
rtl818x-0.1/ieee80211.h
rtl818x-0.1/r8180_gct.c
rtl818x-0.1/r8180_gct.h
rtl818x-0.1/.r8180_core.o.d
rtl818x-0.1/r8180_rtl8225.c.old
rtl818x-0.1/Modules.symvers
rtl818x-0.1/CHANGES
rtl818x-0.1/LICENSE
rtl818x-0.1/r8180_93cx6.h
rtl818x-0.1/README.master
rtl818x-0.1/r8180_hw.h
rtl818x-0.1/README
rtl818x-0.1/r8180_pm.c
rtl818x-0.1/r8180_sa2400.c
rtl818x-0.1/COPYING
rtl818x-0.1/README.adhoc
rtl818x-0.1/r8180_rtl8225.c
rtl818x-0.1/.tmp_versions/
rtl818x-0.1/.tmp_versions/r8180.mod
rtl818x-0.1/INSTALL
rtl818x-0.1/r8180_rtl8255.c
rtl818x-0.1/r8180_core.c
rtl818x-0.1/r8180_pm.h
rtl818x-0.1/Makefile
rtl818x-0.1/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/tmp
make -C /lib/modules/2.6.17-11-generic/build M=/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.o
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:391: warning: ISO C90 forbids mixed declarations and code
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1470: warning: ISO C90 forbids mixed declarations and code
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1472: warning: ‘chlen’ may be used uninitialized in this function
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1359:4: warning: #warning CHECK_LOCK_HERE
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac.c:1399:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_rx.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_tx.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_wx.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_module.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac_wx.o
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac_wx.c: In function ‘ieee80211_wx_set_wap’:
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_softmac_wx.c:143: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211-rtl.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST
  CC      /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211-rtl.ko
  CC      /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/tmp
make -C /lib/modules/2.6.17-11-generic/build M=/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_core.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_sa2400.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_93cx6.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_wx.o
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_wx.c:468: warning: ‘r8180_wx_set_monitor_type’ defined but not used
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_max2820.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_gct.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_rtl8225.o
  CC [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_rtl8255.o
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_rtl8255.c: In function ‘rtl8255_rf_init’:
/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180_rtl8255.c:1708: warning: ISO C90 forbids mixed declarations and code
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.o
  Building modules, stage 2.
  MODPOST
WARNING: "ieee80211_wx_get_freq" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_ps_tx_ack" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_power" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_power" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko] undefined!
  CC      /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.mod.o
  LD [M]  /home/brandon/Wireless/rtl8185_linux_26.1010.0531.2006/rtl818x-0.1/r8180.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ 
```


```
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ sudo ./wlan0up
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8180.ko': -1 Unknown symbol in module
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ 

```


```
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ sudo ./wlan0rmv
ERROR: Module r8180 does not exist in /proc/modules
ERROR: Module ieee80211_r8180 does not exist in /proc/modules
ERROR: Module ieee80211_crypt_r8180 does not exist in /proc/modules
brandon@brandon-laptop:~/Wireless/rtl8185_linux_26.1010.0531.2006$ 

```

---

