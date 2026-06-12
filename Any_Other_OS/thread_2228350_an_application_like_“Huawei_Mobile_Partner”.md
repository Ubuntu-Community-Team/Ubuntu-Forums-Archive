---
title: "an application like “Huawei Mobile Partner”"
date: 2014-06-06
forum: Any Other OS
---

### Post by ramakanta on 2014-06-06
I have a Huawei Data card .  Is there an application in Linux Mint which is like ***Huawei Mobile Partner , ***That should provide 
[LIST]
[*]Connection & Disconnection
[*]SMS
[*]Display Bandwidth
[*]Display Data Usage
[*]USSD
[/LIST]
USSD is the main important . thank you.

---

### Post by monkeybrain20122 on 2014-06-07
[http://askubuntu.com/questions/380650/in-ubuntu-is-there-an-application-like-huawei-mobile-partner-for-broadband-co](http://askubuntu.com/questions/380650/in-ubuntu-is-there-an-application-like-huawei-mobile-partner-for-broadband-co)

---

### Post by ramakanta on 2014-06-07
I think **V Mobile Broadband** is for **Vodafone Mobile Connect** . 

Modem Manager GUI ok .

but what about **Huawei data** card ????

---

### Post by ramakanta on 2014-06-07
> **monkeybrain20122 said:**
> [http://askubuntu.com/questions/380650/in-ubuntu-is-there-an-application-like-huawei-mobile-partner-for-broadband-co](http://askubuntu.com/questions/380650/in-ubuntu-is-there-an-application-like-huawei-mobile-partner-for-broadband-co)

when check balance by using Modem manager it shows look likes 

 &#49712;&#23335;&#29633;&#24620;&#27544;&#44339;&#38597;&#8345;&#3364;&#33733;&#28332;&#26995;&#2578;&#34521;&#15000;&#2822;&#25349;&#23361;&#53428;&#14805;&#49500;&#12312;&#11224;&#31362;&#42701;&#43342;&#6246;&#60256;&#11800;&#52229;

---

### Post by ramakanta on 2014-07-13
when ever i want to install Linux** Huawei **Mobile Partner , the following error  message displayed ..

```


                        
Local path is: /usr/local/Mobile_Partner
  Installing Mobile Partner...
 /usr/local/Mobile_Partner/driver/ndis_driver
 modinfo: ERROR: missing module or filename.
 rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'cdc_ether': No such file or directory
 rmmod: ERROR: could not remove module cdc_ether: No such file or directory
 rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'usbnet': No such file or directory
 rmmod: ERROR: could not remove module usbnet: No such file or directory
 rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'hw_cdc_driver': No such file or directory
 rmmod: ERROR: could not remove module hw_cdc_driver: No such file or directory
 make -C src/ clean
 make[1]: Entering directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
 rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh  "clean" "/lib/modules/3.13.0-24-generic/build/include/linux/usb"
 rmmod -f hw_cdc_driver
 rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'hw_cdc_driver': No such file or directory
 rmmod: ERROR: could not remove module hw_cdc_driver: No such file or directory
 make[1]: *** [clean] Error 1
 make[1]: Leaving directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
 make: *** [clean] Error 2
 make -C src/ modules
 make[1]: Entering directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
 #/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh  "modules" "/lib/modules/3.13.0-24-generic/build/include/linux/usb"
 make -C /lib/modules/3.13.0-24-generic/build SUBDIRS=/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src modules
 make[2]: Entering directory `/usr/src/linux-headers-3.13.0-24-generic'
   CC [M]  /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o
 In file included from include/linux/module.h:17:0,
                  from /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:23:
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function &#8216;__check_ncm_prefer_32&#8217;:
 include/linux/moduleparam.h:349:45: warning: return from incompatible pointer type [enabled by default]
   static inline type *__check_##name(void) { return(p); }
                                              ^
 include/linux/moduleparam.h:395:35: note: in expansion of macro &#8216;__param_check&#8217;
  #define param_check_bool(name, p) __param_check(name, p, bool)
                                    ^
 include/linux/moduleparam.h:127:2: note: in expansion of macro &#8216;param_check_bool&#8217;
   param_check_##type(name, &(value));       \
   ^
 include/linux/moduleparam.h:113:2: note: in expansion of macro &#8216;module_param_named&#8217;
   module_param_named(name, name, type, perm)
   ^
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:112:1: note: in expansion of macro &#8216;module_param&#8217;
  module_param(ncm_prefer_32, bool, S_IRUGO);
  ^
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function &#8216;__check_ncm_prefer_crc&#8217;:
 include/linux/moduleparam.h:349:45: warning: return from incompatible pointer type [enabled by default]
   static inline type *__check_##name(void) { return(p); }
                                              ^
 include/linux/moduleparam.h:395:35: note: in expansion of macro &#8216;__param_check&#8217;
  #define param_check_bool(name, p) __param_check(name, p, bool)
                                    ^
 include/linux/moduleparam.h:127:2: note: in expansion of macro &#8216;param_check_bool&#8217;
   param_check_##type(name, &(value));       \
   ^
 include/linux/moduleparam.h:113:2: note: in expansion of macro &#8216;module_param_named&#8217;
   module_param_named(name, name, type, perm)
   ^
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:115:1: note: in expansion of macro &#8216;module_param&#8217;
  module_param(ncm_prefer_crc, bool, S_IRUGO);
  ^
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: In function &#8216;__check_rt_debug&#8217;:
 include/linux/moduleparam.h:349:45: warning: return from incompatible pointer type [enabled by default]
   static inline type *__check_##name(void) { return(p); }
                                              ^
 include/linux/moduleparam.h:395:35: note: in expansion of macro &#8216;__param_check&#8217;
  #define param_check_bool(name, p) __param_check(name, p, bool)
                                    ^
 include/linux/moduleparam.h:127:2: note: in expansion of macro &#8216;param_check_bool&#8217;
   param_check_##type(name, &(value));       \
   ^
 include/linux/moduleparam.h:113:2: note: in expansion of macro &#8216;module_param_named&#8217;
   module_param_named(name, name, type, perm)
   ^
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:127:1: note: in expansion of macro &#8216;module_param&#8217;
  module_param(rt_debug, bool, S_IRUGO|S_IWUSR);
  ^
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c: At top level:
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.c:155:27: fatal error: linux/usb/ncm.h: No such file or directory
  #include <linux/usb/ncm.h>
                            ^
 compilation terminated.
 make[3]: *** [/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o] Error 1
 make[2]: *** [_module_/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src] Error 2
 make[2]: Leaving directory `/usr/src/linux-headers-3.13.0-24-generic'
 make[1]: *** [modules] Error 2
 make[1]: Leaving directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
 make: *** [modules] Error 2
 make -C src/ install
 make[1]: Entering directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
 #install -m 744 -c hw_cdc_driver.o /lib/modules/3.13.0-24-generic/kernel/drivers/usb/net
 #depmod -a
 #modprobe hw_cdc_driver
 /usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src/add_header.sh  "install"
 modprobe hw_cdc_driver
 modprobe: FATAL: Module hw_cdc_driver not found.
 make[1]: *** [install] Error 1
 make[1]: Leaving directory `/usr/local/Mobile_Partner/driver/ndis_driver/ndis_src/src'
 make: *** [install] Error 2
 

 [COLOR=#ff3333]Install NDIS driver failed.[/COLOR]
 [COLOR=#ff3333]The compiling environment is not all ready.[/COLOR]
 [COLOR=#ff3333]Please check gcc, make and kernel buid(/lib/modules/3.13.0-24-generic/build) to be all installed?[/COLOR]
 [COLOR=#ff3333]Now please enter any key to finish other installations.[/COLOR]
 [COLOR=#ff3333]NDIS is disabled, and only Modem can be used.[/COLOR]
 AUTORUNPATH=/home/thinkuser/.config/autostart
 ADDRUNLEVEL=/etc/rc5.d
 &#8216;/etc/rc5.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
 &#8216;/etc/rc5.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
 ADDRUNLEVEL=/etc/rc3.d
 &#8216;/etc/rc3.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
 &#8216;/etc/rc3.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
 ADDRUNLEVEL=/etc/rc4.d
 &#8216;/etc/rc4.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
 &#8216;/etc/rc4.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
 ADDRUNLEVEL=/etc/rc2.d
 &#8216;/etc/rc2.d/S99runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
 &#8216;/etc/rc2.d/K10runhwactivator&#8217; -> &#8216;/etc/init.d/runhwactivator&#8217;
                                           [ done ]  
 

 Finished, press any key to exit
  


```

previously in Ubuntu 10.04 it was perfectly installed ..

---

