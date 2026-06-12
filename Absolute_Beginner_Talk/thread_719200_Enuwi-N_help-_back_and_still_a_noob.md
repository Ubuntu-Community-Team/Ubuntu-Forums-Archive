---
title: "Enuwi-N help- back and still a noob"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Kenjitamura on 2008-03-08
Been out of the ubuntu community for a while and back, forgotten just about everything lol.  I built a new system and I need to get my USB wireless N card functioning properly.  Using a D-link Dir655 wireless n gigabit router and Encore Enuwi-n 300 mb usb adapter by ralink.  Both worked great in XP.  Right now im using the linux opensource rt2870 drivers from ralink but I probably installed them incorrectly.  I didn't notice the instructions before doing make and make install, just as well because i find them confusing.  I can use WICD to connect to an unsecured local wireless network but i can't connect to my dir655 using WPA2.  My bros computer uses ubuntu as well and its connecting fine to the router although with a built in wireless adapter.  Here were the build instructions i ignored from the rt2870 drivers  

1> $tar -xvzf DPO_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPO_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	** Build for being controlled by WpaSupplicant with Ralink Custom Event
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make									# compile driver source code

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta

---

### Post by Kenjitamura on 2008-03-08
forgot to mention that for some reason my WICD lists the network im trying to connect to as WEP protected when it is WPA2.  My bros WICD correctly lists it as WPA.

---

