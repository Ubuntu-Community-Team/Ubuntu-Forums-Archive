---
title: "Problem installing ATI Mobility Radeon x1400 driver"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by hrolfp on 2007-03-10
I followed the instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b-2)

and downloaded the ATI driver installer for my ATI x1400 card here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.34.8-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.34.8-x86.x86_64.run)

I get a problem at this step :```
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
```

I got an error with the output:

```

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/edgy
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.34.8-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 8.34.8-1
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx.H14597/debian/control.template ]; then \
                cat /tmp/fglrx.H14597/debian/control.template > /tmp/fglrx.H14597/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.H14597/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/edgy/" /tmp/fglrx.H14597/debian/driver.$i > \
              /tmp/fglrx.H14597/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.H14597/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.H14597/debian/10fglrx.template > /tmp/fglrx.H14597/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.H14597/debian/fglrx.default ]; then \
          mv /tmp/fglrx.H14597/debian/fglrx.default /tmp/fglrx.H14597/debian/fglrx; \
        fi
dh_testdir
make: dh_testdir: Command not found
make: *** [configure] Error 127
Removing temporary directory: fglrx-install

```

Not sure what to do, since I downloaded the latest driver from the ATI site.

---

### Post by hrolfp on 2007-03-10
bump

---

### Post by .G$:. on 2008-05-07
2 me i checked both drivers the x64 n the non x64 n they both download the same thing theres no difference i think ati didnt put the correct link.

---

