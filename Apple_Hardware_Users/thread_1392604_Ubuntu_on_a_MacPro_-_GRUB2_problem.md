---
title: "Ubuntu on a MacPro - GRUB2 problem"
date: 2010-01-28
forum: Apple Hardware Users
---

### Post by Leejin on 2010-01-28
Greetings,

after several searches through this Board, AppleTalk, and exhaustive google searches I'm out of any ideas how to solve the following Problem:

I installed rEFIt on MacOS X Snow Leopard.
Later on I created a partition with BootCamp.

I inserted the Ubuntu Linux CD (64-Bit), and installed it - one attemp via LiveCD , another one via "Standard" installation. 

The installation itself went fine, I manually created on a separate hard drive a sdd1 Partition (ext3) for Linux, and about 20GB for Swap.(I also tried ext4 before - but it actually seems not to work properly with rEFIt).

Once I tried to install GRUB2 on the MBR, which cracked my rEFIt and MacOS booted up with a folder and a questionmark (which actually means that it couldn't find OS X). I fixed this problem by inserting the rEFIt image and running the partition tool.

In a second attemp I installed the Bootloader on the ext3 partition of Ubuntu.

When I do start now the system, rEFIt appears. I choose the "Legacy Partition" ...but what actually ALWAYS appears is :


GRUB.


,....that's all, just GRUB ...and I have absolutely no idea how to solve this problem or what this "GRUB" message actually means.

Thanks in advance for any hints about this weird problem.

With best regards

Leejin

---

### Post by linuxopjemac on 2010-01-28
try to reinstall grub, from the liveCD:

```
grub-install /dev/sdd 
``` (don't do sdd1)

(assuming sdd is your drive)...

---

### Post by Leejin on 2010-01-29
Hi,

unfortunately it does not work. I get the following error msg:

-----------------------

ubuntu@ubuntu:/dev$ sudo grub-install /dev/sdd
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

-----------------------

No matter what I do, this message appears almost every time when I try to install or setup GRUB. Also a reinstallation did not worked.

Under Disk Utility I also get the correct name:
/dev/sdd

Any ideas?

Regards and thanks for the help 

Leejin

---

### Post by linuxopjemac on 2010-01-29
do you have four drives attached then ? what happens with

```
grub-probe --help
```

[http://grub.enbug.org/FranklinPiat/grub-probe.manpage](http://grub.enbug.org/FranklinPiat/grub-probe.manpage)

---

### Post by Leejin on 2010-01-29
jepp, I got 4 HDD attached to it, while 3 do belong to OSX and a 1 TB one belongs to Ubuntu.

When I type in grub-probe --help I get the following:

-------------------------

ubuntu@ubuntu:/dev$ grub-probe --help
Usage: grub-probe [OPTION]... [PATH|DEVICE]

Probe device information for a given path (or device, if the -d option is given).

  -d, --device              given argument is a system device, not a path
  -m, --device-map=FILE     use FILE as the device map [default=/boot/grub/device.map]
  -t, --target=(fs|fs_uuid|drive|device|partmap|abstraction)
                            print filesystem module, GRUB drive, system device, partition map module or abstraction module [default=fs]
  -h, --help                display this message and exit
  -V, --version             print version information and exit
  -v, --verbose             print verbose messages

Report bugs to <bug-grub@gnu.org>.


----------------

However, if I also try to make a complete reinstall of GRUB the following message appears:

----------------

ubuntu@ubuntu:/dev$ sudo grub-install --root-directory=/media/5bf05320-d62e-4a99-ba48-1aeca0f9c946 /dev/sdd
grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly

---------------

Best regards

Leejin

---

### Post by linuxopjemac on 2010-01-29
I read a lot of similar errors like you on the net. Apparently Grub2 is not so good yet. Here one guy found a solution:



> When trying to install grub2 (whatever snapshot was current as of today) I kept getting the following error:

$ sudo /sbin/grub-setup -v --directory=/media/sysrescd/boot/grub \
  --device-map=/media/sysrescd/boot/grub/device.map -r '(hd1,1)' '(hd1)'
.... snip ...
grub-setup: error: Cannot read `/media/sysrescd/boot/grub/core.img' correctly

The error was not very descriptive because grub was apparently able to read other important files like boot.img and such. The filesystem on my USB stick was identical (feature wise) to the /boot on my HDD — ext2. And the same command worked just fine for installing to my hard disk.

Digging through the code revealed where the problem is. The error was caused by grub-setup being unable to embed core.img in the MBR. The core.img prepared by grub-mkimage was 25k big. That is about 50 sectors. The first partition on my hard disk starts on sector 63. The first partition on my USB stick was starting on sector 32 (or was it 31?). 32 < 50 => core.img cannot be embedded. If only the error message had been a little clearer it would have saved me some headache.

Destroying the first partition on the USB stick and recreating it starting from sector 63 fixed the problem.


personally, I would take GRUB1, as it is more stable.

---

### Post by Leejin on 2010-01-29
Thank you very much - that saves me a lot of time :)

Could you tell me how to 

1. Uninstall Grub 2 and
2. Install Grub 1 via Live CD ?

Or do I have to reinstall Ubuntu ? (And if yes, are there any options to install GRUB 1 instead of GRUB 2 ?)

Best regards

Leejin

---

### Post by linuxopjemac on 2010-01-29
The easiest way, which I would do, seems more work, but is easier. I would reinstall Ubuntu starting from Jaunty (9.04). It installs Grub1 by default. Then you put in your Karmic liveCD and install Karmic on the partition where Jaunty resided, having ext4. This will give you Karmic with Grub1.97 (~beta4 I think), just like I have on my MacBook. This works great.

---

### Post by linuxopjemac on 2010-01-29
I also see some important data on the [https://help.ubuntu.com/community/MacPro](https://help.ubuntu.com/community/MacPro) site:

> {X} WARNING: It is important to install the Grub boot loader on the Ubuntu partition (e.g. /dev/sda3), instead of the default disk root. This is done by selecting the Advanced options after partitioning and before the actual installation.

By default, Ubuntu installs the GRUB boot loader on the disk root (e.g. dev/sda). This does modify the EFI and GUID boot loader, which then potentially removes your Mac OSX boot.... <:( You must specify a partition for GRUB installation, e.g. /dev/sda3

I guess the remark is only relevant if you have OSX on that partition where Linux is to be installed.

---

### Post by ipina on 2010-01-29
Hi, I successfully installed Karmic 9.10 on a MacPro with four drives (sda, ..., sdd), being sdc the target of my installation. It was important the way this disk is formatted. In Mac OS X and Disk Utility, erase it choosing a MS-DOS format, write on it a folder in order for the disk to be seen by Ubuntu, run live CD and be sure /dev/sdd (in your case) is seen. Then 'sudo dd if=/dev/zero of=/dev/sdd bs=512 count=1'. As a consequence, your disk is clean and ready for install Grub2. Hope this helps.

---

### Post by Leejin on 2010-01-29
Still the GRUB Problem ....I installed Ubuntu 9.04 - no luck ...it still brings up this :


GRUB _


I installed the bootloader on the Ubuntu Partition ...but still no luck. Do you got any ideas ?

Best regards

Leejin

---

### Post by linuxopjemac on 2010-01-29
did you try > Hi, I successfully installed Karmic 9.10 on a MacPro with four drives (sda, ..., sdd), being sdc the target of my installation. It was important the way this disk is formatted. In Mac OS X and Disk Utility, erase it choosing a MS-DOS format, write on it a folder in order for the disk to be seen by Ubuntu, run live CD and be sure /dev/sdd (in your case) is seen. Then 'sudo dd if=/dev/zero of=/dev/sdd bs=512 count=1'. As a consequence, your disk is clean and ready for install Grub2. Hope this helps. as was posted earlier ?

---

### Post by Leejin on 2010-01-29
Shall I install than the Bootloader (during Ubuntu installation process) within the ubuntu partition or just leave the options as they are ? 

Best regards

Leejin

---

### Post by linuxopjemac on 2010-01-29
I think, as you don't install OSX on said partition, that you can leave it as it is and install it in the MBR on /dev/sdd.

---

### Post by Leejin on 2010-01-29
Tested - does not work - same Message:


GRUB _



while the "_" blinking


...maybe the MBR is not set ?

I have to say that I use rEFIt 

EDIT:Is there a tool/way of auto detecting and "repairing" grub 2 ?

Best regards

Leejin

---

### Post by linuxopjemac on 2010-01-29
I am lost. I can only give you a good GRUB2 site. You are on your own now...

[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

---

### Post by linuxopjemac on 2010-01-29
some links I found
[http://saladwithsteve.com/2008/02/ubuntu-on-mac-pro.html](http://saladwithsteve.com/2008/02/ubuntu-on-mac-pro.html)
[http://www.kapsi.de/blog/?p=3](http://www.kapsi.de/blog/?p=3)

One other thing I totally forgot, did you sync  the partition table with the partition tool in rEFIT? You can also try to reinstall Grub after that with

```
sudo grub-install /dev/sdd
```

I don't know if it will make a difference, but you can try.

---

