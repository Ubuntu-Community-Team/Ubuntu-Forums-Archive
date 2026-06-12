---
title: "Intel® PRO/Wireless 2200BG Driver"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by raffman on 2007-11-26
Hi,
          I'm trying to install a linux driver for my Intel® PRO/Wireless 2200BG Wireless card (came in my laptop) I found it on a website [here]("http://ipw2200.sourceforge.net/") it even has instructions but I'm a complete noob and don't understand them
Can some one please translate the instructions into noob for me?
or just tell me what to type in the terminal?
Thanks a lot!!

:confused::confused::confused:

---

### Post by jfinkels on 2007-11-26
First the requirements:

-Install wireless-tools. Type the following in the terminal:```
sudo aptitude install wireless-tools
```

-Download the driver: [http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.2.2.tgz?download](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.2.2.tgz?download)

-Download the firmware: [http://ipw2200.sourceforge.net/firmware.php?fid=7](http://ipw2200.sourceforge.net/firmware.php?fid=7)

-You may also need to install the build-essential package, which contains compilers and libraries and stuff that you need when compiling an executable file from source. Type:```
sudo aptitude install build-essential
```

-Install checkinstall. Type:```
sudo aptitude install checkinstall
```

Second, install necessary stuff, according to the INSTALL file in the .tgz file for the ipw2200 driver:

-Install iee80211-source. Type the following in the terminal:```
sudo aptitude install ieee80211-source
```

-Build the ipw2200 driver. Type:```
make
```

-Install the ipw2200 driver. Type:```
sudo checkinstall
```

Let me know if there are any errors, and post the output if there are!

---

### Post by mofrikaantje on 2007-12-15
Hi,

I'm also experiencing some problems with my wireless connection (it's not showing in network manager), and I tried reinstalling my drivers. I tried with the GUI of ndiswrapper (installing the proprietary driver that is) but I still don't get a list of available wireless connections. Earlier today, wlan0 DID show with ifconfig, but it's already disappeared by now and I only have eth0 and lo left. 
I then followed the steps above (thinking "who knows?"), but apparently ieee80211 isn't installed properly, because I get this when I want to make the driver:

```
sander@sander-laptop:~$ cd Desktop
sander@sander-laptop:~/Desktop$ cd ipw*
sander@sander-laptop:~/Desktop/ipw2200-1.2.2$ make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.22-14-386/include'.

-e You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Fout 1
```

The installation of ieee80211 seemed succesfull, so I don't understand what's still causing this. (The driver should in fact already been installed succesfully, cf. above)
Any ideas?

(PS: I know this isn't "networking and wireless", but the topic comes closest to my problem)

---

### Post by jfinkels on 2007-12-15
> **mofrikaantje said:**
> 
sander@sander-laptop:~/Desktop/ipw2200-1.2.2$ make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.22-14-386/include'.

-e You need to install the ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/
[/CODE]


You can use the program "locate" to find files on your computer. Update the "locate" database by typing:```
sudo locate -u
```and search for the ieee80211 files by typing:```
locate ieee80211
```

When I do this, locate finds my files at the following locations:```
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
/usr/src/linux-headers-2.6.22-14/net/ieee80211
/usr/src/linux-headers-2.6.22-14/net/ieee80211/Kconfig
/usr/src/linux-headers-2.6.22-14/net/ieee80211/softmac
/usr/src/linux-headers-2.6.22-14/net/ieee80211/softmac/Kconfig
/usr/src/linux-headers-2.6.22-14/net/ieee80211/softmac/Makefile
/usr/src/linux-headers-2.6.22-14/net/ieee80211/Makefile
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211softmac.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211_radiotap.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211_crypt.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211softmac_wx.h
/usr/src/linux-headers-2.6.22-14/include/linux/ieee80211.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/softmac.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt/tkip.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt/ccmp.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt/wep.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211.h
/usr/src/linux-headers-2.6.22-14-generic/include/linux/ieee80211.h

```
It looks like the files we need to locate are here:```

<snip>
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211softmac.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211_radiotap.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211_crypt.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211softmac_wx.h
<snip>
```
Now, if your files were installed to the same place as mine were, you will need to point make to look for them in the directory "/usr/src/linux-headers-2.6.22-14/include/net/" by typing the following instead of typing 'make':```
make IEEE80211_INC=/usr/src/linux-headers-2.6.22-14/include/net/
```Of course, replace the directory with the appropriate one for your system if it is different. Let me know if you need further explanation or help.

---

### Post by dthomas08 on 2007-12-19
Hey,
I'm a bit new to Ubuntu as I have only had it on my desktop for 3 months, but I just put it on my laptop. It's a Dell Latitude D800. I found this post and it sounded quite promissing ... but sadly it doesn't seem to have worked. After doing your instructions:

> 
sudo checkinstall


I get the following output

```

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@derek-laptop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ ipw2200 ]
3 -  Version: [ 1.2.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ipw2200-1.2.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
mkdir -p /tmp/.tmp_versions
pwd: couldn't find directory entry in `../../../../..' with matching i-node
make -C /lib/modules/2.6.20-16-generic/build M= MODVERDIR=/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[2]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/gcc-version.sh: Permission denied
[: 1: 0400: unexpected operator
  HOSTCC  scripts/genksyms/lex.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make[2]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

I can't seem to think of the cause of the failure as I went by the instructions exactly ... one question though. You tell us to download the firmware, but never tell us what to do with it. Could this be the problem as I didn't do what I needed to do with the firmware?

Thanks a lot

---

### Post by Whiffle on 2007-12-19
Woah woah woah...why are you trying to make this one from source?  It comes with ubuntu already...

---

### Post by aJayRoo on 2007-12-19
Yeah I thought this driver came with Ubuntu? I have been using my laptop with an intel pro wireless 2200 for a few versions now and the only thing I have ever had to do was drop the firmware in the '/lib/firware' directory. Having said that I'm fairly sure it worked out the box with Ubuntu 7.10, although I could be wrong.

---

### Post by dthomas08 on 2007-12-19
I am unable to get my wireless to find any networks. I even tried to manually configure a wireless connection when I knew the name of the network and the password (as I created it...). Any Idea how I can configure this thing?

---

### Post by dthomas08 on 2007-12-19
Oh and I am using 7.04

---

### Post by Whiffle on 2007-12-19
Could you post the output of

'iwconfig'

---

### Post by dthomas08 on 2007-12-19
Here's the output:

```


lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

---

### Post by Whiffle on 2007-12-19
Alrite it looks like your wireless drivers are working fine, so the problem lies somewhere with networkmanager or wpa_supplicant.

What does it do when you give networkmanager your name/password?

---

### Post by dthomas08 on 2007-12-19
ok so I click "connect to other wireless networks..." then I type in the necessary information and it sits there and attempts to connect

---

### Post by Whiffle on 2007-12-19
Hmph.  I havn't used networkmanager in ages... I do know that the version that came with feisty is not as well developed as the one in gutsy.  If you're feeling adventurous you might try removing the feisty networkmanager packages and installing some from gutsy (which can be had at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) ).  Other than that and some command line stuff I really don't know what else to try.

---

### Post by dthomas08 on 2007-12-19
I might try Gusty and get back to the post as soon as I have checked it. Thanks for your help

---

### Post by Whiffle on 2007-12-19
You might try a LiveCD and see what that does.

---

### Post by zgornel on 2007-12-19
The Intel wireless driver should work out of the box. What does ```
dmesg | grep ipw
``` say ?

---

### Post by dthomas08 on 2007-12-19
that didn't say anything

---

### Post by aJayRoo on 2007-12-19
Erm, doesn't iwconfig say you have a Broadcom 4306 chipset and not the Intel Pro Wireless? I could be wrong but I think you need to be searching for broadcom driver installation problems on the forums!

---

### Post by Whiffle on 2007-12-19
Thats just a nickname set by an accesspoint or something else.  If he really is not sure about what he has, then 

lspci -v 

would tell him what he has..

---

### Post by dthomas08 on 2007-12-19
In case you were curious:

> 

02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card
        Flags: fast devsel, IRQ 5
        Memory at fafec000 (32-bit, non-prefetchable) [size=8K]



---

### Post by aJayRoo on 2007-12-19
It does look like your wireless chipset is actually a Broadcom 4306. I would advise you to search these forums for further advice on how to setup a wireless connection with this type of chipset. I am certain that there will be multiple helpful threads relating to this. I had a PCI wireless card with a Broadcom chipset and all that was required was to extract the firmware from the windows driver and place it in the '/lib/firmware' folder (using bcm43xx-fwcutter from the repositories) though I'm not sure that this process is the same for all chipsets.

---

### Post by dthomas08 on 2007-12-19
Thanks a lot for all the help everybody!

---

### Post by raffman on 2007-12-19
I tried and this is what I got
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.22-14-generic/include'.

-e But an in-tree version of ieee80211 subsystem is found. Will use this one
 instead. If you find problems when compiling the driver, please install
 the external ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)

mkdir -p /home/raffi/Documents/School/ipw2200-1.2.2/tmp/.tmp_versions
make -C /lib/modules/2.6.22-14-generic/build M=/home/raffi/Documents/School/ipw2200-1.2.2 MODVERDIR=/home/raffi/Documents/School/ipw2200-1.2.2/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/raffi/Documents/School/ipw2200-1.2.2/ipw2200.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/raffi/Documents/School/ipw2200-1.2.2/ipw2200.mod.o
  LD [M]  /home/raffi/Documents/School/ipw2200-1.2.2/ipw2200.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
raffi@laptop-1:~/Documents/School/ipw2200-1.2.2$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> linux wireless
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@laptop-1 ]
1 -  Summary: [ linux wireless ]
2 -  Name:    [ ipw2200 ]
3 -  Version: [ 1.2.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ipw2200-1.2.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
pwd: couldn't find directory entry in `../../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../../..' with matching i-node
mkdir -p /tmp/.tmp_versions
pwd: couldn't find directory entry in `../../../../../..' with matching i-node
make -C /lib/modules/2.6.22-14-generic/build M= MODVERDIR=/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function ‘usage’:
scripts/basic/fixdep.c:131: warning: implicit declaration of function ‘fprintf’
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:131: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function ‘exit’
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘print_cmdline’:
scripts/basic/fixdep.c:140: warning: implicit declaration of function ‘printf’
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: ‘NULL’ undeclared here (not in a function)
scripts/basic/fixdep.c: In function ‘grow_config’:
scripts/basic/fixdep.c:156: warning: implicit declaration of function ‘realloc’
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function ‘perror’
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c: In function ‘is_defined_config’:
scripts/basic/fixdep.c:174: warning: implicit declaration of function ‘memcmp’
scripts/basic/fixdep.c: In function ‘define_config’:
scripts/basic/fixdep.c:187: warning: implicit declaration of function ‘memcpy’
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c: In function ‘use_config’:
scripts/basic/fixdep.c:206: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:220: warning: implicit declaration of function ‘tolower’
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:206: warning: unused variable ‘s’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_config_file’:
scripts/basic/fixdep.c:227: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function ‘ntohl’
scripts/basic/fixdep.c:244: warning: implicit declaration of function ‘isalnum’
scripts/basic/fixdep.c: In function ‘strrcmp’:
scripts/basic/fixdep.c:261: warning: implicit declaration of function ‘strlen’
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function ‘strlen’
scripts/basic/fixdep.c: In function ‘do_config_file’:
scripts/basic/fixdep.c:272: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function ‘open’
scripts/basic/fixdep.c:276: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:278: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:282: warning: implicit declaration of function ‘fstat’
scripts/basic/fixdep.c:284: warning: implicit declaration of function ‘close’
scripts/basic/fixdep.c:287: warning: implicit declaration of function ‘mmap’
scripts/basic/fixdep.c:287: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function ‘parse_config_file’
scripts/basic/fixdep.c:296: warning: implicit declaration of function ‘munmap’
scripts/basic/fixdep.c:272: warning: unused variable ‘st’
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or ‘...’ before ‘size_t’
scripts/basic/fixdep.c: In function ‘parse_dep_file’:
scripts/basic/fixdep.c:304: error: ‘len’ undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: ‘PATH_MAX’ undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function ‘strchr’
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function ‘strchr’
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:310: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function ‘memcpy’
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function ‘printf’
scripts/basic/fixdep.c:306: warning: unused variable ‘s’
scripts/basic/fixdep.c: In function ‘print_deps’:
scripts/basic/fixdep.c:343: error: storage size of ‘st’ isn’t known
scripts/basic/fixdep.c:347: error: ‘O_RDONLY’ undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:349: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function ‘exit’
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:359: error: ‘PROT_READ’ undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: ‘MAP_PRIVATE’ undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function ‘parse_dep_file’
scripts/basic/fixdep.c:343: warning: unused variable ‘st’
scripts/basic/fixdep.c: In function ‘traps’:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function ‘fprintf’
scripts/basic/fixdep.c:378: error: ‘stderr’ undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function ‘exit’
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

what should I do?

---

### Post by dthomas08 on 2007-12-19
Ok here's what I did to fix my problem. Since I found that I actually had a broadcom product, I went to the following webpage and it worked perfectly:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

Oh and I installed Gutsy which is pretty nice. Thanks everyone for helping me. If you have another wireless card, try the above website and see if it has information on your own card.  Good luck everyone

---

### Post by jfinkels on 2007-12-19
> **raffman said:**
> I tried and this is what I got
[...]
what should I do?
When you post the output of executing a command, please post the command you entered so that we can all see. What is the first command whose output you posted above?

You can only run checkinstall after running "make" successfully.

Can you post the output of ```
locate ieee80211
```

---

### Post by raffman on 2007-12-26
sure...
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/var/lib/dpkg/info/ieee80211-source.list
/var/lib/dpkg/info/ieee80211-source.md5sums
/var/cache/apt/archives/ieee80211-source_1.1.6-4_all.deb
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt/tkip.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt/ccmp.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/crypt/wep.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211/softmac.h
/usr/src/linux-headers-2.6.22-14-generic/include/config/ieee80211.h
/usr/src/linux-headers-2.6.22-14-generic/include/linux/ieee80211.h
/usr/src/ieee80211-source.tar.gz
/usr/src/linux-headers-2.6.22-14/net/ieee80211
/usr/src/linux-headers-2.6.22-14/net/ieee80211/softmac
/usr/src/linux-headers-2.6.22-14/net/ieee80211/softmac/Kconfig
/usr/src/linux-headers-2.6.22-14/net/ieee80211/softmac/Makefile
/usr/src/linux-headers-2.6.22-14/net/ieee80211/Kconfig
/usr/src/linux-headers-2.6.22-14/net/ieee80211/Makefile
/usr/src/linux-headers-2.6.22-14/include/linux/ieee80211.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211softmac.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211softmac_wx.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211_crypt.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211_radiotap.h
/usr/src/linux-headers-2.6.22-14/include/net/ieee80211.h
/usr/share/doc/aircrack-ng/injection-patches/ieee80211_inject.patch
/usr/share/doc/ieee80211-source
/usr/share/doc/ieee80211-source/changelog.gz
/usr/share/doc/ieee80211-source/README.Debian
/usr/share/doc/ieee80211-source/changelog.Debian.gz
/usr/share/doc/ieee80211-source/copyright
/usr/include/ieee80211
/usr/include/ieee80211/net
/usr/include/ieee80211/net/ieee80211_crypt.h
/usr/include/ieee80211/net/ieee80211_radiotap.h
/usr/include/ieee80211/net/ieee80211.h
/home/raffi/aircrack-ng-0.9.1/patches/ieee80211_inject.patch

---

### Post by jfinkels on 2007-12-28
Sorry for the delay in reply. I have been out of contact with my computer.

Since your ieee80211*.h files are contained in the directory "/usr/src/linux-headers-2.6.22-14/include/net/", try running make with this command, (which tells make to look for the ieee80211*.h files in that directory): 
```

make IEEE80211_INC=/usr/src/linux-headers-2.6.22-14/include/net/

```

---

### Post by mshipon on 2008-03-01
This is the output from the "make" and "sudo checkinstall" commands...  Did it work?  What's going on?  Sorry, I'm new at this...

Thanks!

Martin


cottman@ubuntu:~/Desktop/ipw2200-1.2.2$ make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.20-16-generic/include'.

-e But an in-tree version of ieee80211 subsystem is found. Will use this one
 instead. If you find problems when compiling the driver, please install
 the external ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)

mkdir -p /home/cottman/Desktop/ipw2200-1.2.2/tmp/.tmp_versions
make -C /lib/modules/2.6.20-16-generic/build M=/home/cottman/Desktop/ipw2200-1.2.2 MODVERDIR=/home/cottman/Desktop/ipw2200-1.2.2/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/cottman/Desktop/ipw2200-1.2.2/ipw2200.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/cottman/Desktop/ipw2200-1.2.2/ipw2200.mod.o
  LD [M]  /home/cottman/Desktop/ipw2200-1.2.2/ipw2200.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
cottman@ubuntu:~/Desktop/ipw2200-1.2.2$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Intel 2200BG Driver Installation
>> EOF
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Intel 2200BG Driver Installation ]
2 -  Name:    [ ipw2200 ]
3 -  Version: [ 1.2.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ipw2200-1.2.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name: 
>> 

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Intel 2200BG Driver Installation ]
2 -  Name:    [ ipw2200 ]
3 -  Version: [ 1.2.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ipw2200-1.2.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
mkdir -p /tmp/.tmp_versions
pwd: couldn't find directory entry in `../../../../..' with matching i-node
make -C /lib/modules/2.6.20-16-generic/build M= MODVERDIR=/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/gcc-version.sh: Permission denied
[: 1: 0400: unexpected operator
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTCC  scripts/kconfig/conf.o
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTCC  scripts/kconfig/kxgettext.o
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTCC  scripts/kconfig/zconf.tab.o
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/i386/Kconfig
*
* Restart config...
*
*
* Wireless LAN (non-hamradio)
*
Wireless LAN drivers (non-hamradio) & Wireless Extensions (NET_RADIO) [Y/n/?] y
  Wireless Extension API over RtNetlink (NET_WIRELESS_RTNETLINK) [Y/n/?] y
  *
  * Obsolete Wireless cards support (pre-802.11)
  *
  STRIP (Metricom starmode radio IP) (STRIP) [M/n/y/?] m
  Aironet Arlan 655 & IC2200 DS support (ARLAN) [M/n/y/?] m
  AT&T/Lucent old WaveLAN & DEC RoamAbout DS ISA support (WAVELAN) [M/n/y/?] m
  AT&T/Lucent old WaveLAN Pcmcia wireless support (PCMCIA_WAVELAN) [M/n/?] m
  Xircom Netwave AirSurfer Pcmcia wireless support (PCMCIA_NETWAVE) [M/n/?] m
  *
  * Wireless 802.11 Frequency Hopping cards support
  *
  Aviator/Raytheon 2.4MHz wireless support (PCMCIA_RAYCS) [M/n/?] m
  *
  * Wireless 802.11b ISA/PCI cards support
  *
  Intel PRO/Wireless 2100 Network Connection (IPW2100) [N/m/y/?] (NEW) 
  Intel PRO/Wireless 2200BG and 2915ABG Network Connection (IPW2200) [N/m/y/?] (NEW) 
  Cisco/Aironet 34X/35X/4500/4800 ISA and PCI cards (AIRO) [M/n/y/?] m
  Hermes chipset 802.11b support (Orinoco/Prism2/Symbol) (HERMES) [M/n/y/?] m
    Hermes in PLX9052 based PCI adaptor support (Netgear MA301 etc.) (PLX_HERMES) [M/n/?] m
    Hermes in TMD7160 based PCI adaptor support (TMD_HERMES) [M/n/?] m
    Nortel emobility PCI adaptor support (NORTEL_HERMES) [M/n/?] m
    Prism 2.5 PCI 802.11b adaptor support (PCI_HERMES) [M/n/?] m
  Atmel at76c50x chipset  802.11b support (ATMEL) [M/n/y/?] m
    Atmel at76c506 PCI cards (PCI_ATMEL) [M/n/?] m
  *
  * Wireless 802.11b Pcmcia/Cardbus cards support
  *
  Hermes PCMCIA card support (PCMCIA_HERMES) [M/n/?] m
  Symbol Spectrum24 Trilogy PCMCIA card support (PCMCIA_SPECTRUM) [M/n/?] m
  Cisco/Aironet 34X/35X/4500/4800 PCMCIA cards (AIRO_CS) [M/n/?] m
  Atmel at76c502/at76c504 PCMCIA cards (PCMCIA_ATMEL) [M/n/?] m
  Planet WL3501 PCMCIA cards (PCMCIA_WL3501) [M/n/?] m
  *
  * Prism GT/Duette 802.11(a/b/g) PCI/Cardbus support
  *
  Intersil Prism GT/Duette/Indigo PCI/Cardbus (PRISM54) [N/m/y/?] n
  USB ZD1201 based Wireless device support (USB_ZD1201) [M/n/?] m
  IEEE 802.11 for Host AP (Prism2/2.5/3 and WEP/TKIP/CCMP) (HOSTAP) [M/n/y/?] m
    Support downloading firmware images with Host AP driver (HOSTAP_FIRMWARE) [Y/n/?] y
      Support for non-volatile firmware download (HOSTAP_FIRMWARE_NVRAM) [Y/n/?] y
    Host AP driver for Prism2/2.5/3 in PLX9052 PCI adaptors (HOSTAP_PLX) [M/n/?] m
    Host AP driver for Prism2.5 PCI adaptors (HOSTAP_PCI) [M/n/?] m
    Host AP driver for Prism2/2.5/3 PC Cards (HOSTAP_CS) [M/n/?] m
  Broadcom BCM43xx wireless support (BCM43XX) [M/n/?] m
    Broadcom BCM43xx debugging (RECOMMENDED) (BCM43XX_DEBUG) [N/y/?] n
    BCM43xx data transfer mode
    > 1. DMA + PIO (BCM43XX_DMA_AND_PIO_MODE)
      2. DMA (Direct Memory Access) only (BCM43XX_DMA_MODE)
      3. PIO (Programmed I/O) only (BCM43XX_PIO_MODE)
    choice[1-3]: 1
  ZyDAS ZD1211/ZD1211B USB-wireless support (ZD1211RW) [M/n/?] m
    ZyDAS ZD1211 debugging (ZD1211RW_DEBUG) [N/y/?] n
#
# configuration written to .config
#
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/gcc-version.sh: Permission denied
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
[: 1: 0400: unexpected operator
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/gcc-version.sh: Permission denied
[: 1: 0400: unexpected operator
  HOSTCC  scripts/genksyms/lex.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make[2]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


> cottman@ubuntu:~/Desktop/ipw2200-1.2.2$ make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.20-16-generic/include'.

-e But an in-tree version of ieee80211 subsystem is found. Will use this one
 instead. If you find problems when compiling the driver, please install
 the external ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net)

mkdir -p /home/cottman/Desktop/ipw2200-1.2.2/tmp/.tmp_versions
make -C /lib/modules/2.6.20-16-generic/build M=/home/cottman/Desktop/ipw2200-1.2.2 MODVERDIR=/home/cottman/Desktop/ipw2200-1.2.2/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/cottman/Desktop/ipw2200-1.2.2/ipw2200.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/cottman/Desktop/ipw2200-1.2.2/ipw2200.mod.o
  LD [M]  /home/cottman/Desktop/ipw2200-1.2.2/ipw2200.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
cottman@ubuntu:~/Desktop/ipw2200-1.2.2$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> Intel 2200BG Driver Installation
>> EOF
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Intel 2200BG Driver Installation ]
2 -  Name:    [ ipw2200 ]
3 -  Version: [ 1.2.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ipw2200-1.2.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 2
Enter new name: 
>> 

This package will be built according to these values: 

0 -  Maintainer: [ root@ubuntu ]
1 -  Summary: [ Intel 2200BG Driver Installation ]
2 -  Name:    [ ipw2200 ]
3 -  Version: [ 1.2.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ ipw2200-1.2.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
pwd: couldn't find directory entry in `../../../../..' with matching i-node
mkdir -p /tmp/.tmp_versions
pwd: couldn't find directory entry in `../../../../..' with matching i-node
make -C /lib/modules/2.6.20-16-generic/build M= MODVERDIR=/tmp/.tmp_versions modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
make[2]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/gcc-version.sh: Permission denied
[: 1: 0400: unexpected operator
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTCC  scripts/kconfig/conf.o
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTCC  scripts/kconfig/kxgettext.o
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTCC  scripts/kconfig/zconf.tab.o
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
make[3]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/kconfig/lxdialog/check-lxdialog.sh: Permission denied
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/i386/Kconfig
*
* Restart config...
*
*
* Wireless LAN (non-hamradio)
*
Wireless LAN drivers (non-hamradio) & Wireless Extensions (NET_RADIO) [Y/n/?] y
  Wireless Extension API over RtNetlink (NET_WIRELESS_RTNETLINK) [Y/n/?] y
  *
  * Obsolete Wireless cards support (pre-802.11)
  *
  STRIP (Metricom starmode radio IP) (STRIP) [M/n/y/?] m
  Aironet Arlan 655 & IC2200 DS support (ARLAN) [M/n/y/?] m
  AT&T/Lucent old WaveLAN & DEC RoamAbout DS ISA support (WAVELAN) [M/n/y/?] m
  AT&T/Lucent old WaveLAN Pcmcia wireless support (PCMCIA_WAVELAN) [M/n/?] m
  Xircom Netwave AirSurfer Pcmcia wireless support (PCMCIA_NETWAVE) [M/n/?] m
  *
  * Wireless 802.11 Frequency Hopping cards support
  *
  Aviator/Raytheon 2.4MHz wireless support (PCMCIA_RAYCS) [M/n/?] m
  *
  * Wireless 802.11b ISA/PCI cards support
  *
  Intel PRO/Wireless 2100 Network Connection (IPW2100) [N/m/y/?] (NEW) 
  Intel PRO/Wireless 2200BG and 2915ABG Network Connection (IPW2200) [N/m/y/?] (NEW) 
  Cisco/Aironet 34X/35X/4500/4800 ISA and PCI cards (AIRO) [M/n/y/?] m
  Hermes chipset 802.11b support (Orinoco/Prism2/Symbol) (HERMES) [M/n/y/?] m
    Hermes in PLX9052 based PCI adaptor support (Netgear MA301 etc.) (PLX_HERMES) [M/n/?] m
    Hermes in TMD7160 based PCI adaptor support (TMD_HERMES) [M/n/?] m
    Nortel emobility PCI adaptor support (NORTEL_HERMES) [M/n/?] m
    Prism 2.5 PCI 802.11b adaptor support (PCI_HERMES) [M/n/?] m
  Atmel at76c50x chipset  802.11b support (ATMEL) [M/n/y/?] m
    Atmel at76c506 PCI cards (PCI_ATMEL) [M/n/?] m
  *
  * Wireless 802.11b Pcmcia/Cardbus cards support
  *
  Hermes PCMCIA card support (PCMCIA_HERMES) [M/n/?] m
  Symbol Spectrum24 Trilogy PCMCIA card support (PCMCIA_SPECTRUM) [M/n/?] m
  Cisco/Aironet 34X/35X/4500/4800 PCMCIA cards (AIRO_CS) [M/n/?] m
  Atmel at76c502/at76c504 PCMCIA cards (PCMCIA_ATMEL) [M/n/?] m
  Planet WL3501 PCMCIA cards (PCMCIA_WL3501) [M/n/?] m
  *
  * Prism GT/Duette 802.11(a/b/g) PCI/Cardbus support
  *
  Intersil Prism GT/Duette/Indigo PCI/Cardbus (PRISM54) [N/m/y/?] n
  USB ZD1201 based Wireless device support (USB_ZD1201) [M/n/?] m
  IEEE 802.11 for Host AP (Prism2/2.5/3 and WEP/TKIP/CCMP) (HOSTAP) [M/n/y/?] m
    Support downloading firmware images with Host AP driver (HOSTAP_FIRMWARE) [Y/n/?] y
      Support for non-volatile firmware download (HOSTAP_FIRMWARE_NVRAM) [Y/n/?] y
    Host AP driver for Prism2/2.5/3 in PLX9052 PCI adaptors (HOSTAP_PLX) [M/n/?] m
    Host AP driver for Prism2.5 PCI adaptors (HOSTAP_PCI) [M/n/?] m
    Host AP driver for Prism2/2.5/3 PC Cards (HOSTAP_CS) [M/n/?] m
  Broadcom BCM43xx wireless support (BCM43XX) [M/n/?] m
    Broadcom BCM43xx debugging (RECOMMENDED) (BCM43XX_DEBUG) [N/y/?] n
    BCM43xx data transfer mode
    > 1. DMA + PIO (BCM43XX_DMA_AND_PIO_MODE)
      2. DMA (Direct Memory Access) only (BCM43XX_DMA_MODE)
      3. PIO (Programmed I/O) only (BCM43XX_PIO_MODE)
    choice[1-3]: 1
  ZyDAS ZD1211/ZD1211B USB-wireless support (ZD1211RW) [M/n/?] m
    ZyDAS ZD1211 debugging (ZD1211RW_DEBUG) [N/y/?] n
#
# configuration written to .config
#
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/gcc-version.sh: Permission denied
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
[: 1: 0400: unexpected operator
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: execvp: /usr/src/linux-headers-2.6.20-16-generic/scripts/gcc-version.sh: Permission denied
[: 1: 0400: unexpected operator
  HOSTCC  scripts/genksyms/lex.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/modpost.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
make[2]: *** No rule to make target `arch/i386/kernel/msr.c', needed by `arch/i386/kernel/msr.o'.  Stop.
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [modules] Error 2

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by Firebat451 on 2008-03-25
I'm having the same problems as everyone else here.  Using the 'make IEEE80211_INC=/usr/src/linux-headers-2.6.22-14/include/net/' command didn't work, I did check and the file locations are the same on my computer.  Dropping the firmware files into the folder did nothing either.  Here is my 'iwconfig'

```

lo           no wireless extensions.

eth0       no wireless extensions.

eth1       radio off  ESSID:""
             Mode:Managed  Channel:0  Access Point: Not-Associated
             Bit Rate:0 kb/s  Tx-Power=off   Sensitivity=8/0
             Retry limit:7  RTS thr:off  Fragment thr:off
             Power Management:off
             Link Quality:0 Signal level:0 Noise level:0
             Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
             Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth2       no wireless extensions.

```

---

