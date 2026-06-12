---
title: "Compiling on Ubuntu PPC"
date: 2007-07-16
forum: Apple PPC Users
---

### Post by SyB on 2007-07-16
Hi,

I guess that my previous post was not too clear.

I would like to port several Intel-Linux command-line programs that I have written to Ubuntu on PPC.
The gcc complier runs but I get error messages (file not found) for the C-language header files (stdio.h ... ) and the C-language libraries ( crt.lib, ...).

I have tried downloading "build-essential" using the package manager, but it fails on all seven packages.

Where can I find the C-language header (*.h) files and the C-language libraries (*.lib)?

Thanks in advance,

SyB

---

### Post by Tommy on 2007-07-16
If it fails on those packages, you have a problem in your sources. 

I suspect there is a bug in the Feisty PowerPC installer that (sometimes?) puts the wrong lines in /etc/apt/sources.list so the updates won't work.

Is that the version of Ubuntu you are running?

---

### Post by SyB on 2007-07-16
Hi,

Thanks for the reply.

I am running Edgy 6.10.  In an unrelated matter I had upgraded to Feisty 7.04 but the video crashed, so I had to reinstall 6.10.

SyB

---

### Post by Tommy on 2007-07-16
Please copy the contents of the file /etc/apt/sources.list and paste it in a message in this thread so I can see what it says. I'm not running Edgy (still stuck on Dapper with my oldworld hardware) but maybe the problem will be evident.

---

### Post by SyB on 2007-07-16
Hi,

Here are the contents of /etc/apt/sources.list

Thanks for the response.

SyB

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Tommy on 2007-07-16
Well, the good news is that looks correct. In fact, just to be sure, I copied it here and issued the ```
sudo apt-get update
``` command, and it apparently picked up all the repositories correctly. I did NOT try to install anything (as I have a Dapper system it might have gone crazy...) .

When you open a terminal and issue the ```
sudo apt-get update
``` command do you see any error messages? 

Do your other network services work correctly on that machine (can you open a browser and bring up Google, can you ping [www.ubuntu.com](www.ubuntu.com) etc.)?

---

### Post by SyB on 2007-07-17
Hi,

Networking works ok.  I can ping both the lan and the internet.

When I use the Synaptic package manager, I search for "build-essential" and tell it to install the seven packages.

I get the following error messages:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-11.38_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-11.38_powerpc.deb)
  Temporary failure resolving 'security.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.3_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.3_powerpc.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.1-13ubuntu5_powerpc.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.1/g++-4.1_4.1.1-13ubuntu5_powerpc.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g++_4.1.1-6ubuntu3_powerpc.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.13.22ubuntu7_all.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_11.3_powerpc.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'


Thanks again for the help.

SyB

---

### Post by SyB on 2007-07-17
Hi again,

I downloaded the seven files from the web sites and installed them manually.

The command-line programs seem to compile ok.

Many thanks again for the help.

SyB

---

### Post by Tommy on 2007-07-18
> **SyB said:**
> Hi,

Networking works ok.  I can ping both the lan and the internet.

When I use the Synaptic package manager, I search for "build-essential" and tell it to install the seven packages.

I get the following error messages:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-11.38_powerpc.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/linux-libc-dev_2.6.17.1-11.38_powerpc.deb)
  Temporary failure resolving 'security.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.3_powerpc.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12.3_powerpc.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'


You might make sure your network connection shows at least one DNS and preferably two. Left-click on the connection manager and bring up the connection information. If it doesn't look right (if you've never looked before you may not know -- but there should be something other than 0.0.0.0 for most of the entries).

If your DNS (name servers) look OK ... Try ```
ping -c 5 us.archive.ubuntu.com
``` and ```
ping -c 5 security.ubuntu.com
```. If ping does not fail, the updates should work afterward. (I'm not sure why it happens, but it's usually temporary, as it says.)

I'm glad you were able to get the packages installed "manually," but I hope you get the regular manager working because things like security updates are a big hassle to do manually.

---

