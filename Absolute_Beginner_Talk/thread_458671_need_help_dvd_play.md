---
title: "need help dvd play"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by leesway on 2007-05-29
Ok I installed 6.o6 LTS last night. So far its pretty cool. tonight I'm trying to get a dvd to play. Went to comunity docs and cut and pasted this to terminal.

wget [http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb

this is what I got when I entered.

(Reading database ... 79040 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2+build1 (using libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb) ...
Unpacking replacement libdvdcss2 ...
dpkg: dependency problems prevent configuration of libdvdcss2:
 libdvdcss2 depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
dpkg: error processing libdvdcss2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdvdcss2



Help please

---

### Post by kernel tom on 2007-05-29
if you follow the steps in the community help docs you should be fine 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by BoyOfDestiny on 2007-05-29
EDIT: Nevermind... Follow the link the poster above gave.

---

### Post by lahook on 2007-05-29
> **leesway said:**
> Ok I installed 6.o6 LTS last night. So far its pretty cool. tonight I'm trying to get a dvd to play. Went to comunity docs and cut and pasted this to terminal.

wget [http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb](http://medibuntu.sos-sts.com/repo/pool/feisty/free/i386/libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb

this is what I got when I entered.

(Reading database ... 79040 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu2+build1 (using libdvdcss2_1.2.9-2medibuntu2+build1_i386.deb) ...
Unpacking replacement libdvdcss2 ...
dpkg: dependency problems prevent configuration of libdvdcss2:
 libdvdcss2 depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
dpkg: error processing libdvdcss2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdvdcss2



Help please

see if a newer version of libc6 is available in your repositories
sudo apt-cache search libc6
if available install it
sudo apt-get install  libc6

then try and install it again, if more dependencies search and install them.
i hope this helps you out

---

