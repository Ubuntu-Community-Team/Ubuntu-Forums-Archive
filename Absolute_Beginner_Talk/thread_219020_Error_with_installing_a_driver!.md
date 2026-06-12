---
title: "Error with installing a driver!"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-07-19
Hi, I am trying to install the fglrx driver for my ATI Card....
The file is a .run file and the default distros the drivers are for is Redhat and Suse...SO it said to type --listpkg in terminal so I did and found Dapper and then when I type --buildpkg
I get this Error:(Towards the bottom of the code)

```
Generating package: Ubuntu/6.06
/tmp/fglrx.oTDhbg ~/Desktop/fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.26.18-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture i386
 debian/rules build
echo "Using architecture: i386"
Using architecture: i386
if [ -f /tmp/fglrx.oTDhbg/debian/control.template ]; then \
                cat /tmp/fglrx.oTDhbg/debian/control.template > /tmp/fglrx.oTDhbg/debian/control; \
        fi
for i in preinst postinst postrm shlibs atieventsd.init ; do \
          if [ -f /tmp/fglrx.oTDhbg/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx.oTDhbg/debian/driver.$i > \
              /tmp/fglrx.oTDhbg/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx.oTDhbg/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
            /tmp/fglrx.oTDhbg/debian/10fglrx.template > /tmp/fglrx.oTDhbg/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx.oTDhbg/debian/fglrx.default ]; then \
          mv /tmp/fglrx.oTDhbg/debian/fglrx.default /tmp/fglrx.oTDhbg/debian/fglrx; \
        fi
dh_testdir
make: dh_testdir: Command not found
make: *** [configure] Error 127
~/Desktop/fglrx-install
Removing temporary directory: fglrx-install
```

---

### Post by zxcvbnm on 2006-07-19
Nevermind...I found out what I needed, It was the debhelper package...

Thanks anyways :D

---

