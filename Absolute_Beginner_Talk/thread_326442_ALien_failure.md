---
title: "ALien failure"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by OpenUser1 on 2006-12-27
Hi ALl,

I need to install a rpm pkg for a program for work.  Alien is failing with :
" <snip>
.
.
chmod 644 ITvpnclient-4.6_JDS//usr/src/vpnclient-4.6/vpn_ioctl_linux.h
        chown 0:0 ITvpnclient-4.6_JDS//usr/src/vpnclient-4.6/vpnmod_build
        chmod 755 ITvpnclient-4.6_JDS//usr/src/vpnclient-4.6/vpnmod_build
        mkdir ITvpnclient-4.6_JDS/debian
        hostname -f
        822-date
        hostname -f
        822-date
        chmod 755 ITvpnclient-4.6_JDS/debian/rules
        debian/rules binary 2>&1
Use of uninitialized value in die at /usr/share/perl5/Alien/Package/Deb.pm line 488, <GETPERMS> line 58.
Package build failed. Here's the log:
        find ITvpnclient-4.6_JDS -type d -exec chmod 755 {} ;
find: ITvpnclient-4.6_JDS: No such file or directory
        rm -rf ITvpnclient-4.6_JDS
"

little help ?

Thanks.

---

