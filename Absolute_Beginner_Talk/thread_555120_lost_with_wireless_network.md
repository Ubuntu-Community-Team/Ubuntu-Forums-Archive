---
title: "lost with wireless network"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by pilot_guy415 on 2007-09-19
Hi, I feel like a complete moron but I have to try something!

Anyway, Im brand new to linux...as in never used it EVER before.
I just installed ubuntu 2 days ago and I cant seem to get an internet connection. I have an internal wireless card on an HP dv6000. The card is an intel 3945ABG. I have ubuntu 6.06.

Here is the big problem, I only have ubuntu. I had a gunked up laptop and got sick of it so I formatted the hard drive then used someone elses computer (the computer Im on now) to download ubuntu and install it on my laptop. Well, ubuntu cant find my wireless card. I tried the trouble shooting guide but it seems to go past me and doesnt discribe very well.

I have no idea how to get ubuntu to read my card, and I cant download anything onto ubuntu because I obviously have no internet connection!

Please help!!

---

### Post by Maestro23 on 2007-09-19
You can download the driver on the computer you're on now to a flash drive or cd.  Save it and boot up Ubuntu and copy the file over.

The driver is a .tar.gz file so you will have to extract it. Download to your Desktop,  Right click on it and extract it or in command line:

> 
cd /home/username/Desktop
tar xvzf filename.tar.gz

Once extracted, there should be a README.txt file with all the instructions you will need.  When you run into problems, post back in this thread to get some help. I believe this is your Driver Download:  [http://sourceforge.net/project/downloading.php?groupname=ipw3945&filename=ipw3945-1.2.2.tgz&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=ipw3945&filename=ipw3945-1.2.2.tgz&use_mirror=superb-west)

---

### Post by pilot_guy415 on 2007-09-19
I appreciate the fast response. I downloaded the file but not I cant figure out how to install it lol.

The file says to build and install the ieee80211 subsystem

well I downloaded what it told me too but when I type in the code it tells me to (tar xzvf ieee80211-1.2.16) it says the file doesnt exist so I tried used ieee80211-1.1.18 (the name of the file I downloaded) and still nothing, any help here? I think I should have waited on formatting my harddrive lol this is scary.

---

### Post by Maestro23 on 2007-09-19
> **pilot_guy415 said:**
> I appreciate the fast response. I downloaded the file but not I cant figure out how to install it lol.

The file says to build and install the ieee80211 subsystem

well I downloaded what it told me too but when I type in the code it tells me to (tar xzvf ieee80211-1.2.16) it says the file doesnt exist so I tried used ieee80211-1.1.18 (the name of the file I downloaded) and still nothing, any help here? I think I should have waited on formatting my harddrive lol this is scary.

Is the file on your Desktop?  If so, you need to navigate to it first using the commands I posted earlier.  Then run the tar command.

---

### Post by pilot_guy415 on 2007-09-19
yes the files are on the desktopn and I used the cd /home...still says "No such file or directory"

---

### Post by Maestro23 on 2007-09-19
> **pilot_guy415 said:**
> yes the files are on the desktopn and I used the cd /home...still says "No such file or directory"

Linux is case sensitive.  If you can see the files on your Desktop then that command should work. Hmm...

> cd /home/username/**D**esktop

---

### Post by pilot_guy415 on 2007-09-19
> **Maestro23 said:**
> Linux is case sensitive.  If you can see the files on your Desktop then that command should work. Hmm...

ok I figured out part of it now I have another problem. I need to install the subsystem right? Well it says to install the subsystem I need to install the kernel source packages? Where would I get that? lol Im gonna be an expert with linux by the time I get this thing done!

---

### Post by pilot_guy415 on 2007-09-20
bump

---

### Post by pilot_guy415 on 2007-10-03
Ok, I am determined now to get this working...yea still havent done that! I have figured some stuff out but I am at a loss as to what Im doing wrong. Im just going to post everything it says in Terminal and if anyone can tell me whats going on it would be greatly appreciated!

> pat@pat-laptop:~$ cd /home/pat/Desktop/ipw3945-1.2.2
pat@pat-laptop:~/Desktop/ipw3945-1.2.2$ make
Makefile:53: 
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: 'make SHELL=/bin/bash'.
Makefile:57: 
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
pat@pat-laptop:~/Desktop/ipw3945-1.2.2$ make IEEE80211_IGNORE_DUPLICATE=y
Makefile:53: 
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: 'make SHELL=/bin/bash'.
Makefile:57: 
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e 
 ERROR: A compatible subsystem was not found in the following path[s]:

        /lib/modules/2.6.20-15-generic/include/ /lib/modules/2.6.20-15-generic/

You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

        % make IEEE80211_INC=/usr/src/ieee80211/

or use the 'make patch_kernel' within the ieee80211 subsystem to patch your
kernel sources.

make: *** [check_inc] Error 1
pat@pat-laptop:~/Desktop/ipw3945-1.2.2$ cd /home/pat/Desktop/ieee80211-1.2.18
pat@pat-laptop:~/Desktop/ieee80211-1.2.18$ make patch_kernel
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
-e 
 This will install this IEEE80211 subsystem into your
 kernel tree located here:

/lib/modules/2.6.20-15-generic/build

 If you would like to instal to a different location, run
 this as follows: make KSRC=/path/to/kernel patch_kernel 

Do you wish to continue? [Yn] y
-e 
If this fails, you may need to be root to patch the kernel.

cp: cannot stat `{*.c,in-tree/{Makefile,Kconfig},compat.h}': No such file or directory
make: *** [patch_kernel] Error 1
pat@pat-laptop:~/Desktop/ieee80211-1.2.18$ su root
Password: 
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# make patch_kernel
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
-e 
 This will install this IEEE80211 subsystem into your
 kernel tree located here:

/lib/modules/2.6.20-15-generic/build

 If you would like to instal to a different location, run
 this as follows: make KSRC=/path/to/kernel patch_kernel 

Do you wish to continue? [Yn] y
cp: cannot stat `{*.c,in-tree/{Makefile,Kconfig},compat.h}': No such file or directory
make: *** [patch_kernel] Error 1
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# make SHELL=/bin/bash
Checking in /lib/modules/2.6.20-15-generic for ieee80211 components...
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-15-generic/include/net/ieee80211_radiotap.h
/lib/modules/2.6.20-15-generic/include/net/ieee80211_crypt.h
/lib/modules/2.6.20-15-generic/include/net/ieee80211.h
Above files found.  Remove? [y],n y
make -C /lib/modules/2.6.20-15-generic/build M=/home/pat/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_module.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_tx.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_rx.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_wx.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_geo.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_wep.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_ccmp.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_tkip.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_ccmp.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_tkip.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_wep.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# make patch_kernel
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
-e 
 This will install this IEEE80211 subsystem into your
 kernel tree located here:

/lib/modules/2.6.20-15-generic/build

 If you would like to instal to a different location, run
 this as follows: make KSRC=/path/to/kernel patch_kernel 

Do you wish to continue? [Yn] y
cp: cannot stat `{*.c,in-tree/{Makefile,Kconfig},compat.h}': No such file or directory
make: *** [patch_kernel] Error 1
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# make install
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
make -C /lib/modules/2.6.20-15-generic/build M=/home/pat/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
/home/pat/Desktop/ieee80211-1.2.18/Makefile:17: 
/home/pat/Desktop/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/pat/Desktop/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/pat/Desktop/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/pat/Desktop/ieee80211-1.2.18/Makefile:21: 
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_module.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_tx.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_rx.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_wx.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_geo.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_wep.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_ccmp.o
  CC [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_tkip.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_ccmp.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_ccmp.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_tkip.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_tkip.ko
  CC      /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_wep.mod.o
  LD [M]  /home/pat/Desktop/ieee80211-1.2.18/ieee80211_crypt_wep.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
install -d /lib/modules/2.6.20-15-generic/net/ieee80211/
install -m 644 -c ieee80211.ko ieee80211_crypt.ko ieee80211_crypt_wep.ko ieee80211_crypt_ccmp.ko ieee80211_crypt_tkip.ko /lib/modules/2.6.20-15-generic/net/ieee80211/
install -d `echo /lib/modules/2.6.20-15-generic/include | grep "/net\$" || echo /lib/modules/2.6.20-15-generic/include/net`
install -m 644 -c net/ieee80211.h net/ieee80211_crypt.h net/ieee80211_radiotap.h `echo /lib/modules/2.6.20-15-generic/include | grep "/net\$" || echo /lib/modules/2.6.20-15-generic/include/net`
mkdir -p /lib/modules/2.6.20-15-generic/net/ieee80211//.tmp_versions
cd .tmp_versions && install -m 644 -c ieee80211.mod ieee80211_crypt.mod ieee80211_crypt_wep.mod ieee80211_crypt_ccmp.mod ieee80211_crypt_tkip.mod /lib/modules/2.6.20-15-generic/net/ieee80211//.tmp_versions
/sbin/depmod -a 2.6.20-15-generic
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# . remove-old
Checking in /lib/modules/2.6.20-15-generic for ieee80211 components...
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_tkip.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_ccmp.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211_crypt_wep.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/.tmp_versions/ieee80211.mod
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-15-generic/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-15-generic/include/net/ieee80211_radiotap.h
/lib/modules/2.6.20-15-generic/include/net/ieee80211_crypt.h
/lib/modules/2.6.20-15-generic/include/net/ieee80211.h
Above files found.  Remove? [y],n y
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# cd /lib/modules/\`uname -r\`/build
bash: cd: /lib/modules/`uname: No such file or directory
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# /lib/modules/\`uname -r\`/2.6.2
bash: /lib/modules/`uname: No such file or directory
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# make IEEE80211_INC=/usr/Include
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
Checking in /lib/modules/2.6.20-15-generic for ieee80211 components...
make -C /lib/modules/2.6.20-15-generic/build M=/home/pat/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
/home/pat/Desktop/ieee80211-1.2.18/Makefile:17: 
/home/pat/Desktop/ieee80211-1.2.18/Makefile:18: WARNING: $SHELL not set to bash.
/home/pat/Desktop/ieee80211-1.2.18/Makefile:19: If you experience build errors, try
/home/pat/Desktop/ieee80211-1.2.18/Makefile:20: 'make SHELL=/bin/bash'.
/home/pat/Desktop/ieee80211-1.2.18/Makefile:21: 
  Building modules, stage 2.
  MODPOST 5 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# su
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# su pat
pat@pat-laptop:~/Desktop/ieee80211-1.2.18$ cd ipw3945-1.2.2
bash: cd: ipw3945-1.2.2: No such file or directory
pat@pat-laptop:~/Desktop/ieee80211-1.2.18$ cd /home/pat/Desktop/ipw3945-1.2.2
pat@pat-laptop:~/Desktop/ipw3945-1.2.2$ make
Makefile:53: 
Makefile:54: WARNING: $SHELL not set to bash.
Makefile:55: If you experience build errors, try
Makefile:56: 'make SHELL=/bin/bash'.
Makefile:57: 
/bin/sh: Syntax error: "(" unexpected
/bin/sh: Syntax error: "(" unexpected
-e 
 WARNING: Your kernel contains ieee80211 symbol definitions and you
are not using the kernel's default ieee80211 subsystem.  (Perhaps you
used the out-of-tree ieee80211 subsystem's 'make install' or have
provided a path to the ieee80211 subsystem via IEEE80211_INC.)

If you wish to use the out-of-tree ieee80211 subsystem then it is
recommended to use that projects' "make patch_kernel" facility
and rebuild your kernel to update the Module symbol version information.

Failure to do this may result in build warnings and unexpected
behavior when running modules which rely on the ieee80211 subsystem.

 
-e  Aborting the build.  You can force the build to continue by adding:

        IEEE80211_IGNORE_DUPLICATE=y

to your make command line.


make: *** [check_inc] Error 1
pat@pat-laptop:~/Desktop/ipw3945-1.2.2$ su root
Password: 
root@pat-laptop:/home/pat/Desktop/ipw3945-1.2.2# cd /home/pat/Desktop/ieee80211-1.2.18
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# make patch_kernel
Makefile:17: 
Makefile:18: WARNING: $SHELL not set to bash.
Makefile:19: If you experience build errors, try
Makefile:20: 'make SHELL=/bin/bash'.
Makefile:21: 
-e 
 This will install this IEEE80211 subsystem into your
 kernel tree located here:

/lib/modules/2.6.20-15-generic/build

 If you would like to instal to a different location, run
 this as follows: make KSRC=/path/to/kernel patch_kernel 

Do you wish to continue? [Yn] y
cp: cannot stat `{*.c,in-tree/{Makefile,Kconfig},compat.h}': No such file or directory
make: *** [patch_kernel] Error 1
root@pat-laptop:/home/pat/Desktop/ieee80211-1.2.18# 


Please save me from this damn wired universe! lol

---

### Post by pilot_guy415 on 2007-10-03
bump...oh and fyi...if it makes a difference: I switched from the 6.06LTS version to the 7.04 version

---

### Post by hyper_ch on 2007-10-03
Its still not recognized in 7.04? (You could also try 7.10 as it has better wifi support as far as I know --> if you're lucky your wifi card works out of the box)

---

### Post by pilot_guy415 on 2007-10-03
Well, it does have the option of wireless available in the network window. The reason I figured I still need the drivers is because it doesnt work lol. I cant figure out how to search for local networks...and when I manually input the info for my network...nothing happens. Also the on my laptop indicating that the wireless card is working is saying its inactive. 

Is there a way to  update to 7.10 without downloading/formatting/reinstalling the whole system?

---

### Post by pilot_guy415 on 2007-10-03
bump

---

### Post by pilot_guy415 on 2007-10-05
Bump...someone has GOT to know SOMETHING

---

