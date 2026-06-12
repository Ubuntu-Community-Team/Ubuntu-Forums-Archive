---
title: "ZIMBRA in server 7.04"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by januka on 2007-09-11
HI ,,,,,,,,, I'm trying to install ZIMBRA server on ubuntu server 7.04. But there is no release on zimbra for server 7.04 but they have it for 6.10 i think.......
Even though i have installed the  prerequisite module as most documentation on the web, i still getting these errors.

 ./install.sh

Operations logged to /tmp/install.log.7321
Checking for existing installation...
    zimbra-ldap...NOT FOUND
    zimbra-logger...NOT FOUND
    zimbra-mta...NOT FOUND
    zimbra-snmp...NOT FOUND
    zimbra-store...NOT FOUND
    zimbra-apache...NOT FOUND
    zimbra-spell...NOT FOUND
    zimbra-core...NOT FOUND
./util/utilfunc.sh: line 381: rpm: command not found


PLEASE READ THIS AGREEMENT CAREFULLY BEFORE USING THE SOFTWARE.
ZIMBRA, INC. ("ZIMBRA") WILL ONLY LICENSE THIS SOFTWARE TO YOU IF YOU
FIRST ACCEPT THE TERMS OF THIS AGREEMENT. BY DOWNLOADING OR INSTALLING
THE SOFTWARE, OR USING THE PRODUCT, YOU ARE CONSENTING TO BE BOUND BY
THIS AGREEMENT. IF YOU DO NOT AGREE TO ALL OF THE TERMS OF THIS
AGREEMENT, THEN DO NOT DOWNLOAD, INSTALL OR USE THE PRODUCT.

License Terms for the Zimbra Collaboration Suite:
        [http://www.zimbra.com/license/collaboration_suite_collective_license_1.0.html](http://www.zimbra.com/license/collaboration_suite_collective_license_1.0.html)


Press Return to continue

Checking for prerequisites...
    NPTL...FOUND
    sudo...MISSING
    libidn...MISSING
    curl...MISSING
    fetchmail...MISSING
    gmp...MISSING
    /usr/lib/libstdc++.so.5...MISSING

###ERROR###

One or more prerequisite packages are missing.
Please install them before running this installer.

Installation cancelled.


Can any-body help me the way to over come this problem ..............

Cheers 

januka:confused:

---

### Post by nick_nitro on 2007-09-11
from the zimbra forums:

Workarounds for Ubuntu 7.04 Feisty
sudo apt-get install fetchmail # this is needed anyway, seems to be only thing missing with default feisty install

then either:

1) edit /etc/lsb-release
change
DISTRIB_RELEASE=7.04
to
DISTRIB_RELEASE=6

or

2)
edit util/utilfunc.sh
change
if [ $PLATFORM = "DEBIAN3.1" -o $PLATFORM = "UBUNTU6" ]; then
to
if [ $PLATFORM = "DEBIAN3.1" -o $PLATFORM = "UBUNTU6" -o $PLATFORM = "UBUNTUUNKNOWN" ]; then

change
if [ $PLATFORM = "UBUNTU6" ]; then
to
if [ $PLATFORM = "UBUNTU6" -o $PLATFORM = "UBUNTUUNKNOWN" ]; then

edit
util/modules/platform.sh
change
if [ $PLATFORM = "DEBIAN3.1" -o $PLATFORM = "MANDRIVA2006" -o $PLATFORM = "UBUNTU6" ]; then
to
if [ $PLATFORM = "DEBIAN3.1" -o $PLATFORM = "MANDRIVA2006" -o $PLATFORM = "UBUNTU6" -o $PLATFORM = "UBUNTUUNKNOWN" ]; then

they both do pretty much same thing so 1) is easier, just change it back when install finished.

As usual, this is not recommended for production servers! YMMV.

---

### Post by januka on 2007-09-11
Thankx a lot

---

### Post by jimbo99 on 2007-10-17
> **nick_nitro said:**
> from the zimbra forums:

Workarounds for Ubuntu 7.04 Feisty
sudo apt-get install fetchmail # this is needed anyway, seems to be only thing missing with default feisty install

......
......
......

As usual, this is not recommended for production servers! YMMV.

What does this last sentence really mean?

---

### Post by haxor999 on 2008-02-08
Production server = mission critical server that is running applications whose interruption would mean immediate financial loss to a company

The reason for that footnote is that the steps detailed above have not been officially endorsed/approved by Zimbra so you take them at your own risk.

---

