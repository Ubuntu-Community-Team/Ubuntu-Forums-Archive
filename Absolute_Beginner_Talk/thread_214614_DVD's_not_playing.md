---
title: "DVD's not playing"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by sanjito on 2006-07-12
When I try to play a DVD, it does not read the disc. I open totem and can not get to the DVD drive. I try to open the drive via compuer and get the folloing error:

Unable to mount the selected volume
> show more details
mount: no medium found

I do have the following installed if this helps any,

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-ffmpeg
libdvdread3

It can read data DVD's, but not movies. anything else I may try? Thanks in advance.

---

### Post by teet on 2006-07-12
Try clicking on System ==> Help ==> System Documentation.

Then click on Ubuntu Desktop Guide.  Then click on Common Tasks ==> Video.

Have you followed that guide for installing DVD support?

(I'm assuming you're running regular ubuntu and not kubuntu)

-teet

---

### Post by fredinator on 2006-07-12
try [easyubuntu]("http://easyubuntu.freecontrib.org/") to install DVD drivers

---

### Post by cow_racer on 2006-07-15
I have the exact same problem.

I used to be able to read DVD but after few updates I can't read DVD anymore.

---

### Post by arkangel on 2006-07-15
i never like  totem  ,  well that is my thing :) ....
try  with  Xine movie player (synaptic) or my  favorite over all  other media players  Mplayer(also syanptic but i strongly recommend  to recompile it yourself for  more format support )  both work nice and easy

---

### Post by kurniawands on 2006-07-15
got same problem with you guys, till i found that ubuntu (and other distro) needs something called "libdvdcss" which are no longer available to download. but after googling for sometime, i got this shell script. it works very well with kaffeine on my dapper 6.06.

here's the script (i just copy n paste it to my text editor, save it and launch it):

---------------------------------------------------------------------------


#!/bin/sh
# Shell script to install libdvdcss under Debian GNU Linux
# Many DVDs use css for encryption.  To play these discs, a special library 
# is needed to decode them, libdvdcss.  Due to legal problems, Debian and most
# Linux distibutions cannot distribute libdvdcss
# Use this shell script to install the libdvdcss under DEBIN GNU/Linux
# --------------------------------------------------------------------------
# Refer url for more info:
# Copyright info -  [http://www.dtek.chalmers.se/~dvd/](http://www.dtek.chalmers.se/~dvd/)
# -------------------------------------------------------------------------
# This script is part of nixCraft shell script collection (NSSC)
# Visit [http://bash.cyberciti.biz/](http://bash.cyberciti.biz/) for more information.
# -------------------------------------------------------------------------

set -e

site=http://www.dtek.chalmers.se/groups/dvd/deb/
arch=$(dpkg --print-installation-architecture)

soname=2
uversion=1.2.5
#available="alpha hppa i386 ia64 powerpc s390 sparc"
available="i386"
version=${uversion}-1

if ! type wget > /dev/null ; then
    echo "Install wget and run this script again"
    exit 1
fi

for a in $available; do
    if [  "$a" = "$arch" ]; then
	wget ${site}libdvdcss${soname}_${version}_${arch}.deb -O /tmp/libdvdcss.deb
	dpkg -i /tmp/libdvdcss.deb
	exit $?
    fi
done

echo "No binary deb available.  Will try to build and install it."
echo "You need to have debhelper, dpkg-dev and fakeroot installed."
echo "If not, interrupt now, install them and rerun this script."
echo ""
echo "This is higly experimental, look out for what happens below."
echo "If you want to stop, interrupt now (control-c), else press"
echo "return to proceed"
read dum

mkdir -p /tmp/dvd
cd /tmp/dvd
wget ${site}libdvdcss_${uversion}.orig.tar.gz
wget ${site}libdvdcss_${version}.diff.gz
wget ${site}libdvdcss_${version}.dsc
dpkg-source -x libdvdcss_${version}.dsc
cd libdvdcss-${uversion}
fakeroot ./debian/rules binary
echo "Any problems?  Interrupt now (control-c) and try to fix"
echo "manually, else go on and install (return)."
dpkg -i ../libdvdcss${soname}_${version}_${arch}.deb

---------------------------------------------------------------------------

open your terminal, do this:

sudo sh yourscriptfile

and wait till it's done. that's it... just that easy, at least for me as someone who just experience ubuntu or supposed to say linux couple days ago hehehehehe.... peace...

---

### Post by orb9220 on 2006-07-15
That's funny I just looked in synaptic and it's there.

libdvdcss2

a portable abstraction library for DVD decryption
libdvdcss is a portable abstraction library for DVD decryption, it
provides a simple API to access a DVD device as a block device.

This package contains the libdvdcss2 runtime library.

Make sure all your reposotories are selected tho.

Plus I just use easyubuntu and it installs flash,java,audio & Video codecs, and on and on. It should be the first thing after a fresh insall.

---

### Post by crispy_420 on 2006-07-15
libdvdcss is in there if you add those repositories. Just keep in mind the legal issues of use in some countries (USA).

---

### Post by tx1138 on 2006-07-15
I installed easyubuntu and totem still doesn't read dvd's :S It finished downloading everything, but it didn't tell me where it installed anything :S

---

### Post by kurniawands on 2006-07-16
> **orb9220 said:**
> That's funny I just looked in synaptic and it's there.

libdvdcss2

a portable abstraction library for DVD decryption
libdvdcss is a portable abstraction library for DVD decryption, it
provides a simple API to access a DVD device as a block device.

This package contains the libdvdcss2 runtime library.

Make sure all your reposotories are selected tho.

Plus I just use easyubuntu and it installs flash,java,audio & Video codecs, and on and on. It should be the first thing after a fresh insall.

fyi, libdvdcss is no longer available on ubuntu's resources, don't believe me ? ask any body who just install ubuntu... i.e. my self. easyubuntu can't do it since the source is no longer there. I got that libdvdcss2 from "http://www.dtek.chalmers.se/~dvd/" and install it using above shell script... that's true..

---

### Post by crispy_420 on 2006-07-16
PLF repositories:

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

---

### Post by Uncle Spellbinder on 2006-07-16
I installed, and used,  [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646") and haven't looked back. DVD's play just fine.

---

### Post by Uncle Spellbinder on 2006-07-16
> **crispy_420 said:**
> PLF repositories:

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free


I've had problems with *PLF repositories*. They have not worked at all for me: 

The above link, **404 - NOT FOUND**.

---

### Post by crispy_420 on 2006-07-16
> The above link, 404 - NOT FOUND.

I just noticed that myself. Maybe they are just down temporarly.

---

### Post by Uncle Spellbinder on 2006-07-16
> **crispy_420 said:**
> I just noticed that myself. Maybe they are just down temporarly.

It's been that way for over a week, in my case.

---

### Post by deadgobby on 2006-07-16
I would agree to install Automatic by the Beerorkid. All hail beer or kid. Just bear in mind. After the a upgrade to the next Ubie. The codec will be whipe out. Cause you may live in a no no country and you can't have them unless you pay for the codecs.

---

