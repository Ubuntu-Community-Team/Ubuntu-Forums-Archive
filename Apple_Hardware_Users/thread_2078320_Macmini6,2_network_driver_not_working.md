---
title: "Macmini6,2 network driver not working"
date: 2012-10-30
forum: Apple Hardware Users
---

### Post by ianneub on 2012-10-30
Howdy All,

I've been pulling my hair out trying to get the network working with my new mac mini. Any one else having issues installing Ubuntu 12.04 server on a macmini6,2 (Late 2012)?

Running lspci I see that the ethernet card is a Broadcom BCM57765.

I tried loading the tg3 driver, but it doesn't seem to do anything.

```
modeprobe tg3
```

```
dmesg | grep eth
``` reports nothing.

Any thoughts on where to go from here?

Thanks in advance.

---

### Post by ianneub on 2012-10-30
I was able to get it to work with newer drivers from Broadcom.

[http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php](http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php)

Compiled against kernel 3.2.0-32-generic works just fine.

---

### Post by superyounan1 on 2012-10-31
I have this same problem, I have the base model 2012 mac mini, neither wired or wireless works.

Would you kindly post instructions for how you got the module loaded?

---

### Post by ianneub on 2012-10-31
> **superyounan1 said:**
> Would you kindly post instructions for how you got the module loaded?

Sure.

I actually used a 2nd Ubuntu 12.04 install to do the follow steps, but you should be able to do it all on the mac mini if that is all you have access to. You will for sure need another computer though to download the driver.

First, make sure you have a build environment setup. You can do this on the mac mini during the install process. It will ask what packages to install, you need to select the last option to choose additional packages.

Find the build-essentials package and hit +, then g to install it. You will also need the unzip package.

You will also need the linux-source package. I'm not sure if that's on the install iso or not. If it is not, then you'll need to download it from another machine and copy it over and then install it.

At this point the machine should be installed and you should have a sane build environment with the linux kernel sources.

Download the Broadcom drivers from here:
[http://www.broadcom.com/support/license.php?file=570x/linux-3.124c.zip](http://www.broadcom.com/support/license.php?file=570x/linux-3.124c.zip)

Unzip the downloaded file.

Under the Server/Linux/Driver directory untar this file: tg3-3.124c.tar.gz

Then, inside that directory run ```
make
```

If that all works then you should have a tg3.ko file in that directory.

Copy that file to /lib/modules/`uname -r`/kernel/drivers/net/ethernet/broadcom/tg3.ko

Then run ```
modprobe tg3
```

You should be able to see that it worked by checking ```
dmesg | grep eth0
```

If you see some text after that command you're good to go.

Let me know if you have any questions.

---

### Post by superyounan1 on 2012-11-01
Sigh, I never once compiled something from source in linux without running into a dozen errors or coming up against an endless list of missing dependencies.

I'm using a live session with persistence (casper), so I popped it into a dell laptop (goes online fine, btw) and tried to compile, got this:

```

ubuntu@ubuntu:~/Downloads/Server/Linux/Driver/tg3-3.124c$ make
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.o
/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.c:96:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[2]: *** [/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.o] Error 1
make[1]: *** [_module_/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [default] Error 2

```

I do have linux headers installed, but somehow system.h is missing? I did some googling and found a very similar issue affecting nvidia drivers, though I don't think they're related.

Anyway I have small intel atom / ion htpc running 12.04, tried compiling there and got this:

```

/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_phy_autoneg_cfg’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:4338:2: error: implicit declaration of function ‘ethtool_adv_to_mii_adv_t’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:4346:3: error: implicit declaration of function ‘ethtool_adv_to_mii_ctrl1000_t’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_phy_pull_config’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:4614:3: error: implicit declaration of function ‘mii_adv_to_ethtool_adv_t’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:4631:4: error: implicit declaration of function ‘mii_ctrl1000_to_ethtool_adv_t’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:4642:4: error: implicit declaration of function ‘mii_adv_to_ethtool_adv_x’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_phy_copper_fetch_rmtadv’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:4787:3: error: implicit declaration of function ‘mii_stat1000_to_ethtool_lpa_t’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:4793:2: error: implicit declaration of function ‘mii_lpa_to_ethtool_lpa_t’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_setup_fiber_mii_phy’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:5913:3: error: implicit declaration of function ‘ethtool_adv_to_mii_adv_x’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_tx’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:6684:2: error: implicit declaration of function ‘netdev_tx_completed_queue’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_start_xmit’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:8263:2: error: implicit declaration of function ‘netdev_tx_sent_queue’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_free_rings’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:8705:3: error: implicit declaration of function ‘netdev_tx_reset_queue’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_rss_init_dflt_indir_tbl’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:9903:3: error: implicit declaration of function ‘ethtool_rxfh_indir_default’ [-Werror=implicit-function-declaration]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: At top level:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:14512:2: error: unknown field ‘get_rxfh_indir_size’ specified in initializer
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:14512:2: warning: initialization from incompatible pointer type [enabled by default]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:14512:2: warning: (near initialization for ‘tg3_ethtool_ops.set_rxnfc’) [enabled by default]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:14514:2: warning: initialization from incompatible pointer type [enabled by default]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:14514:2: warning: (near initialization for ‘tg3_ethtool_ops.get_rxfh_indir’) [enabled by default]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:14515:2: warning: initialization from incompatible pointer type [enabled by default]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:14515:2: warning: (near initialization for ‘tg3_ethtool_ops.set_rxfh_indir’) [enabled by default]
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c: In function ‘tg3_init_one’:
/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.c:17926:2: error: unknown type name ‘netdev_features_t’
cc1: some warnings being treated as errors
make[2]: *** [/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c/tg3.o] Error 1
make[1]: *** [_module_/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make: *** [default] Error 2

```

I'll do some searching tomorrow for more options.

---

### Post by rcsheets on 2012-11-01
> **superyounan1 said:**
> 
I'm using a live session with persistence (casper), so I popped it into a dell laptop (goes online fine, btw) and tried to compile, got this:

```

ubuntu@ubuntu:~/Downloads/Server/Linux/Driver/tg3-3.124c$ make
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.o
/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.c:96:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[2]: *** [/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c/tg3.o] Error 1
make[1]: *** [_module_/home/ubuntu/Downloads/Server/Linux/Driver/tg3-3.124c] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [default] Error 2

```

I do have linux headers installed, but somehow system.h is missing? I did some googling and found a very similar issue affecting nvidia drivers, though I don't think they're related.


Note that you're compiling against a different version of the kernel than the example above. I'm guessing you are using quantal, whereas the other example was using precise. It seems that asm/system.h was removed somewhat recently, at least on x86.

> 
Anyway I have small intel atom / ion htpc running 12.04, tried compiling there and got this:

```

[...]
make[1]: *** [_module_/home/(replaced)/Desktop/Server/Linux/Driver/tg3-3.124c] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-32-generic'
make: *** [default] Error 2

```

Here you're back to 3.2.0, which I imagine is on precise.

I have not tried building the tg3 driver on precise, but I did manage to get it working on quantal on my macmini6,1. I made the following changes to the driver sources:

1. At line 96 of tg3.c, simply comment out the inclusion of asm/system.h:
```

/* #include <asm/system.h> */

```

2. At line 14534 of tg3.c, I surrounded the following two lines of code ...
```

	.get_sg			= ethtool_op_get_sg,
	.set_sg			= ethtool_op_set_sg,

```
... with a preprocessor directive reflecting the fact that get_sg and set_sg were deprecated in (I believe) Linux 3.0 and removed sometime after that. Here's what that looks like:
```

#if (LINUX_VERSION_CODE < 0x30000)
	.get_sg			= ethtool_op_get_sg,
	.set_sg			= ethtool_op_set_sg,
#endif
```

3. Finally, since the API the driver tries to use to do TCP Segment Offloading went through the same deprecation and removal as get_sg and set_sg, and since I have no idea how to modify the driver to use the new API, I attempted to remove the TSO support entirely by changing line 3 of tg3_firmware.h from ...
```

#ifdef NETIF_F_TSO
```
... to ...
```

#ifdef XXXXNETIF_F_TSO
```

That resulted in a driver that's working for me. Clearly it's just a quick hack, but it got the network up on my new Mac mini, so it's good enough for me for now. Hopefully someone who knows more about Ethernet drivers can provide a proper patch, or perhaps Broadcom will update their driver sometime soon.

---

### Post by ianneub on 2012-11-01
> **superyounan1 said:**
> Sigh, I never once compiled something from source in linux without running into a dozen errors or coming up against an endless list of missing dependencies.


I hear ya. I redid what I did before and wrote down everything this time, maybe this will help:

Starting with a fresh install of Ubuntu 12.04 Server on a x86_64 VM

```

apt-get install build-essential linux-source linux-server unzip

wget !snip!

unzip linux-3.124c.zip?dl=1

cd Server/Linux/Driver/
tar zxf tg3-3.124c.tar.gz

cd tg3-3.124c

make

```

At that point the build was successful and I had a tg3.ko file ready to go. The only other problem was that this was compiled against kernel version 3.2.0-32-generic. This is not the standard kernel installed with the 12.04 install CD, so you have to upgrade the kernel before you can use the .ko file.

I installed the kernel on the mac mini and copied the tg3.ko file to /lib/modules/3.2.0-32-generic/kernel/drivers/net/ethernet/broadcom/tg3.ko

Here is a zip file that contains the compiled tg3.ko module as well as the deb packages to upgrade the mac mini to the right kernel.

!snip!

Good luck!

---

### Post by superyounan1 on 2012-11-01
So before I checked this thread this morning I installed "firmware-b43-installer" and "linux-firmware-nonfree" - one of these two got me onto wifi, although scans weren't finding 802.11n networks. Wired networking also was still not working.

I tried compiling the module again with rcsheet's advice (post #6) to simply comment out the include of asm/system.h and the the other changes, this worked. I moved the binary tg3.ko to /lib/modules/`uname -r`/kernel/drivers/net/ethernet/broadcom/, ran ```
sudo modprobe tg3
```
and viola, a "wired connection established" notification popped up. 

```

ubuntu@ubuntu:~$ dmesg | grep eth0
[  736.089264] pcieport 0000:00:1c.0: eth0: Tigon3 [partno(BCM957766a) rev 57766001] (PCI Express) MAC address (redacted)
[  736.089271] pcieport 0000:00:1c.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[  736.089275] pcieport 0000:00:1c.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[  736.089280] pcieport 0000:00:1c.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]

```

I'll try this more often... missing header file? Missing library? Fine, just erase or comment that part of the code calling it. :)

Thank you both, ianneub and rcsheets.

---

### Post by superyounan1 on 2012-11-01
Additional information:

Based on ianneub's instructions for 12.04 in post #7 I went back to my 12.04 pc and installed linux-source and linux-server, then tried compiling again the source I downloaded originally from broadcom directly and got the same warnings and errors I posted in post #5. I'm using kernel version 3.2.0-32-generic on that machine.

I didn't want to install kernel 3.2.0-32 on the persistent live session I'm using on the mac mini because that's 12.10 with 3.5.0-17-generic. 

Thanks for going through the trouble of posting the package and compiled kernel to dropbox, but I doubt I would've felt comfortable doing that even if I hadn't gotten it going.

---

### Post by ianneub on 2012-11-01
> **superyounan1 said:**
> Thanks for going through the trouble of posting the package and compiled kernel to dropbox, but I doubt I would've felt comfortable doing that even if I hadn't gotten it going.

No sweat, I totally understand that. I wouldn't either :)

I ended up throwing in the towel on getting this macmini6,2 working under 12.04. I also had problems with the SD card reader not working as well as some USB issues.

Unfortunately I don't have the time to work through the issues and I'll just use OS X for this server :-(

If anyone ever gets a good working system and wants to post info on how to duplicate it I'd love to try it!

---

### Post by rcsheets on 2012-11-01
> **superyounan1 said:**
> I tried compiling the module again with rcsheet's advice (post #6) to simply comment out the include of asm/system.h and the the other changes, this worked. I moved the binary tg3.ko to /lib/modules/`uname -r`/kernel/drivers/net/ethernet/broadcom/, ran ```
sudo modprobe tg3
```
and viola, a "wired connection established" notification popped up.
I'm glad to know this has now worked for more than just me. One minor difference though is that (though I didn't mention this in my earlier post) I installed the module with 'sudo make install'.

> I'll try this more often... missing header file? Missing library? Fine, just erase or comment that part of the code calling it. :)

Somehow I doubt that approach works very often. ;)

---

### Post by Gompa on 2012-11-01
iam working on a mac mini 6.1 ? (its with a ivy bridge proc so i assume its the same)

it got it to work on the 3.5 kernel from [this tread]("http://ubuntuforums.org/showthread.php?t=1998963") with the drivers from broadcom by editing the files described

this is the fixed source : [DOWNLOAD]("http://castlebravo.h-bomb.nl/tg3-3.124c.zip") 

i take no responsibility i only did what was mentioned in this tread earlier

---

### Post by rcsheets on 2012-11-01
> **Gompa said:**
> iam working on a mac mini 6.1 ? (its with a ivy bridge proc so i assume its the same)
The macmini6 models are all the models released last month. macmini6,1 is the Core i5 model, macmini6,2 is the Core i7 model, and macmini6,3 is the Mac mini Server (which also has a Core i7).

I believe all of them have the same network hardware.

---

### Post by nick58b on 2012-11-04
Here's some DKMS instructions to auto-build and install the tg3 module automatically on later kernel updates. They work for me, but I'm not a DKMS expert.

[LIST]
[*]Install dkms, build-essential, linux-headers, linux-source, etc
[*]Download the Linux tg3 module from [http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php]("http://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php")
[*]Extract it
[*]Navigate to Server/Linux/Driver/tg3-3.124c.tar.gz
[*]Extract that file to /usr/src/tg3-3.124c/src/
[*]Create a file called /usr/src/tg3-3.124c/dkms.conf with the following contents:
[/LIST]

```

PACKAGE_NAME=tg3
PACKAGE_VERSION=3.124c
CLEAN="make -C src/ clean"
MAKE="cd src/ && make BUILD_KERNEL=${kernelver} KVER=${kernelver}"
BUILT_MODULE_NAME[0]="tg3"
BUILT_MODULE_LOCATION[0]="src/"
DEST_MODULE_LOCATION[0]=/updates
AUTOINSTALL=yes

```

After that run the DKMS commands to install it:
```

sudo dkms add -m tg3 -v 3.124c
sudo dkms build -m tg3 -v 3.124c
sudo dkms install -m tg3 -v 3.124c

```

Then reboot or:
```

sudo modprobe tg3

```

You should now have a working tg3 network module that survives kernel updates.

---

### Post by tonyoz on 2013-03-13
I have tried this promising solution but I am having difficulties (probably due to my being new to Ubuntu no doubt).

The first problem I encountered was that it wasn't obvious that DKMS needs to be installed first from here:

[http://linux.dell.com/dkms/](http://linux.dell.com/dkms/)

After that DKMS would work but I got the following error after trying to use sudo dkms. I have no idea what this means or what to do next before  trying install. Any ideas, please advise:

DKMS make.log for tg3-3.124c for kernel 3.8.2-030802-generic (x86_64)
Wed Mar 13 20:17:56 WST 2013
sh makeflags.sh /lib/modules/3.8.2-030802-generic/build > tg3_flags.h
make -C /lib/modules/3.8.2-030802-generic/build SUBDIRS=/var/lib/dkms/tg3/3.124c/build/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.8.2-030802-generic'
CC [M] /var/lib/dkms/tg3/3.124c/build/src/tg3.o
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:96:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[2]: *** [/var/lib/dkms/tg3/3.124c/build/src/tg3.o] Error 1
make[1]: *** [_module_/var/lib/dkms/tg3/3.124c/build/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.8.2-030802-generic'
make: *** [default] Error 2

---

### Post by tonyoz on 2013-03-13
I have since tried rcheets changes to driver files in post 6 with Ubuntu updated to kernel 3.7.10.
Unfortunately I still have no ethernet and now get the following errors.

Would appreciate suggestions on how to fix this:

DKMS make.log for tg3-3.124c for kernel 3.7.10-030710-generic (x86_64)
Thu Mar 14 10:11:24 WST 2013
sh makeflags.sh /lib/modules/3.7.10-030710-generic/build  > tg3_flags.h
make -C /lib/modules/3.7.10-030710-generic/build SUBDIRS=/var/lib/dkms/tg3/3.124c/build/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.7.10-030710-generic'
  CC [M]  /var/lib/dkms/tg3/3.124c/build/src/tg3.o
In file included from /var/lib/dkms/tg3/3.124c/build/src/tg3.h:13:0,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:119:
/var/lib/dkms/tg3/3.124c/build/src/tg3_compat.h:1953:21: error: conflicting types for &#8216;ethtool_cmd_speed&#8217;
In file included from include/linux/ethtool.h:16:0,
                 from include/linux/netdevice.h:42,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:48:
include/uapi/linux/ethtool.h:61:21: note: previous definition of &#8216;ethtool_cmd_speed&#8217; was here
In file included from /var/lib/dkms/tg3/3.124c/build/src/tg3.h:13:0,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:119:
/var/lib/dkms/tg3/3.124c/build/src/tg3_compat.h:1960:21: error: conflicting types for &#8216;ethtool_cmd_speed_set&#8217;
In file included from include/linux/ethtool.h:16:0,
                 from include/linux/netdevice.h:42,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:48:
include/uapi/linux/ethtool.h:53:20: note: previous definition of &#8216;ethtool_cmd_speed_set&#8217; was here
/var/lib/dkms/tg3/3.124c/build/src/tg3.c: In function &#8216;tg3_get_invariants&#8217;:
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:16502:28: error: &#8216;struct pci_bus&#8217; has no member named &#8216;subordinate&#8217;
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:16530:28: error: &#8216;struct pci_bus&#8217; has no member named &#8216;subordinate&#8217;
/var/lib/dkms/tg3/3.124c/build/src/tg3.c: In function &#8216;tg3_init_one&#8217;:
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:18013:47: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:18013:2: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:18013:2: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/tg3/3.124c/build/src/tg3.c: At top level:
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:11300:13: warning: &#8216;tg3_reset_task&#8217; defined but not used [-Wunused-function]
make[2]: *** [/var/lib/dkms/tg3/3.124c/build/src/tg3.o] Error 1
make[1]: *** [_module_/var/lib/dkms/tg3/3.124c/build/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7.10-030710-generic'
make: *** [default] Error 2

---

### Post by sparklyballs on 2013-03-18
> **tonyoz said:**
> I have since tried rcheets changes to driver files in post 6 with Ubuntu updated to kernel 3.7.10.
Unfortunately I still have no ethernet and now get the following errors.

Would appreciate suggestions on how to fix this:

DKMS make.log for tg3-3.124c for kernel 3.7.10-030710-generic (x86_64)
Thu Mar 14 10:11:24 WST 2013
sh makeflags.sh /lib/modules/3.7.10-030710-generic/build  > tg3_flags.h
make -C /lib/modules/3.7.10-030710-generic/build SUBDIRS=/var/lib/dkms/tg3/3.124c/build/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.7.10-030710-generic'
  CC [M]  /var/lib/dkms/tg3/3.124c/build/src/tg3.o
In file included from /var/lib/dkms/tg3/3.124c/build/src/tg3.h:13:0,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:119:
/var/lib/dkms/tg3/3.124c/build/src/tg3_compat.h:1953:21: error: conflicting types for ‘ethtool_cmd_speed’
In file included from include/linux/ethtool.h:16:0,
                 from include/linux/netdevice.h:42,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:48:
include/uapi/linux/ethtool.h:61:21: note: previous definition of ‘ethtool_cmd_speed’ was here
In file included from /var/lib/dkms/tg3/3.124c/build/src/tg3.h:13:0,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:119:
/var/lib/dkms/tg3/3.124c/build/src/tg3_compat.h:1960:21: error: conflicting types for ‘ethtool_cmd_speed_set’
In file included from include/linux/ethtool.h:16:0,
                 from include/linux/netdevice.h:42,
                 from /var/lib/dkms/tg3/3.124c/build/src/tg3.c:48:
include/uapi/linux/ethtool.h:53:20: note: previous definition of ‘ethtool_cmd_speed_set’ was here
/var/lib/dkms/tg3/3.124c/build/src/tg3.c: In function ‘tg3_get_invariants’:
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:16502:28: error: ‘struct pci_bus’ has no member named ‘subordinate’
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:16530:28: error: ‘struct pci_bus’ has no member named ‘subordinate’
/var/lib/dkms/tg3/3.124c/build/src/tg3.c: In function ‘tg3_init_one’:
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:18013:47: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:18013:2: error: ‘INIT_WORK’ undeclared (first use in this function)
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:18013:2: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/tg3/3.124c/build/src/tg3.c: At top level:
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:11300:13: warning: ‘tg3_reset_task’ defined but not used [-Wunused-function]
make[2]: *** [/var/lib/dkms/tg3/3.124c/build/src/tg3.o] Error 1
make[1]: *** [_module_/var/lib/dkms/tg3/3.124c/build/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.7.10-030710-generic'
make: *** [default] Error 2




i have a patch file that works for kernel 3.7.x for the tg3 driver. 

i'm not sure how to post links to files on here though. 

i'm looking for a similar patch for kernel 3.8.x for this driver.

---

### Post by cricketnut on 2013-03-23
Thank you so much for the info. Now I have a mac mini with ubuntu 12.04.2 up an running.

---

### Post by TheBeechnut on 2013-03-23
> **cricketnut said:**
> Thank you so much for the info. Now I have a mac mini with ubuntu 12.04.2 up an running.

Hi --

You'll forgive me if I'm confused how you got from the stack trace to the above quote. Did you apply a patch? If so, would you provide a link or any further information?

I'm running on a Mac Mini 6,1 / Ubuntu 12.10 / 3.5.x kernel, getting the following errors upon `sudo dkms build -m tg3 -v 3.124c`. (All packages installed, `dkms add` ran perfectly.)

Terminal
----------
cd src/ && make BUILD_KERNEL=3.5.0-17-generic KVER=3.5.0-17-generic....(bad exit status: 2)
ERROR (dkms apport): binary package for tg3: 3.124c not found
Error! Bad return status for module build on kernel: 3.5.0-17-generic (i686)
Consult /var/lib/dkms/tg3/3.124c/build/make.log for more information.

make.log
----------
DKMS make.log for tg3-3.124c for kernel 3.5.0-17-generic (i686)
Sat Mar 23 16:29:08 EDT 2013
sh makeflags.sh /lib/modules/3.5.0-17-generic/build  > tg3_flags.h
make -C /lib/modules/3.5.0-17-generic/build SUBDIRS=/var/lib/dkms/tg3/3.124c/build/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-17-generic'
  CC [M]  /var/lib/dkms/tg3/3.124c/build/src/tg3.o
/var/lib/dkms/tg3/3.124c/build/src/tg3.c:96:24: fatal error: asm/system.h: No such file or directory
compilation terminated.
make[2]: *** [/var/lib/dkms/tg3/3.124c/build/src/tg3.o] Error 1
make[1]: *** [_module_/var/lib/dkms/tg3/3.124c/build/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-17-generic'
make: *** [default] Error 2

---

### Post by JoeBlack2k on 2013-04-01
First of all you want to be at 3.8.5 because of the sound support and lots of usb3 fixes!


cd /tmp 
wget [http://dl.dropbox.com/u/47950494/upubuntu.com/kernel-3.8.5](http://dl.dropbox.com/u/47950494/upubuntu.com/kernel-3.8.5) -O kernel-3.8.5 
chmod +x kernel-3.8.5 
sudo sh kernel-3.8.5 
sudo reboot




1. Download your kernel source

[https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.8.5.tar.xz](https://www.kernel.org/pub/linux/kernel/v3.x/linux-3.8.5.tar.xz)

2. Put the kernel source on a usb stick (cause you don't have internet on the mac mini..)

3. mount the usb stick:

sudo mkdir /media/USB 
sudo mount /dev/sdb /media/USB (sda is your internal drive so sdb would be your first usb disk)

4. untar the file:

tar xz linux-3.8.5.tar.xz

5. edit the broadcom file:

cd /media/USB/linux-3.8.5/Drivers/net/ethernet/broadcom/
sudo nano tg3.c

6. add the macmini pci info:

look for:   {PCI_DEVICE(PCI_VENDOR_ID_BROADCOM, TG3PCI_DEVICE_TIGON3_57762)}, and underneath cp this:

{PCI_DEVICE(PCI_VENDOR_ID_BROADCOM, TG3PCI_DEVICE_TIGON3_57766)},
{PCI_DEVICE(PCI_VENDOR_ID_BROADCOM, TG3PCI_DEVICE_TIGON3_57782)},
{PCI_DEVICE(PCI_VENDOR_ID_BROADCOM, TG3PCI_DEVICE_TIGON3_57786)},

7. save the file (ctrl+x YES)

8. copy your current Module.symvers

sudo cp /usr/src/linux-headers-3.8.5-030805-generic/Module.symvers /media/USB/linux-3.8.5/

9. make stuff:
cd /media/USB/linux-3.8.5/
make clean
make oldconfig
make scripts
make prepare
cd drivers/net/ethernet/broadcom/
make -C /media/USB/linux-3.8.5 SUBDIRS=$PWD modules

10. install new driver and activate:

sudo cp /media/USB/drivers/net/ethernet/broadcom/tg3.ko /lib/modules/${kernelversion}/kernel/drivers/net/ethernet/broadcom/
sudo modprobe tg3


NICE INTERNET!

[21321.011542] tg3.c:v3.128 (December 03, 2012)
[21321.121927] tg3 0000:01:00.0 eth0: Tigon3 [partno(BCM957766a) rev 57766001] (PCI Express) MAC address a8:20:66:50:dd:a2

---

