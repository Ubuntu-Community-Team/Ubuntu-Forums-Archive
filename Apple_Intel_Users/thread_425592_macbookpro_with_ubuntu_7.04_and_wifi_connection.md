---
title: "macbookpro with ubuntu 7.04 and wifi connection"
date: 2007-04-27
forum: Apple Intel Users
---

### Post by gagginaspinnata on 2007-04-27
Hello everyone ):P  This is my first post :mrgreen:  First of all I would like to apologise for my not perfect english :) 

I've installed ubuntu 7.04 on a macbookpro core duo (didint mean core 2 duo) and I'm facing a lot of troubles trying to connect to internet via wifi. 
I heard about [madwifi]("www.madwifi.org") but it wont work :) . Doing *make* says:
```
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ sudo makeChecking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  HOSTCC  /home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: At top level:
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'main':
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode] Error 1
make[2]: *** [/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal] Error 2
make[1]: *** [_module_/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ 
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$
```

As you can see there is some errors


Than, doing *make isntall* it says:
```
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.20-15-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
test -d //lib/modules/2.6.20-15-generic/net || mkdir -p //lib/modules/2.6.20-15-generic/net
cp ath_pci.ko //lib/modules/2.6.20-15-generic/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
make: *** [install-modules] Error 1
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ 


```

There is again some errors :( 

I've even tried this guide:
> Actually, you CAN get your wireless working. I just did it, and it's not hard. I also have a 17" iMac Intel Core Duo, with a Broadcom 4310 wireless card.

First, to check if you also have the same card, do this:
Code:

lspci | grep Broadcom\ Corporation

If you see something involving the number 4310, you can use the following to get it working:

1. Open System->Administration->Network and find the device eth1. Open the settings for eth1, and uncheck the box that says "Roaming". This will prevent NetworkManager for interfering with the following process. (NetworkManager is that networking icon in the upper-right corner of your screen.) For some reason, NetworkManager didn't work for me, and I had to turn it off when I installed the wireless driver.

2. Open synaptic package manager (from System->Administration->Synaptic Package Manager) or a terminal.

3. If using synaptic, search (ctrl+f) for "ndiswrapper" and select the packages related to ndiswrapper, then install them.

4. If using terminal, type:
Code:

sudo apt-get install ndiswrapper-common ndiswrapper-utils

5. Open a terminal and type:
Code:

sudo gedit /etc/modprobe.d/blacklist

6. Add these lines to the file so nothing interferes with ndiswrapper, then save it:
Code:

# remove the following to allow use of bcm43xx for wireless
blacklist bcm43xx

7. Download the driver for your card at the following link:
Code:

[ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)

8. Either use synaptic or a terminal to install cabextract:
Code:

sudo apt-get install cabextract

9. Run the command:
Code:

cabextract sp33008.exe

(do this if you're already in the directory with sp33008.exe in it, if not, use "cd <path to sp33008.exe>" to get to that directory first.)

10. While still in the same directory as sp33008.exe, run the command:
Code:

sudo ndiswrapper -i bcmwl5.inf

(that's a lowercase I as in "Into")

11. Type:
Code:

sudo ndiswrapper -l

(that's a lowercase L as in "Loopy")

12. If you see something like, "Driver installed," you've done it right.

13. Type:
Code:

sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo gedit /etc/modules

14. Add the following line to the file:
Code:

ndiswrapper

15. Type:
Code:

sudo iwconfig

16. If you see a device called "eth1," everything is probably working correctly.

17. You can also type the following command to make sure your wireless card is seeing networks, especially yours. Also, it can help you know what your network's ESSID is for the next step:
Code:

sudo iwlist scan

18. Type:
Code:

sudo iwconfig eth1 essid "<YOUR NETWORK'S NAME>"

(where <YOUR NETWORK'S NAME> is actually the name you gave your network)
Code:

sudo iwconfig eth1 key restricted <YOUR WEP PASSWORD>

(where <YOUR WEP PASSWORD> is actually the password for your network. NOTE: This assumes you're using a WEP password. If not, don't do this step.)

19. Type:
Code:

sudo dhclient

20. If it seems to have gotten an IP address and you can open web pages, you've successfully finished configuring your wireless network. Congratulations.



I'm not able to connect to internet via wireless :( 

There is anyone who would like to help me?

---

### Post by ronocdh on 2007-05-04
Hey there! Sorry your question has gone unanswered so long. Personally I don't have a solution, but it appears [you are not alone]("http://ubuntuforums.org/showthread.php?t=432269") in your troubles.

Have you made any progress towards getting it to work?

Also, please post your specific wireless chipset, so we know what we're working with here.

---

### Post by gagginaspinnata on 2007-05-04
At the end I reinstalled ubuntu and madwifi worked as well :mrgreen: 
Dunno why it didnt work before&#8230;now is working properly;) 
Simply I made ```
make
make isntall
```
and after rebooting ubuntu, has worked!):P

---

### Post by furbys on 2007-05-04
Ye, my core duo mac wifi worked the first time i started up ubuntu. Guess you were just a little unlucky

---

### Post by ronocdh on 2007-05-04
> **furbys said:**
> Ye, my core duo mac wifi worked the first time i started up ubuntu. Guess you were just a little unlucky
It all depends on the chipset, certainly--but also on [the basics]("http://ubuntuforums.org/showthread.php?t=432269") (resolution for other thread posted there).

=) Glad to hear it's working again.

---

### Post by gagginaspinnata on 2007-05-04
this is my chipset :

[IMG]http://img413.imageshack.us/img413/3626/immagine2bb5.png[/IMG]

If it isnt, where can I get it?

Anyway now is well working  wink

---

### Post by ronocdh on 2007-05-04
> **gagginaspinnata said:**
> this is my chipset :

[IMG]http://img413.imageshack.us/img413/3626/immagine2bb5.png[/IMG]

If it isnt, where can I get it?

Anyway now is well working  wink
I was interested in the results of **lspci**. (You may need to run **sudo update-pciids** if your chipset comes up as "unknown.")

---

### Post by stchman on 2007-05-04
> **gagginaspinnata said:**
> Hello everyone ):P  This is my first post :mrgreen:  First of all I would like to apologise for my not perfect english :) 

I've installed ubuntu 7.04 on a macbookpro core duo (didint mean core 2 duo) and I'm facing a lot of troubles trying to connect to internet via wifi. 
I heard about [madwifi]("www.madwifi.org") but it wont work :) . Doing *make* says:
```
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ sudo makeChecking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  HOSTCC  /home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: At top level:
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'main':
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode] Error 1
make[2]: *** [/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal] Error 2
make[1]: *** [_module_/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ 
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$
```

As you can see there is some errors


Than, doing *make isntall* it says:
```
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.20-15-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
test -d //lib/modules/2.6.20-15-generic/net || mkdir -p //lib/modules/2.6.20-15-generic/net
cp ath_pci.ko //lib/modules/2.6.20-15-generic/net
cp: cannot stat `ath_pci.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/gagginaspinnata/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath'
make: *** [install-modules] Error 1
gagginaspinnata@ubuntu:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ 


```

There is again some errors :( 

I've even tried this guide:


I'm not able to connect to internet via wireless :( 

There is anyone who would like to help me?

First off what kind of wireless card do you have?  I have procedures for getting Atheros and Broadcon 43xx cards working.

Broadcom - [http://www.stchman.com/install_ndis_broadcom.html](http://www.stchman.com/install_ndis_broadcom.html)

Atheros(madwifi) - [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

You have to have the build-essential package installed for compiling C programs (which make does)

sudo apt-get install build-essential

Follow one of these procedures and you should be up and running.

---

### Post by gagginaspinnata on 2007-05-04
> **ronocdh said:**
> I was interested in the results of **lspci**. (You may need to run **sudo update-pciids** if your chipset comes up as "unknown.")


```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)


```

I hope its clear 
stchman Thanks for your help, anyway, as you can read above, madwifi is now working :D

---

