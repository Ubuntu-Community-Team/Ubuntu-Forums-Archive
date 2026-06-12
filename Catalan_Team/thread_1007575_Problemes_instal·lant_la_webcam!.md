---
title: "Problemes instal·lant la webcam!"
date: 2008-12-10
forum: Catalan Team
---

### Post by mcako on 2008-12-10
Lo que creia que seria lo més fàcil del món m'està resultant tot lo contrari.
He intentat instal·lar els drivers per la webcam que tinc però m'ha donat problemes al compilar el modul de kernel.
Segons el lsusb la meva webcam es del fabricant Z-Star i he vist que és compatible amb el driver gspca:
```
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
Els passos que he seguit són molt senzills:
```

sudo aptitude install build-essential
sudo apt-get install linux-headers-`uname -r`
apt-get install gspca-source unp
cd /usr/src
unp gspca.tar.bz2 
cd /usr/src/gpsca/modules
make install

```

I al fer el make és on peta, el log es el següent:
```

dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[1]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[1]: Leaving directory `/usr/src/modules/gspca'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/gspca'
dh_testdir
dh_testroot
dh_clean
/usr/bin/make -C /usr/src/modules/gspca clean
make[2]: Entering directory `/usr/src/modules/gspca'
rm -r -f *.o decoder/.gspcadecoder.o.cmd decoder/*.o \
	.gspca.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i \
	*.symvers *.err
make[2]: Leaving directory `/usr/src/modules/gspca'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.27-9-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.27-9-generic/g ;s/#KVERS#/2.6.27-9-generic/g ; s/_KVERS_/2.6.27-9-generic/g ; s/##KDREV##/2.6.27-9.19/g ; s/#KDREV#/2.6.27-9.19/g ; s/_KDREV_/2.6.27-9.19/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
# Build the module
/usr/bin/make -C /usr/src/modules/gspca KERNEL_VERSION=2.6.27-9-generic KERNELDIR=/usr/src/linux-headers-2.6.27-9-generic
make[2]: Entering directory `/usr/src/modules/gspca'
/usr/bin/make -C /usr/src/linux-headers-2.6.27-9-generic SUBDIRS=/usr/src/modules/gspca CC=gcc modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:54:27: error: asm/semaphore.h: No such file or directory
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_ioctl&#8217;:
/usr/src/modules/gspca/gspca_core.c:2463: error: implicit declaration of function &#8216;video_usercopy&#8217;
/usr/src/modules/gspca/gspca_core.c: At top level:
/usr/src/modules/gspca/gspca_core.c:2609: error: unknown field &#8216;owner&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c:2609: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2611: error: unknown field &#8216;type&#8217; specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca50x_create_sysfs&#8217;:
/usr/src/modules/gspca/gspca_core.c:2769: error: implicit declaration of function &#8216;video_device_create_file&#8217;
/usr/src/modules/gspca/gspca_core.c:2780: error: implicit declaration of function &#8216;video_device_remove_file&#8217;
/usr/src/modules/gspca/gspca_core.c: In function &#8216;spca5xx_probe&#8217;:
/usr/src/modules/gspca/gspca_core.c:4301: error: incompatible types in assignment
make[4]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[3]: *** [_module_/usr/src/modules/gspca] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/gspca'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/gspca'
make: *** [kdist_build] Error 2

```

Òbviament si faig un "sudo modprobe gspca" no em troba el modul.

Sembla que no compila perquè no troba semaphore.h i algunes coses més, ho he estat mirant en altres forums i es veu que és un problema bastant generalitzat, tot i així no he trobat la solució.

He provat mil coses, instal·lar els drivers amb l'Easycam, amb el module-assistant fent:
```
m-a prepare
m-a a-i gspca

```
Però res, em segueix donant els mateixos errors.

---

