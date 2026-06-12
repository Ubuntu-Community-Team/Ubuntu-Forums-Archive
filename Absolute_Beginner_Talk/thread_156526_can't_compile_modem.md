---
title: "can't compile modem"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by dksdk on 2006-04-07
hi i am a newbie to ubuntu. i installed ubuntu 5.10 last week and i am dual booting with win xp home on sony vaio at the moment. ubuntu does'nt recognise my modem. so after going through the forum and other ubuntu support sites i ran a scan modem. it says that i have a ALiM5457 AC'97 Modem which is capable of supporting soft modems- agere systems, conexant& smartlink. so i downloaded slmodems 2.9.10 tar diff and dsc along with others like gcc3.4, fake root, linux headers 2.6.12.9.386. but i am not able to compile the modem. i read in the forum about changing your gcc to 3.4. i tried it it gives me this error  
:~$ sudo apt-get update
Ign file: ./ Release.gpg
Ign file: ./ Release
Ign file: ./ Packages
Err file: ./ Packages
  File not found
Failed to fetch file:///home/sree/gcc-3.4/./Packages.gz  File not found
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/_home_sree_gcc-3.4_._Packages
E: The package lists or status file could not be parsed or opened.

pl help

---

### Post by htinn on 2006-04-07
I think you're going to need to use "sudo dpkg -i packagename.deb" to install your packages.

---

### Post by Matchless on 2006-04-08
Hi,
   I suggest you go to the Wiki, seach for Dialupmodemhowto, the preliminaries right up to compling the driver is what you should do.

---

### Post by Sef on 2006-04-08
Did you download build-essential? Without it you can't compile.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by psibaboon on 2006-04-08
I'm not sure about laptop modems, but if your modem has a Conexant chipset, you might want to try drivers from Linuxant. They have Breezy-specific .debs on their website.

---

### Post by dksdk on 2006-04-09
hi thank you very much. in the meantime i managed to install build essential, linux headers and gcc3.4. i thought i compiled the sl-modem and sl-modem demon. but when i start wvdial i get this message and if try to restart the demon it does'nt work
sree@ubuntumaruti:~$ sudo wvdial
Password:
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
sree@ubuntumaruti:~$ sudo /etc/init.d/sl-modem-daemon restart
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Unloading modem driver from kernel ... slamr.
Starting SmartLink Modem driver for: slamr0.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
sree@ubuntumaruti:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
what have i done wrong
pl help.
should i try linuxant drivers

---

### Post by dksdk on 2006-04-10
hi i gave up on installing slmodems and installed linuxant driver which installed ok.there is a dialing tone and it dials but can not establish a connection.
but i presume that to dial a AOL account u need a pengaol.
so i downloaded and tried to recompile but it is refusing to install. it is giving me this error message
sree@ubuntumaruti:~$ cd linux
sree@ubuntumaruti:~/linux$ cd peng
sree@ubuntumaruti:~/linux/peng$ make
make  all-recursive
make[1]: Entering directory `/home/sree/linux/peng'
Making all in peng
make[2]: Entering directory `/home/sree/linux/peng/peng'
g++ -DHAVE_CONFIG_H -I. -I. -I..     -D_REENTRANT -c threadELV3.cpp
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from cclienttoaol30.h:24,
                 from kernel30.h:50,
                 from caolcmd30.h:22,
                 from threadELV3.h:24,
                 from threadELV3.cpp:21:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
kernel30.h:226: error: ISO C++ forbids declaration of â&#8364;&#732;CAolCmd30â&#8364;&#8482; with no type
kernel30.h:226: error: expected â&#8364;&#732;;â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
make[2]: *** [threadELV3.o] Error 1
make[2]: Leaving directory `/home/sree/linux/peng/peng'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sree/linux/peng'
make: *** [all-recursive-am] Error 2
sree@ubuntumaruti:~/linux/peng$ make install
Making install in peng
make[1]: Entering directory `/home/sree/linux/peng/peng'
g++ -DHAVE_CONFIG_H -I. -I. -I..     -D_REENTRANT -c threadELV3.cpp
In file included from /usr/include/c++/4.0.2/backward/iostream.h:31,
                 from cclienttoaol30.h:24,
                 from kernel30.h:50,
                 from caolcmd30.h:22,
                 from threadELV3.h:24,
                 from threadELV3.cpp:21:
/usr/include/c++/4.0.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
kernel30.h:226: error: ISO C++ forbids declaration of â&#8364;&#732;CAolCmd30â&#8364;&#8482; with no type
kernel30.h:226: error: expected â&#8364;&#732;;â&#8364;&#8482; before â&#8364;&#732;*â&#8364;&#8482; token
make[1]: *** [threadELV3.o] Error 1
make[1]: Leaving directory `/home/sree/linux/peng/peng'
make: *** [install-recursive] Error 1
sree@ubuntumaruti:~/linux/peng$

i cant makeout what the problem
is there any other AOL dialing softwarw for linux
is there a way to correct this pengaol problem
please help me i am stuck

---

