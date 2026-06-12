---
title: "problem with creating deb packages from ati driver installer"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by que on 2006-10-06
Hi, my first real problem.

I'm trying to install drivers for ATI 200M using tomahawk's (sorry if spelling is off) suggestions, but I can't get the installation package to produce .deb's.. 


```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.24.8.............................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
cp: cannot stat `/fglrx-install/x690_64a/*': No such file or directory
cp: cannot stat `/fglrx-install/arch/x86_64/*': No such file or directory
/tmp/fglrx /fglrx-install
Package build failed!
Package build utility output:
dpkg-buildpackage: source package is fglrx-installer
dpkg-buildpackage: source version is 8.24.8-1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://www.ati.com/support/driver.html>
dpkg-buildpackage: host architecture amd64
 debian/rules build
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx/debian/fglrx.default ]; then \
          mv /tmp/fglrx/debian/fglrx.default /tmp/fglrx/debian/fglrx; \
        fi
dh_testdir
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
if [ -f /tmp/fglrx/debian/control.template ]; then \
                cat /tmp/fglrx/debian/control.template > /tmp/fglrx/debian/control; \
        fi
for i in preinst postinst prerm postrm ; do \
          if [ -f /tmp/fglrx/debian/driver.$i ]; then \
            sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
                -e "s/#DISTRO#/dapper/" /tmp/fglrx/debian/driver.$i > \
              /tmp/fglrx/debian/xorg-driver-fglrx.$i; \
          fi; \
        done
if [ -f /tmp/fglrx/debian/10fglrx.template ]; then \
          sed -e "s|#XMODDIR#|usr/lib/xorg/modules|" -e "s|#XMODDIR32#|usr/lib32/xorg/modules|" \
            /tmp/fglrx/debian/10fglrx.template > /tmp/fglrx/debian/10fglrx; \
        fi
if [ -f /tmp/fglrx/debian/fglrx.default ]; then \
          mv /tmp/fglrx/debian/fglrx.default /tmp/fglrx/debian/fglrx; \
        fi
dh_testdir
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
rm -f /tmp/fglrx/debian/control
sed -e 's/#XSERVER#/xorg/g' debian/control.template > /tmp/fglrx/debian/control
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
                usr/lib \
                usr/lib/xorg/modules \
                usr/lib/xorg/modules/dri \
                usr/lib/xorg/modules/drivers \
                usr/lib/xorg/modules/linux \
                usr/share/fglrx/diversions \
                etc/acpi \
                etc/acpi/events \
                etc/default
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
                usr/lib32 \
                usr/lib32/xorg/modules \
                usr/lib32/xorg/modules/dri \
                usr/lib32/xorg/modules/drivers \
                usr/lib32/xorg/modules/linux \
                etc/X11/Xsession.d
dh_installdirs -pxorg-driver-fglrx-dev \
                usr/include \
                usr/lib
dh_installdirs -pfglrx-kernel-source \
                usr/src/modules/fglrx \
                usr/src/modules/fglrx/debian
dh_installdirs -A -pfglrx-control \
                usr/bin \
                usr/share \
                usr/share/applnk \
                usr/share/gnome \
                usr/share/gnome/apps \
                usr/share/icons \
                usr/share/pixmaps
dh_installdirs -pfglrx-sources \
                usr/src
dh_install
# Driver package
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
cp: cannot stat `./usr/X11R6/bin/aticonfig': No such file or directory
dh_install: command returned error code 256
make: *** [binary] Error 1
/fglrx-install
Removing temporary directory: fglrx-install
```

is what I get when I attempt to run  "sudo ./ati-driver-installer-8.24.8-x86.run --buildpkg Ubuntu/dapper"

Doesn't seem like anybody else has had this problem.  
I've tried creating said directories, I've tried running it from /usr/src
Thanks:-D

---

### Post by que on 2006-10-06
All right, after running running the installer with no parameters, I realized it didn't list x.org 7, which I would assume is causing my problem.

How would I go about downgrading to x.org 6.9?

Would there be any reasons I wouldn't want to do that?

Regardless, I will never give ATI or Broadcom my business again, directly or indirectly.

---

