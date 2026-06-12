---
title: "Running ATI installer..."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by eks on 2007-05-18
This is certainly really simple but is driving me nuts. (Resumed question bolded at the end :))

I'm trying both the [official]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.36.5-inst.html") and [unnofficial]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") commands to install ATI driver:

```

 sh ./ati-driver-installer-8.36.5.run

```
and
```

sudo bash ati-driver-installer-8.36.5-x86.x86_64.run --buildpkg Ubuntu/feisty

```

Which gives me:
```

Detected version of X does not have a matching 'x720_64a' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]
The following values may be used for <xdir>:
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit

```

Then, when I type:
```

X_VERSION=x710_64a ./ati-driver-installer-8.36.5-x86.x86_64.run --install

```

I obviusly get Permission denied. I'm not root, just a user that has to use sudo. Which in turn gives me this:
```

~/Desktop/ati$ sudo X_VERSION=x710_64a ./ati-driver-installer-8.36.5-x86.x86_64.run --install
sudo: X_VERSION=x710_64a: command not found

```

For some amazingly unexplained reason, ati drivers seems to need the flags BEFORE calling the program :confused:. **How do I call the program and the flag with super user permissions?**


Thanks a lot!
eks

---

### Post by Bachstelze on 2007-05-18
I think it would make your life easier if you did that when logged in as real root, not with sudo. To login as root, just do *sudo -i*.

---

### Post by krisfrajer on 2007-05-18
couldnt you start a superuser shell?

sudo -i

---

### Post by Bachstelze on 2007-05-18
I win :p

---

### Post by eks on 2007-05-18
I was going to scream ARGH THANK YOU because it would obviously work, but now I'm baffled and :confused::

```

root@domub:/home/eks/Desktop/ati# sh X_VERSION=x710_64a ./ati-driver-installer-8.36.5-x86.x86_64.run --install
sh: Can't open X_VERSION=x710_64a

root@domub:/home/eks/Desktop/ati# X_VERSION=x710_64a ./ati-driver-installer-8.36.5-x86.x86_64.run --install
-bash: ./ati-driver-installer-8.36.5-x86.x86_64.run: Permission denied

```

How can root have Permission denied??

---

### Post by H4rm0ny on 2008-05-23
Hi eks,

Did you get anywhere with resolving this? I have just had the same problem - permission denied when I run this:

```
sudo sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy
```

I've tried variations such as running it in a shell started by root, as root, etc. Didn't work and I didn't expect it to. There's something more fundamental going on here.

H.

---

### Post by reggaedaddy on 2008-06-11
I'm stuck with this too... in a root shell...

When i entered:

```
sh ati-driver-installer-8-5-x86.x86_64.run --buildpkg Ubuntu/hardy
```


it gave me back:

```

Created directory fglrx-install.A11556
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.493.1...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/hardy
Package build failed!
Package build utility output:
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.493.1-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 debian/rules build
dpkg-buildpackage: host architecture amd64
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.K11639/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.K11639/debian/driver.$i > \
	      /tmp/fglrx.K11639/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.K11639/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.K11639/debian/10fglrx.template > /tmp/fglrx.K11639/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.K11639/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.K11639/debian/fglrx.default /tmp/fglrx.K11639/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
 debian/rules binary
echo "Using architecture: amd64"
Using architecture: amd64
for i in preinst postinst postrm shlibs atieventsd.init ; do \
	  if [ -f /tmp/fglrx.K11639/debian/driver.$i ]; then \
	    sed -e "s/#PKGNAME#/xorg-driver-fglrx/" \
	        -e "s/#DISTRO#/hardy/" /tmp/fglrx.K11639/debian/driver.$i > \
	      /tmp/fglrx.K11639/debian/xorg-driver-fglrx.$i; \
	  fi; \
	done
if [ -f /tmp/fglrx.K11639/debian/10fglrx.template ]; then \
	  sed -e "s|#XMODDIR#|usr/lib|" -e "s|#XMODDIR32#|usr/lib32|" \
	    /tmp/fglrx.K11639/debian/10fglrx.template > /tmp/fglrx.K11639/debian/10fglrx; \
	fi
if [ -f /tmp/fglrx.K11639/debian/fglrx.default ]; then \
	  mv /tmp/fglrx.K11639/debian/fglrx.default /tmp/fglrx.K11639/debian/fglrx; \
	fi
dh_testdir
dh_testdir
# move licenses away from binary dir
if [ ! -d usr/share/doc/fglrx ]; then \
		mkdir -p usr/share/doc/fglrx; \
		mv usr/X11R6/bin/LICENSE.* usr/share/doc/fglrx; \
	fi
# set executable on user apps
find usr/X11R6/bin -type f | xargs chmod a+x
# remove exec bit from files that don't deserve it
find usr/X11R6/include \
		usr/X11R6/lib \
		usr/X11R6/lib64 \
		usr/share usr/src     -type f | xargs chmod -x
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testdir
dh_testroot
dh_clean -k
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
# Create the directories to install into
dh_installdirs -pxorg-driver-fglrx \
		usr/lib \
		usr/sbin \
		usr/lib \
		usr/lib/xorg/modules \
		usr/lib/xorg/modules/drivers \
		usr/lib/xorg/modules/linux \
		etc/acpi \
		etc/acpi/events \
		etc/default \
		etc/X11/Xsession.d \

# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pxorg-driver-fglrx \
		usr/lib32 \
		usr/lib32
dh_installdirs -A -pxorg-driver-fglrx \
		usr/bin \
		usr/sbin \
		usr/share \
		usr/share/applnk \
		usr/share/gnome \
		usr/share/gnome/apps \
		usr/share/icons \
		usr/share/pixmaps
dh_installdirs -pxorg-driver-fglrx-dev \
		usr/include \
		usr/lib
dh_installdirs -pfglrx-kernel-source \
		usr/src/fglrx-8.493.1
dh_install
# Driver package
/sbin/ldconfig -n usr/X11R6/lib/
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install -pxorg-driver-fglrx "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install -pxorg-driver-fglrx "usr/sbin/atieventsd"     "usr/sbin"
dh_installman -pxorg-driver-fglrx "usr/share/man/man8/atieventsd.8"
# amd64 needs some library redirection
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/drivers" "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.so"    "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib64/modules/*.a"     "usr/lib/xorg/modules"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/*.so*"           "usr/lib32"
dh_install -pxorg-driver-fglrx "usr/X11R6/lib/modules/dri"     "usr/lib32"
dh_install -pxorg-driver-fglrx "etc/ati"                   "etc"
dh_install -pxorg-driver-fglrx "debian/10fglrx"            "etc/X11/Xsession.d"
dh_install -pxorg-driver-fglrx "debian/fglrx-powermode.sh" "etc/acpi"
dh_install -pxorg-driver-fglrx "debian/fglrx-*-aticonfig"  "etc/acpi/events"
dh_install -pxorg-driver-fglrx "debian/fglrx"              "etc/default"
dh_installinit -pxorg-driver-fglrx --name="atieventsd"
# Driver dev package
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/lib64/*.a" "usr/lib"
dh_install -pxorg-driver-fglrx-dev "usr/X11R6/include/*" "usr/include"
dh_install -pxorg-driver-fglrx-dev "usr/include/*"       "usr/include"
#Create dkms.conf
echo "PACKAGE_NAME=\"fglrx\"" > debian/dkms.conf
echo "PACKAGE_VERSION=\"8.493.1\"" >> debian/dkms.conf
echo "CLEAN=\"rm -f *.*o\"" >> debian/dkms.conf
echo "BUILT_MODULE_NAME[0]=\"fglrx\"" >> debian/dkms.conf
echo "MAKE[0]=\"pushd \${dkms_tree}/fglrx/8.493.1/build; sh make.sh --nohints; popd\"" >> debian/dkms.conf
echo "DEST_MODULE_LOCATION[0]=\"/kernel/drivers/char/drm\"" >> debian/dkms.conf
echo "AUTOINSTALL=\"yes\"" >> debian/dkms.conf
# Kernel source package
dh_install -pfglrx-kernel-source \
		lib/modules/fglrx/build_mod/*.c            \
		lib/modules/fglrx/build_mod/*.h            \
		lib/modules/fglrx/build_mod/*.sh           \
		lib/modules/fglrx/build_mod/lib*           \
		lib/modules/fglrx/build_mod/2.6.x/Makefile \
		debian/dkms.conf			   \
		usr/src/fglrx-8.493.1
# control panel package
dh_install -A -pfglrx-amdcccle "usr/X11R6/bin/amdcccle"				"usr/bin"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/icons"
dh_install -A -pfglrx-amdcccle "usr/share/icons/*.xpm"				"usr/share/pixmaps"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.desktop"			"usr/share/applications"
dh_install -A -pfglrx-amdcccle "debian/amdcccle.kdelnk"				"usr/share/applnk"
dh_install -A -pfglrx-amdcccle "usr/share/ati"					"usr/share"
dh_desktop    -pfglrx-amdcccle
# start the install
dh_installdocs
dh_installdocs -pxorg-driver-fglrx usr/share/doc/fglrx/*
#dh_installchangelogs
dh_link
dh_strip
dh_compress
dh_installdeb
dh_makeshlibs
dh_shlibdeps
dpkg-shlibdeps: warning: symbol XauFileName used by debian/xorg-driver-fglrx/usr/sbin/atieventsd found in none of the libraries.
dpkg-shlibdeps: warning: debian/xorg-driver-fglrx/usr/sbin/atieventsd shouldn't be linked with libXrender.so.1 (it uses none of its symbols).
dpkg-shlibdeps: failure: couldn't find library libfglrx_gamma.so.1 needed by debian/xorg-driver-fglrx/usr/bin/fglrx_xgamma (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: *** [binary] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.A11556

```

And failed.  Any suggestions would be VERY appreciated.

THANKS!

---

### Post by archat68 on 2008-06-28
I'm a newbie. 
I'm getting sh: Can't open ati-driver-installer-8-6-x86.x86_64.run
What should I do?
Please help.

---

### Post by screaminj3sus on 2008-07-02
same problem here root shell does nothing to fix it. this is ridiculous

---

### Post by screaminj3sus on 2008-07-02
randomly got it to work by opening the root shell, dragging the .run file I downloaded into the terminal window and adding --buildpkg Ubuntu/hardy at the end

---

### Post by jasonkostempski on 2008-07-12
Happened to me too. Try:

Right Click File -> Properties -> Permissions -> Allow executing file as program

---

