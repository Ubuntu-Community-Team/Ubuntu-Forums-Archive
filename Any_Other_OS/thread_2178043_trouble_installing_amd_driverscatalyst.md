---
title: "trouble installing amd drivers/catalyst"
date: 2013-10-01
forum: Any Other OS
---

### Post by ac1d2 on 2013-10-01
tried running the installer direct from amd's website, and came out with errors.
this is what spits outs after entering amdcccle in the command line. 

[COLOR=#333333][FONT=Lucida Grande]amdcccle: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS32 [/FONT][/COLOR]

Scanned around on the web for a while looking for a different method of install and found this

[COLOR=#000000]./ati-driver-installer-8.37.6-x86.x86_64.run --buildpkg RedHat/RHEL5[/COLOR]
[COLOR=#000000]./ati-driver-installer-8.37.6-x86.x86_64.run --buildpkg RedHat/RHEL5_64a[/COLOR]
[COLOR=#000000]rpm -ivh fglrx_7_1_0-8.37.6-1.i386.rpm[/COLOR]
[COLOR=#000000]rpm -ivh fglrx64_7_1_0-8.37.6-1.x86_64.rpm --nodeps[/COLOR]

I've completely purged all of my amd drivers, fglrx & xorg.conf. I just reconfigured xorg.conf but am having issues getting this command to go through. Truthfully I'm not even sure if its the correct way to do the install but it seems to make sense seeing as I'm having issues with my 32/64 libs, and yes I made sure to install all of my 32 libs so that's not the issue.

Anyway this is what spits out when trying to enter the command:

[COLOR=#000000][FONT=Lucida Grande]root@D3B1AN:/home/ac1d/Downloads# ./amd-driver-installer-catalyst-13-4-x86.x86_64.run --buildpkg RedHat/RHEL5[/FONT][/COLOR]
[COLOR=#000000][FONT=Lucida Grande]bash: ./amd-driver-installer-catalyst-13-4-x86.x86_64.run: Permission denied[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]





[/FONT][/COLOR]

---

### Post by Mark Phelps on 2013-10-01
Ubuntu doesn't use rpms; instead, it uses .deb files.  You're making the wrong drivers.

What make and model AMD video chipset are you using? And, what version of Ubuntu are you running?

---

### Post by Yellow Pasque on 2013-10-01
> root@D3B1AN
So you're running Debian, trying to build .rpm's for RedHat, and asking for help on Ubuntuforums? Interesting...

---

### Post by ac1d2 on 2013-10-01
I have 2 pcs, one debian, one ubuntu/win7. Debian forums dont have a great user base. So I ask here, linux is linux. There might be small nuances but its all roughly the same.

I ran buildpkg on redhat due to there being no debian support in the amd drivers.

---

### Post by Yellow Pasque on 2013-10-01
What release/branch/kernel of Debian are you running and what is your GPU?

---

### Post by ac1d2 on 2013-10-01
Debian Packages:
	Debian/sid
	Debian/unstable
	Debian/etch
	Debian/stable
	Debian/lenny
	Debian/testing
	Debian/experimental


no Debian/wheezy so I tried Debian/stable and that didn't work, so I gave redhat a try....not really sure why to be honest

---

### Post by ac1d2 on 2013-10-01
running 5 monitors, 2 gpu's 1-5450 & 1-5870. Running Debian/wheezy

root@D3B1AN:/home/ac1d# uname -r
3.2.0-4-amd64

---

### Post by Yellow Pasque on 2013-10-01
fglrx 8.37.6 is ancient (and older than what wheezy offers in its repo). I'm not really sure what you're trying to do or what version you're trying to install...
[https://wiki.debian.org/ATIProprietary#Debian_7_.22Wheezy.22](https://wiki.debian.org/ATIProprietary#Debian_7_.22Wheezy.22)

---

### Post by ac1d2 on 2013-10-01
fglrx 8.37.6? How did you come up with that?

I'm simply trying to get amd catalyst to work.

---

### Post by QIII on 2013-10-01
*Moved to **Other OS/Distro Support***

---

### Post by Yellow Pasque on 2013-10-01
> **ac1d2 said:**
> fglrx 8.37.6? How did you come up with that?

You used it as an example in your first post, though I guess that was the guide you were following. Anyway...

Get prerequisites:
```
sudo apt-get install build-essential cdbs dh-make dkms execstack dh-modaliases linux-headers-generic fakeroot libqtgui4 devscripts lib32gcc1
```

Since you already have the .run file ready to go, make it executable and that should allow you to run it.
```
chmod +x amd-catalyst-13.4-linux-x86.x86_64.run
```

---

### Post by ac1d2 on 2013-10-02
I just used sh to run it last time, worked like a charm. Aside from the libs issues. Since its a x86/64 package I want to install the x86 first then the 64. Wondering how can I do multiple installs off of the same file? Was hoping this was going to work but no-go.

> root@D3B1AN:/home/ac1d/Downloads# sh amd-driver-installer-catalyst-13-4-x86.x86_64.run --buildpkg Debian/stable
Created directory fglrx-install.Tw5CX0
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-12.104....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Debian/stable
cp: cannot stat `/home/ac1d/Downloads/fglrx-install.Tw5CX0/x710_64a/*': No such file or directory
Package build failed!
Package build utility output:
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 12.104-1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.JupB9b
dpkg-buildpackage: host architecture amd64
 debian/rules build
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
find: `usr/X11R6/include': No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# set proper permissions on /etc files
if [ -d etc/ati ]; then            \
        chmod 755 etc/ati ;            \
        chmod 644 etc/ati/* ;        \
        chmod a+x etc/ati/*.sh ;    \
    fi
if [ -f debian/fglrx.default ]; then \
      mv -v debian/fglrx.default debian/fglrx; \
    fi
`debian/fglrx.default' -> `debian/fglrx'
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
 debian/rules binary
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
find: `usr/X11R6/include': No such file or directory
find lib -not -name "*.sh" -type f | xargs chmod -x
find lib      -name "*.sh" -type f | xargs chmod +x
# set proper permissions on /etc files
if [ -d etc/ati ]; then            \
        chmod 755 etc/ati ;            \
        chmod 644 etc/ati/* ;        \
        chmod a+x etc/ati/*.sh ;    \
    fi
if [ -f debian/fglrx.default ]; then \
      mv -v debian/fglrx.default debian/fglrx; \
    fi
# remove exec bit from 64-bit libs too
find usr/X11R6/lib64       -type f | xargs chmod -x
dh_testdir
dh_testroot
dh_clean -k
dh_clean: dh_clean -k is deprecated; use dh_prep instead
dh_clean: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
# Create the directories to install into
dh_installdirs -pfglrx-driver \
        usr \
        usr/lib/xorg \
        usr/lib/xorg/modules \
        usr/lib/dri \
        usr/bin \
        usr/sbin \
        etc/acpi \
        etc/acpi/events \
        etc/default \
        etc/X11/Xsession.d
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
# the amd64 package includes 32bit compatibility libraries
dh_installdirs -pfglrx-driver \
        emul/ia32-linux/usr/lib \
        emul/ia32-linux/usr/lib/xorg \
        emul/ia32-linux/usr/lib/xorg/modules \
        emul/ia32-linux/usr/lib/dri
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -pfglrx-driver-dev \
        usr \
        usr/include \
        usr/lib
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -pfglrx-kernel-src \
        usr/src/modules/fglrx \
        usr/src/modules/fglrx/debian
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -A -pfglrx-amdcccle \
        usr \
        usr/bin \
        usr/share \
        usr/share/applnk \
        usr/share/applications \
        usr/share/icons \
        usr/share/pixmaps
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installdirs -p \
        usr/src
dh_installdirs: Compatibility levels before 5 are deprecated (level 4 in use)
dh_install
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
dh_install -pfglrx-driver "usr/X11R6/bin/fgl*"      "usr/bin"
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
dh_install -pfglrx-driver "usr/X11R6/bin/aticonfig" "usr/bin"
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
dh_install -pfglrx-driver "usr/sbin/atieventsd"     "usr/sbin"
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
dh_installman -pfglrx-driver "usr/share/man/man8/atieventsd.8"
dh_installman: Compatibility levels before 5 are deprecated (level 4 in use)
# amd64 needs some library redirection
dh_install -pfglrx-driver "usr/X11R6/lib64/*.so*"           "usr/lib"
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
dh_install -pfglrx-driver "usr/X11R6/lib64/modules/dri"     "usr/lib"
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
dh_install -pfglrx-driver "usr/X11R6/lib64/modules/linux"   "usr/lib/xorg/modules"
dh_install: Compatibility levels before 5 are deprecated (level 4 in use)
cp: cannot stat `./usr/X11R6/lib64/modules/linux': No such file or directory
dh_install: cp -a ./usr/X11R6/lib64/modules/linux debian/fglrx-driver/usr/lib/xorg/modules/ returned exit code 1
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.Tw5CX0




---

### Post by Yellow Pasque on 2013-10-02
Comments on the Debian page of the AMD/ATI wiki report package generation is broken. I still don't understand what you're trying to do. Use the fglrx package in the Debian repo...

---

