---
title: "Help needed with ASUS USB-N13 Wireless Network Adapter"
date: 2011-11-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Need_your_Advice on 2011-11-17
Chili555

I need your help.  I tried to install the driver you had on your #17 (2009_1110_RT3070_Linux_STA_v2.1.2.0.tar.bz2) so my Wireless adapter USB-N13 would work.

I thought I had succeeded until I  typed iwconfig in a terminal window and noticed that the 'Bit Rate and the RTS' were missing.

Code:
    **** horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ iwconfig
        lo        no wireless extensions.

        eth0      no wireless extensions.

        ra0       RT2870 Wireless  ESSID:""  
                  Mode:Auto  Frequency=2.412 GHz  
        ****      Bit rate is missing    
        ****      RTS ... is missing
                  Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
                  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                  Tx excessive retries:0  Invalid misc:0   Missed beacon:0

When I typed 'dmesg | grep -e rt3 -3 ra0' in the terminal window, nothing happened.  

    lsmod | grep -e rt2 -e rt3
    dmesg | grep -e rt3 -e ra0
    modinfo rt3070sta | grep -e version -e 1784

Code:
    **** horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ lsmod | grep -e rt2 -e rt3
        rt3070sta             512239  0 
    
Code:
             horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ dmesg | grep -e rt3 -e ra0
        **** NOTHING!

Code:
         horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ modinfo rt3070sta | grep -e version -e 1784
        version:        2.1.2.0
        srcversion:     490C020EB5EF0484E8F2833
        vermagic:       2.6.32-02063235-generic SMP mod_unload modversions 586  

Code: 
         horace@horace-desktop ~ $ modinfo rt3070sta
        filename:       /lib/modules/2.6.32-02063235-generic/kernel/drivers/net/wireless/rt3070sta.ko
        version:        2.1.2.0
        license:        GPL
        description:    RT2870 Wireless Lan Linux Driver
        author:         Paul Lin <paul_lin@ralinktech.com>
        srcversion:     490C020EB5EF0484E8F2833
        alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
        alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
        depends:        
        vermagic:       2.6.32-02063235-generic SMP mod_unload modversions 586 
        parm:           mac:rt28xx: wireless mac addr (charp)

I think I am close, but no cigar yet. Please help me to get it working.

What I did to install the driver, from start to finish including the reference I used as a guide, is in the attached file What_I_Did.gz.

---

### Post by chili555 on 2011-11-17
Please try this:```
cd Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
sudo make uninstall
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Change as highlighted:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba [COLOR="Red"]rt2870sta[/COLOR]"
```Now please do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Change as highlighted:```
install [COLOR="Red"]rt2870sta[/COLOR] /sbin/modprobe --ignore-install [COLOR="Red"]rt2870sta[/COLOR] $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```In both cases, proofread carefully, save and close gedit. Now please do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and let us have your report.

---

### Post by Need_your_Advice on 2011-11-17
> **chili555 said:**
> Please try this:```
cd Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
sudo make uninstall
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Change as highlighted:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba [COLOR=Red]rt2870sta[/COLOR]"
```Now please do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Change as highlighted:```
install [COLOR=Red]rt2870sta[/COLOR] /sbin/modprobe --ignore-install [COLOR=Red]rt2870sta[/COLOR] $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id
```In both cases, proofread carefully, save and close gedit. Now please do:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Reboot and let us have your report.
This is what I did:

Code:
    horace@horace-desktop ~ $ cd Downloads
    horace@horace-desktop ~/Downloads $ cd 2009_1110_RT3070_Linux_STA_v2.1.2.0

    horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ sudo make uninstall
    [sudo] password for horace: 
        make -C /home/horace/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux -f Makefile.6 uninstall
        make[1]: Entering directory `/home/horace/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'
        rm -rf /lib/modules/2.6.32-02063235-generic/kernel/drivers/net/wireless/rt3070sta.ko
        /sbin/depmod -a 2.6.32-02063235-generic
        make[1]: Leaving directory `/home/horace/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux'

    horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ sudo gedit /etc/udev/rules.d/network_drivers.rules
        Replaced the line with the line below:
        ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0b05", ATTR{idProduct}=="1784", RUN+="/sbin/modprobe -qba rt2870sta"

    horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ sudo gedit /etc/modprobe.d/network_drivers.conf
        Replaced the line with the line below:
        install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "0b05 1784" > /sys/bus/usb/drivers/rt2870/new_id

    horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ sudo su

    horace-desktop 2009_1110_RT3070_Linux_STA_v2.1.2.0 # echo rt2870sta >> /etc/modules

    horace-desktop 2009_1110_RT3070_Linux_STA_v2.1.2.0 # exit
        exit
        horace@horace-desktop ~/Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0 $ 

Rebooted my computer

The wireless adapter light is on.

Code:
    horace@horace-desktop ~ $ iwconfig
        lo        no wireless extensions.

        eth0      no wireless extensions.

        wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
                  Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
                  Bit Rate:1 Mb/s   
                  RTS thr:off   Fragment thr:off
                  Link Quality=10/100  Signal level:-79 dBm  Noise level:-87 dBm
                  Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
                  Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Problem Solved!

Thanks a Million!

It is connected to my router with a 10% connection speed. :)

Is there any way I can increase the speed of the connection?

---

