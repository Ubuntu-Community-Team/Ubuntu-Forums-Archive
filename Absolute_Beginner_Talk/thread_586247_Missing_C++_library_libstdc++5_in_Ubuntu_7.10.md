---
title: "Missing C++ library libstdc++5 in Ubuntu 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-10-22
Hi,
I have successfully installed Ubuntu 7.10 and I would like to install IBM DB2 Express-C v9.1.2 database. But requirements for DB2 is installing libstdc++5 library. In Ubuntu 7.10 there is library libstdc++6 but there is no libstdc++5.

Trying to install this package by command:
```

sudo apt-get update
sudo apt-get install libstdc++5

```
returns error:
-----------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
-----------------------

How to install libstdc+5? Do I need to enable some kind of external data source? Any help is appreciated.

Thanks,
Abcuser

---

### Post by abcuser on 2007-10-22
Hi,
I have solved the problem. It looks like DB2 is using an old version of libstdc++.so.5 library. So this library has to be installed manually. I did the following:
```

# change directory to /tmp directory:
cd /tmp/

# download deb package:
wget -c http://lug.mtu.edu/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb

# unpack deb package to get library file
dpkg -x libstdc++5_3.3.6-13ubuntu2_i386.deb libstdc++5

# copy library file to /usr/bin directory
sudo cp libstdc++5/usr/lib/libstdc++.so.5.0.7 /usr/lib

# change directory to /usr/lib directory
cd /usr/lib

# create simbolic link to library
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

# install db2
cd /path (Note: change directory to db2setup file)
sudo ./db2setup

```

Thanks,
Abcuser

---

### Post by Skip Da Shu on 2007-11-23
> **abcuser said:**
> Hi,
I have solved the problem. It looks like DB2 is using an old version of libstdc++.so.5 library. So this library has to be installed manually. I did the following:
```

# change directory to /tmp directory:
cd /tmp/

# download deb package:
wget -c http://lug.mtu.edu/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb

# unpack deb package to get library file
dpkg -x libstdc++5_3.3.6-13ubuntu2_i386.deb libstdc++5

# copy library file to /usr/bin directory
sudo cp libstdc++5/usr/lib/libstdc++.so.5.0.7 /usr/lib

# change directory to /usr/lib directory
cd /usr/lib

# create simbolic link to library
sudo ln -s libstdc++.so.5.0.7 libstdc++.so.5

# install db2
cd /path (Note: change directory to db2setup file)
sudo ./db2setup

```

Thanks,
Abcuser

Please excuse the noob level of ignorance here but...

A couple applications I wanna run get an error like this:
```
Fri 23 Nov 2007 02:23:49 PM CST|Leiden Classical|Reason: Unrecoverable error for result wu_1193755502_15807_0 (process exited with code 127 (0x7f, -129))
Fri 23 Nov 2007 02:19:06 PM CST|QMC@HOME|Reason: Unrecoverable error for result two_adb_anthracene.2094_0 (process exited with code 127 (0x7f, -129))

```

I believe this to be due to them wanting libstc++.so.5 perhaps as shown here:```

/var/lib/boinc-client/projects/qah.uni-muenster.de$ ldd Amolqc-preRC1-501
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f12000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7efa000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7eee000)
        libstdc++.so.5 => not found
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ed6000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7eb1000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d67000)
        /lib/ld-linux.so.2 (0xb7f22000)
```
So I am thinking the first 6 of the 7 steps listed above may be a solution for me.

I am assuming that I can ignore the 7th step since the actual application modules getting the error are downloaded as binaries and executed on demand by a controlling 'core client'.  

Am I way off base?  close?  or have I guessed my way into a solution with your excellent clear directions?

If I install 64bit Gutsy on another machine running the same application I assume I would have to find a replacement lib for anything above that has "386" in it?

Thanx, Skip

---

### Post by Skip Da Shu on 2007-11-23
> **Skip Da Shu said:**
> Please excuse the noob level of ignorance here but...

A couple applications I wanna run get an error like this:
```
Fri 23 Nov 2007 02:23:49 PM CST|Leiden Classical|Reason: Unrecoverable error for result wu_1193755502_15807_0 (process exited with code 127 (0x7f, -129))
Fri 23 Nov 2007 02:19:06 PM CST|QMC@HOME|Reason: Unrecoverable error for result two_adb_anthracene.2094_0 (process exited with code 127 (0x7f, -129))

```

I believe this to be due to them wanting libstc++.so.5 perhaps as shown here:```

/var/lib/boinc-client/projects/qah.uni-muenster.de$ ldd Amolqc-preRC1-501
        linux-gate.so.1 =>  (0xffffe000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f12000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7efa000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7eee000)
        libstdc++.so.5 => not found
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ed6000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7eb1000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d67000)
        /lib/ld-linux.so.2 (0xb7f22000)
```
So I am thinking the first 6 of the 7 steps listed above may be a solution for me.

I am assuming that I can ignore the 7th step since the actual application modules getting the error are downloaded as binaries and executed on demand by a controlling 'core client'.  

Am I way off base?  close?  or have I guessed my way into a solution with your excellent clear directions?

If I install 64bit Gutsy on another machine running the same application I assume I would have to find a replacement lib for anything above that has "386" in it?

Thanx, Skip

Hey IT WORKED!  I am a VERY happy camper.  Ubuntu uber alles!

The only thing I did different from the listed steps 1 thru 6 was at step 2.  
```
wget -c http://lug.mtu.edu/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb
```

This got to mtu but then seemed to hang "waiting for response" for several minutes so I ^c'd it and went to **[http://mirror.ne.gov/ubuntu/pool/main/g/gcc-3.3/](http://mirror.ne.gov/ubuntu/pool/main/g/gcc-3.3/)** in firefox and downloaded [ **THIS**]("http://mirror.ne.gov/ubuntu/pool/main/g/gcc-3.3/libstdc++5_3.3.6-13ubuntu2_i386.deb") to my user directory and then copied it to /tmp.  From there I resumed with step #3.

All is good and in that mirror index I saw the AMD64 versions of the libs for my next machine that I'll be converting over from winXP to Gutsy 64bit.

Thank ya'll SO much this was a major deal for me as these machines only purpose in life is to run these apps.

Skip

---

