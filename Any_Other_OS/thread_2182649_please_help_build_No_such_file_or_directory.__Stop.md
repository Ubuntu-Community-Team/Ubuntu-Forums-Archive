---
title: "please help build: No such file or directory.  Stop. make: *** [all] Error 2"
date: 2013-10-21
forum: Any Other OS
---

### Post by weblink2 on 2013-10-21
hello every 1  every time i try to install anything .when i get to  (make) i get this error  No such file or directory.  Stop. make: *** [all] Error 2  i try backtrack,kali  but still the same problem i'm using wmware by the way and i did install wmware tools  Thanks in advance

---

### Post by oldos2er on 2013-10-22
Moved to Other OS/Distro Support.

---

### Post by drmrgd on 2013-10-22
I don't think it has anything to do with running in VMware.  I think you're likely missing some components or dependencies, or not quite building the package correctly.  Can you post more of the output during the make process so that we can see what's being run before the error occurs?  Also, you should mention what packages you're trying to build.

---

### Post by weblink2 on 2013-10-22
sorry for putting my thread in the wrong place i'm new here so... and thank u you for reply drmrgd  let's say i wanna install driver and patch for my wireless rtl8187l usb from aircrack-ng.org i'll follow every command and put every thing here

---

### Post by weblink2 on 2013-10-22
[COLOR=#ff0000]root@bt:~# ifconfig wlan0 down[/COLOR]

[COLOR=#ff0000]root@bt:~# rmmod r8187 rtl8187 2>/dev/null[/COLOR]

[COLOR=#ff0000]root@bt:~# wget http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip[/COLOR]
[SIZE=1]--2013-10-22 11:08:27--  
http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip
Resolving dl.aircrack-ng.org... 87.98.255.2, 2001:41d0:1:1b00:87:98:255:2
Connecting to dl.aircrack-ng.org|87.98.255.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 794171 (776K) [application/zip]
Saving to: `rtl8187_linux_26.1010.zip'

100%[======================================>] 794,171     41.0K/s   in 11s     

2013-10-22 11:08:45 (68.3 KB/s) - `rtl8187_linux_26.1010.zip' saved [794171/794171]
[/SIZE]
[COLOR=#ff0000]root@bt:~# unzip rtl8187_linux_26.1010.zip[/COLOR]

[SIZE=1]Archive:  rtl8187_linux_26.1010.zip
   creating: rtl8187_linux_26.1010.0622.2006/
  inflating: rtl8187_linux_26.1010.0622.2006/wlan0rmv  
  inflating: rtl8187_linux_26.1010.0622.2006/wlan0down  
  inflating: rtl8187_linux_26.1010.0622.2006/wlan0up  
  inflating: rtl8187_linux_26.1010.0622.2006/wlan0dhcp  
  inflating: rtl8187_linux_26.1010.0622.2006/ReadMe.txt  
  inflating: rtl8187_linux_26.1010.0622.2006/makedrv  
  inflating: rtl8187_linux_26.1010.0622.2006/makedrvbk  
  inflating: rtl8187_linux_26.1010.0622.2006/stack.tar.gz  
 extracting: rtl8187_linux_26.1010.0622.2006/ifcfg-wlan0  
  inflating: rtl8187_linux_26.1010.0622.2006/drv.tar.gz  
  inflating: rtl8187_linux_26.1010.0622.2006/makedrv~  
  inflating: rtl8187_linux_26.1010.0622.2006/ReadMe.txt~  
   creating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/.cvsignore  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/ChangeLog  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/Makefile  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/README  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/README-Windows.txt  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/base64.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/base64.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/config.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/config.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/config_file.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/config_ssid.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/crypto.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/crypto.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/crypto_gnutls.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/ctrl_iface.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_ttls.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_ttls.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eapol_sm.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eapol_sm.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eapol_test.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/events.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/hostapd.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/l2_packet.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/l2_packet_freebsd.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/l2_packet_linux.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/l2_packet_pcap.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/main.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/ms_funcs.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/ms_funcs.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/ndis_events.cpp  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/openssl-tls-extensions.patch  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/ctrl_iface.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/defconfig  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/defs.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_atmel.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_broadcom.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_bsd.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_hostap.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_hostap.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_ipw.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_madwifi.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_ndis.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_ndis.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_ndis_.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_ndiswrapper.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_prism54.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_cli.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_ctrl.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_ctrl.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_i.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_passphrase.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_supplicant.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_supplicant.conf  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_supplicant.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_supplicant_i.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/COPYING  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eloop.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eloop.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/common.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/pcsc_funcs.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/pcsc_funcs.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/preauth.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/preauth.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/preauth_test.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/priv_netlink.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/tls.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/tls_gnutls.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/tls_none.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/tls_openssl.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/tls_schannel.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/todo.txt  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/version.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/win_if_list.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_test.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_wext.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_wext.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/driver_wired.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/drivers.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_aka.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_defs.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_fast.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_gtc.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_i.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_leap.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_md5.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_mschapv2.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_otp.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_pax.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_pax_common.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_pax_common.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_peap.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_psk.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_psk_common.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_psk_common.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_sim.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_sim_common.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_sim_common.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_testing.txt  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_tls.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_tls_common.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_tls_common.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_tlv.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/eap_tlv.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/common.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/md5.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/md5.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/rc4.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/rc4.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/sha1.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/sha1.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/aes_wrap.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/aes_wrap.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/aes.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/radius.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/radius.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/radius_client.c  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/radius_client.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/config_types.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wireless_copy.h  
   creating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/.cvsignore  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/code_structure.doxygen  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/ctrl_iface.doxygen  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/doxygen.fast  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/doxygen.full  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/driver_wrapper.doxygen  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/eap.doxygen  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/kerneldoc2doxygen.pl  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/mainpage.doxygen  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/porting.doxygen  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/testing_tools.doxygen  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/wpa_supplicant.fig  
   creating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/.cvsignore  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/Makefile  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_background.sgml  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_cli.sgml  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_passphrase.sgml  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_supplicant.conf.sgml  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_supplicant.sgml  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_background.8  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_cli.8  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_passphrase.8  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_supplicant.conf.5  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/doc/docbook/wpa_supplicant.8  
   creating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/examples/
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/examples/ieee8021x.conf  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/examples/plaintext.conf  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/examples/wep.conf  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/examples/wpa-psk-tkip.conf  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/examples/wpa2-eap-ccmp.conf  
   creating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/
 extracting: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/.cvsignore  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/eventhistory.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/eventhistory.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/main.cpp  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/networkconfig.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/networkconfig.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/scanresults.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/scanresults.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/userdatarequest.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/userdatarequest.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/wpa_gui.pro  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/wpagui.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/wpagui.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui/wpamsg.h  
   creating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/
 extracting: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/.cvsignore  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/eventhistory.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/eventhistory.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/main.cpp  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/networkconfig.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/networkconfig.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/scanresults.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/scanresults.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/setup-mingw-cross-compiling  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/userdatarequest.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/userdatarequest.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/wpa_gui.pro  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/wpagui.ui  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/wpagui.ui.h  
  inflating: rtl8187_linux_26.1010.0622.2006/wpa_supplicant-0.4.9/wpa_gui-qt4/wpamsg.h  
[/SIZE]
[COLOR=#ff0000]root@bt:~# cd rtl8187_linux_26.1010.0622.2006/[/COLOR]

[COLOR=#000000]root@bt:~/rtl8187_linux_26.1010.0622.2006#[/COLOR]

 [COLOR=#ff0000]wget http://patches.aircrack-ng.org/rtl8187_2.6.27.patch[/COLOR]

[SIZE=1]--2013-10-22 11:09:33--  http://patches.aircrack-ng.org/rtl8187_2.6.27.patch
Resolving patches.aircrack-ng.org... 213.186.33.2, 2001:41d0:1:1b00:213:186:33:2
Connecting to patches.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 452734 (442K) [text/plain]
Saving to: `rtl8187_2.6.27.patch'

100%[======================================>] 452,734     61.6K/s   in 10s     

2013-10-22 11:09:56 (44.3 KB/s) - `rtl8187_2.6.27.patch' saved [452734/452734]

root@bt:~/rtl8187_linux_26.1010.0622.2006# [/SIZE]

[SIZE=2][COLOR=#ff0000]wget http://patches.aircrack-ng.org/rtl8187_2.6.32.patch[/COLOR][/SIZE]

[SIZE=1]--2013-10-22 11:10:09--  http://patches.aircrack-ng.org/rtl8187_2.6.32.patch
Resolving patches.aircrack-ng.org... 213.186.33.2, 2001:41d0:1:1b00:213:186:33:2
Connecting to patches.aircrack-ng.org|213.186.33.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4874 (4.8K) [text/plain]
Saving to: `rtl8187_2.6.32.patch'

100%[======================================>] 4,874       --.-K/s   in 0s      

2013-10-22 11:10:13 (51.9 MB/s) - `rtl8187_2.6.32.patch' saved [4874/4874][/SIZE]

[COLOR=#ff0000]root@bt:~/rtl8187_linux_26.1010.0622.2006# tar xzf drv.tar.gz[/COLOR]

[COLOR=#ff0000]root@bt:~/rtl8187_linux_26.1010.0622.2006# tar xzf stack.tar.gz[/COLOR]

[COLOR=#ff0000]root@bt:~/rtl8187_linux_26.1010.0622.2006# patch -Np1 -i rtl8187_2.6.27.patch[/COLOR]

[SIZE=1]patching file beta-8187/ieee80211_crypt.h
patching file beta-8187/ieee80211.h
patching file beta-8187/Makefile
patching file beta-8187/r8180_93cx6.c
patching file beta-8187/r8180_hw.h
patching file beta-8187/r8180_rtl8225.c
patching file beta-8187/r8180_rtl8225.h
patching file beta-8187/r8180_rtl8225z2.c
patching file beta-8187/r8180_wx.c
patching file beta-8187/r8187_core.c
patching file beta-8187/r8187_core.c~
patching file beta-8187/r8187.h
patching file beta-8187/r8187.h~
patching file beta-8187/.tmp_versions/r8187.mod
patching file ieee80211/ieee80211_crypt.c
patching file ieee80211/ieee80211_crypt_ccmp.c
patching file ieee80211/ieee80211_crypt.h
patching file ieee80211/ieee80211_crypt_tkip.c
patching file ieee80211/ieee80211_crypt_wep.c
patching file ieee80211/ieee80211.h
patching file ieee80211/ieee80211_module.c
patching file ieee80211/ieee80211_rx.c
patching file ieee80211/ieee80211_softmac.c
patching file ieee80211/ieee80211_softmac_wx.c
patching file ieee80211/ieee80211_tx.c
patching file ieee80211/ieee80211_wx.c
patching file ieee80211/Makefile
patching file ieee80211/Modules.symvers
patching file ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
patching file ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
patching file ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
patching file ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
patching file ieee80211/.tmp_versions/ieee80211-rtl.mod
patching file makedrv~
patching file Makefile
patching file ReadMe.txt~
patching file symvers
patching file wlan0rmv

[COLOR=#ff0000]root@bt:~/rtl8187_linux_26.1010.0622.2006# patch -Np1 -i rtl8187_2.6.32.patch[/COLOR]

patching file beta-8187/r8187.h
patching file beta-8187/r8187_core.c
patching file ieee80211/ieee80211_module.c
patching file ieee80211/ieee80211_rx.c
patching file ieee80211/ieee80211_tx.c[/SIZE]
root@bt:~/rtl8187_linux_26.1010.0622.2006# [SIZE=4][COLOR=#0000ff]make[/COLOR][/SIZE]

rm -f ieee80211/Module.symvers 2>/dev/null
rm -f ieee80211/Modules.symvers 2>/dev/null
make -C ieee80211 all
make[1]: Entering directory `/root/rtl8187_linux_26.1010.0622.2006/ieee80211'
make -C /lib/modules/3.2.6/build M=/root/rtl8187_linux_26.1010.0622.2006/ieee80211 modules
make[2]: Entering directory `/usr/src/linux-source-3.2.6'

  WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o
In file included from /root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:17:
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211.h:986: error: field ‘ps_task’ has incomplete type
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac_rtl7’:
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:1512: error: implicit declaration of function ‘tasklet_schedule’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init_rtl7’:
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2229: error: implicit declaration of function ‘tasklet_init’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_wpa_set_encryption_rtl7’:
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2474: error: implicit declaration of function ‘request_module’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2503: error: implicit declaration of function ‘try_module_get’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c: At top level:
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2648: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2648: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2648: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2649: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2649: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2649: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2650: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2650: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2650: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2651: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2651: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2651: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2652: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2652: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2652: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2653: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2653: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2653: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2654: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2654: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2654: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2655: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2655: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2655: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2656: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2656: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2656: warning: parameter names (without types) in function declaration
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2657: warning: data definition has no type or storage class
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2657: warning: type defaults to ‘int’ in declaration of ‘EXPORT_SYMBOL’
/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.c:2657: warning: parameter names (without types) in function declaration
make[3]: *** [/root/rtl8187_linux_26.1010.0622.2006/ieee80211/ieee80211_softmac.o] Error 1
make[2]: *** [_module_/root/rtl8187_linux_26.1010.0622.2006/ieee80211] Error 2
make[2]: Leaving directory `/usr/src/linux-source-3.2.6'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/root/rtl8187_linux_26.1010.0622.2006/ieee80211'
make: *** [all] Error 2
root@bt:~/rtl8187_linux_26.1010.0622.2006# [SIZE=4][COLOR=#0000ff]make install[/COLOR][/SIZE]

install -d /lib/modules/3.2.6/kernel/drivers/net/wireless/rtl_ieee80211
install -d /lib/modules/3.2.6/kernel/drivers/net/wireless/rtl8187
install -m 644 ./ieee80211/*.ko /lib/modules/3.2.6/kernel/drivers/net/wireless/rtl_ieee80211
install: cannot stat `./ieee80211/*.ko': No such file or directory
make: *** [install] Error 1
root@bt:~/rtl8187_linux_26.1010.0622.2006#

---

### Post by weblink2 on 2013-10-22
i try sudo make and sudo make install but still the same problem

---

### Post by oldos2er on 2013-10-22
[COLOR=#ff0000]> root@bt:~# wget [http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip](http://dl.aircrack-ng.org/drivers/rtl8187_linux_26.1010.zip)[/COLOR]

I'm sorry, but we don't support aircrack on this forum because of its potential to be used illegally. Try [http://forums.kali.org/](http://forums.kali.org/) instead. Thread closed.

---

