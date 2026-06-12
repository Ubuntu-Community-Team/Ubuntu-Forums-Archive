---
title: "ZD1211 Xubuntu 6.06"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by benjgvps on 2008-01-28
I need to install my ZD1211 based USB Wifi dongle on my iMac G3 with xubuntu 6.06 and I try to build the driver that was on the disk and it gave me an error when compiling: entering directory '/lib/modules/2.6.15-26-powerpc/build'
***no rule to make target 'modules'.   stop.

Would upgrading to 6.10 help me? I'm about to pull my hair out because I have been trying to get the damned thing working for the past 3 days.

---

### Post by benjgvps on 2008-01-28
I have the whole thing now:

ben@Bens-iMac:/tmp/wifi$ make
make both
make[1]: Entering directory `/tmp/wifi'
make clean
make[2]: Entering directory `/tmp/wifi'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/tmp/wifi'
make ZD1211REV_B=0
make[2]: Entering directory `/tmp/wifi'
/lib/modules/2.6.15-26-powerpc/build
/tmp/wifi
-I/tmp/wifi/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.15-26-powerpc/build SUBDIRS=/tmp/wifi modules
make[3]: Entering directory `/lib/modules/2.6.15-26-powerpc/build'
make[3]: *** No rule to make target `modules'.  Stop.
make[3]: Leaving directory `/lib/modules/2.6.15-26-powerpc/build'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tmp/wifi'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/tmp/wifi'
make: *** [all] Error 2
ben@Bens-iMac:/tmp/wifi$ cd
ben@Bens-iMac:~$ sudo delete /lib/firmware/zd1211
Password:
sudo: delete: command not found
ben@Bens-iMac:~$ deldir
bash: deldir: command not found
ben@Bens-iMac:~$ delete
bash: delete: command not found
ben@Bens-iMac:~$ del
bash: del: command not found
ben@Bens-iMac:~$ sudo remove /lib/firmware/zd1211
sudo: remove: command not found
ben@Bens-iMac:~$ sudo rm /lib/firmware/zd1211
rm: cannot remove `/lib/firmware/zd1211': Is a directory
ben@Bens-iMac:~$ sudo rmdir /lib/firmware/zd1211
ben@Bens-iMac:~$ cd /tmp/wifi
ben@Bens-iMac:/tmp/wifi$ make
make both
make[1]: Entering directory `/tmp/wifi'
make clean
make[2]: Entering directory `/tmp/wifi'
rm -rf .tmp_versions .*.cmd *.ko *.mod.c *.mod.o *.o src/*.o  src/.*.o.cmd menudbg apdbg
make[2]: Leaving directory `/tmp/wifi'
make ZD1211REV_B=0
make[2]: Entering directory `/tmp/wifi'
/lib/modules/2.6.15-26-powerpc/build
/tmp/wifi
-I/tmp/wifi/src/include -fomit-frame-pointer -O2 -Wall -Wstrict-prototypes -pipe -DHOST_IF_USB -DAMAC -DGCCK -DOFDM -DHOSTAPD_SUPPORT -DUSE_EP4_SET_REG -DDOWNLOADFIRMWARE -DfTX_GAIN_OFDM=0 -DfNEW_CODE_MAP=1 -DfWRITE_WORD_REG=1 -DfREAD_MUL_REG=1 -DENHANCE_RX=1 -DZDCONF_MENUDBG -DZDCONF_APDBG -DZD1211
src/zd1205.o src/zdasocsvc.o src/zdauthreq.o src/zdauthrsp.o src/zdmmrx.o src/zdshared.o src/zdhci.o src/zdglobal.o src/zdencrypt.o src/zdpmfilter.o src/zdpsmon.o src/zdsynch.o src/zdbuf.o src/zd1205_proc.o src/zdhw.o src/zddebug.o src/zdtkipseed.o src/zdmic.o src/zddebug2.o src/zdusb.o src/zd1211.o
make -C /lib/modules/2.6.15-26-powerpc/build SUBDIRS=/tmp/wifi modules
make[3]: Entering directory `/lib/modules/2.6.15-26-powerpc/build'
make[3]: *** No rule to make target `modules'.  Stop.
make[3]: Leaving directory `/lib/modules/2.6.15-26-powerpc/build'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tmp/wifi'
make[1]: *** [both] Error 2
make[1]: Leaving directory `/tmp/wifi'
make: *** [all] Error 2

---

