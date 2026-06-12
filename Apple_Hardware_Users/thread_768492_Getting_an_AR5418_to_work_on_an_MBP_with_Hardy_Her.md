---
title: "Getting an AR5418 to work on an MBP with Hardy Heron"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2008-04-26
Hello, am trying, after a fresh CD installation of release 8.04 HH on my MacBook Pro 2nd generation (2,2), to get the wireless to work, at home, where I have only wireless...

First off, neither ifconfig nor iwconfig signal recognition of the card, though lspci will show it clearly, correctly identified.
I therefore believe there is a first fundamental problem there that I am not seeing. Of course the NM applet does not show anything wireless.

After some research, I found a madwifi trunk that should work with the Atheros AR5418 (equivalent to the AR 5008), as the snapshot which worked on FF 7.10 is no longer available on the madwifi site...
I tried to compile it, but it fails miserably on billions of errors (see at tbe end of the post), probably incorrect declarations in ath_hal because of the kernel changes.

My questions to competent gurus would therefore be:
1. how to get the card recognised?
2. how to compile correctly?

-Compilation results-

$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/muaddib/Desktop/madwifi-ng-r3456-20080407 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  HOSTCC  /home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c: At top level:
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c: In function 'main':
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal/uudecode] Error 1
make[2]: *** [/home/muaddib/Desktop/madwifi-ng-r3456-20080407/ath_hal] Error 2
make[1]: *** [_module_/home/muaddib/Desktop/madwifi-ng-r3456-20080407] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

---

### Post by cyberdork33 on 2008-04-26
Are you following direction here? You need to make sure the build-essential package is installed first.
[https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927](https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927)

---

### Post by GeneralSunTzu on 2008-04-26
> **cyberdork33 said:**
> Are you following direction here? You need to make sure the build-essential package is installed first.
[https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927](https://help.ubuntu.com/community/MacBookPro#head-688700b3e0e48847a28daba8bc557d4439a30927)

Thank you, oops - I thought it was installed by default.
Now, as I have only WiFi at home, either the build-essential package is on the alternate installation CD and then I can install it from there else I will have to wait to get to work, where I have cabled Ethernet.

The first question is still outstanding, though.
Why doesn't even  see the Airport Extreme card?

---

### Post by Rog-Mahal on 2008-04-26
The card will be recognized once you install the driver. I have the same card and using the instructions in the link by cyberdork helped, the daily snapshot worked just fine. Once you get it to correctly install, you can manually insert the module into your kernel (i.e. get your card to work without rebooting) by running

```
sudo modprobe ath_pci
``` in terminal.

Good luck

---

### Post by GeneralSunTzu on 2008-04-26
> **Rog-Mahal said:**
> The card will be recognized once you install the driver. I have the same card and using the instructions in the link by cyberdork helped, the daily snapshot worked just fine. Once you get it to correctly install, you can manually insert the module into your kernel (i.e. get your card to work without rebooting) by running

```
sudo modprobe ath_pci
``` in terminal.

Good luck

Thank you buddy. 
I believe I will have to try at work (where I have cabled Ethernet) then, because getting the uninstalled libraries via MacOS X (where WiFi works) and then moving them over to Ubuntu appears nearly impossible, because of the dependencies.
I had found a debian package on the CD called build-essential, but it seems just a list of files, not them real files, unfortunately.

---

### Post by cyberdork33 on 2008-04-26
if you startup ubuntu, and insert your install cd, it will detect that there are packages. you can install several packages from the cd rom, but you have to add it as a source for your system

```
sudo gedit /etc/apt/sources.list
```

there should be one or two lines at the top that are commented out for the cdrom. uncomment them, save, then do a 'sudo apt-get update' and you should then be able to install packages off the cd.

---

### Post by GeneralSunTzu on 2008-04-27
> **cyberdork33 said:**
> if you startup ubuntu, and insert your install cd, it will detect that there are packages. you can install several packages from the cd rom, but you have to add it as a source for your system

```
sudo gedit /etc/apt/sources.list
```

there should be one or two lines at the top that are commented out for the cdrom. uncomment them, save, then do a 'sudo apt-get update' and you should then be able to install packages off the cd.

Thank you so much. It worked brilliantly!!!

Am now fighting with hopping onto my WPA2 personal (with GG I did without problems, and both Ubuntus were AMD64 releases).
Something must have changed because simple roaming on the NM applet does not work, and I have a  debug output that tells me it is taking too long to associate to my AP.
I am also able to see all WiFi networks of the neighbourhood (quite crowded, here...), my SSID is not hidden and so I thought everything was all right...
I have also tried some elaborate voodoo suggested by another poster on the Internet/Wireless forum, consisting of renaming ath0 to wlan0, but it had no effect I can detect.
Ifconfig shows eth0, lo, wifi0 (no wireless extension), ath0.
Iwconfig shows ditto, the card is active, 802.11g (which is what I am using), and the right SSID, fleetingly, while it tries to connect, and then no longer, once the attempt fails.

My current list of things to try:

1. different madwifi release?
2. startup script nailing down details (SSID, WPA2 Personal key, TKIP AES, tx rate, etc.);
3. more network voodoo, recipe to be found.

Would you please have a more constructive suggestion, by any chance? 
Am not yet desperate, but I do not understand what I am doing wrong...

---

### Post by cyberdork33 on 2008-04-27
people have been having issues with nm recently but have installed wicd and reported that it works great. I haven't used it before so I can' offer any help.

---

### Post by GeneralSunTzu on 2008-04-28
> **cyberdork33 said:**
> people have been having issues with nm recently but have installed wicd and reported that it works great. I haven't used it before so I can' offer any help.

Dear cyberdork33, indeed it is and I have solved fully the problem.
Thanks to an unsecured WiFi AP in the neighbourhood I could download wicd, updated HH (strangely enough, no update...), and then done the following, to get the AR 5418 to work:

1. compile via subversion exactly the madwifi snapshot provided in the MacBook Pro Ubuntu wiki;
2. configure appropriately wpa_supplicant.conf, which did not exist, even if it may be unnecessary;
3. install wicd, which is totally different from the NM applet and far superior indeed.

And now, on to fix the  minor details (the trash can, the firewall, etc.).
Thanks again for the support and for the encouragement.

I can confirm, now with proof, than WPA2 Personal encryption works fine with AR 5418 Atheros cards and Hardy Heron.

---

