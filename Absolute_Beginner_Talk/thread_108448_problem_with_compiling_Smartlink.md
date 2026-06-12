---
title: "problem with compiling Smartlink"
date: 2005-12-26
forum: Absolute Beginner Talk
---

### Post by MaaSTaaR on 2005-12-26
Hello ...

i have Smartlink modem and i visited [https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4](https://wiki.ubuntu.com/DialupModemHowto#head-27c1595198125d81eb19201b131a3a91876e1ad4)

and do steps in "Modems supported by the Smartlink driver"

it's show for me this errors 

```
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem'
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[1]: Entering directory `/usr/src/modules/sl-modem/modem'
make[1]: Leaving directory `/usr/src/modules/sl-modem/modem'
dh_clean
/usr/bin/make -C drivers clean
make[1]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[1]: Leaving directory `/usr/src/modules/sl-modem/drivers'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/sl-modem'
dh_testdir
dh_testroot
rm -f build-arch-stamp build-indep-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem'
make[1]: [clean] Error 2 (ignored)
cd modem; /usr/bin/make clean SUPPORT_ALSA=1
make[2]: Entering directory `/usr/src/modules/sl-modem/modem'
make[2]: *** No rule to make target `clean'.  Stop.
make[2]: Leaving directory `/usr/src/modules/sl-modem/modem'
make[1]: [clean] Error 2 (ignored)
dh_clean
/usr/bin/make -C drivers clean
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
rm -f kernel-ver slamr.o slusb.o slamr.ko slusb.ko *st7554.o amrmo_init.o sysdep_amr.o *.mod.* .*.cmd *~
rm -f -r .tmp_versions
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
for templ in /usr/src/modules/sl-modem/debian/sl-modem-modules-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.12-9-386/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.12-9-386/g ;s/#KVERS#/2.6.12-9-386/g ; s/_KVERS_/2.6.12-9-386/g ; s/##KDREV##/2.6.12-9.23/g ; s/#KDREV#/2.6.12-9.23/g ; s/_KDREV_/2.6.12-9.23/g' < $templ > ${templ%.modules.in}; \
  done
dh_clean -k
dh_installdirs lib/modules/2.6.12-9-386/misc usr/lib/sl-modem
if ! test -e drivers/Makefile ; then echo "Please update the package, extract the tarball!"; exit 1 ; fi
/usr/bin/make -C drivers KERNEL_DIR=/usr/src/linux-headers-2.6.12-9-386 KVERS=2.6.12-9-386
make[2]: Entering directory `/usr/src/modules/sl-modem/drivers'
gcc-3.4 -I/usr/src/linux-headers-2.6.12-9-386/include -o kernel-ver kernel-ver.c
make[2]: gcc-3.4: Command not found
make[2]: *** [kernel-ver] Error 127
make[2]: Leaving directory `/usr/src/modules/sl-modem/drivers'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/sl-modem'
make: *** [kdist_build] Error 2
```

---

### Post by MaaSTaaR on 2005-12-27
up :???:

---

