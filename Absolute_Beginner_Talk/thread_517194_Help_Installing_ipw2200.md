---
title: "Help: Installing ipw2200"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by ultranoize on 2007-08-04
Hi, I have a ThinkPad T43 with Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05).  I'm trying to install ipw2200 from source according to [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1847&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1847&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")
When I try to make it I get the following error:
```

spp@t43:~/OtherPrograms/ipw2200-1.2.0$ make
mkdir -p /home/spp/OtherPrograms/ipw2200-1.2.0/tmp/.tmp_versions
cp /lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/*.mod /home/spp/OtherPrograms/ipw2200-1.2.0/tmp/.tmp_versions
cp /lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/../Modules.symvers /home/spp/OtherPrograms/ipw2200-1.2.0
cp: cannot stat `/lib/modules/2.6.20-16-generic/net/ieee80211/.tmp_versions/../Modules.symvers': No such file or directory
make: [modules] Error 1 (ignored)
make -C /lib/modules/2.6.20-16-generic/build M=/home/spp/OtherPrograms/ipw2200-1.2.0 MODVERDIR=/home/spp/OtherPrograms/ipw2200-1.2.0/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.o
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_led_link_on’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:864: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_led_link_off’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:907: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘__ipw_led_activity_on’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:945: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:947: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:950: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:952: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_led_shutdown’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:1141: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:1142: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:1143: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_radio_kill_sw’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:1825: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:1833: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:1835: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_irq_tasklet’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:2044: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:2046: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_gather_stats’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:4301: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_rx_notification’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:4428: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:4692: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:4731: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_adhoc_check’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:6042: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_request_scan_helper’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:6390: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_associate’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:7579: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_rf_kill’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10653: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_link_up’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10696: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10705: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_link_down’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10724: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10725: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10726: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10756:56: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_setup_deferred_work’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10756: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10756: error: (Each undeclared identifier is reported only once
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10756: error: for each function it appears in.)
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10757:52: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10758:58: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10759:57: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10760:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10761:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10762:48: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10763:56: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10764:60: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10766:45: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10768:53: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10770:48: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10771:72: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10772:42: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10773:54: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10774:66: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10775:70: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10777:9: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10779:9: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10781:9: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:10783:52: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_up’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:11309: warning: passing argument 2 of ‘queue_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_pci_probe’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:11674: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c: In function ‘ipw_pci_remove’:
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:11808: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:11809: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:11810: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:11811: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.c:11812: warning: passing argument 1 of ‘cancel_delayed_work’ from incompatible pointer type
make[2]: *** [/home/spp/OtherPrograms/ipw2200-1.2.0/ipw2200.o] Error 1
make[1]: *** [_module_/home/spp/OtherPrograms/ipw2200-1.2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2

```

Any ideas what might be wrong?  The procedures seems to be straight forward.

---

### Post by sab0403 on 2007-08-04
Perhaps you need a ./configure first?

---

### Post by ultranoize on 2007-08-04
no luck with ./config, this is what I get:
```

spp@t43:~/OtherPrograms/ipw2200-1.2.0$ ./config 
No 'cfg' found in /sys/bus/pci/drivers/ipw2200.

```

Any other suggestions?? Please  ??

---

### Post by ultranoize on 2007-08-07
I decided to reinstall fesity and after the 109 updates and a restart, i had wireless out-of-the-box. !!!!!!

---

