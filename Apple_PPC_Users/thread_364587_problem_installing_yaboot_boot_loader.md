---
title: "problem installing: yaboot boot loader"
date: 2007-02-18
forum: Apple PPC Users
---

### Post by Mars8082686 on 2007-02-18
I am installing PPC Ubuntu on an external drive. The drive is a 4 gig ipod hard drive; I completely wiped it with dd if=/dev/zero of=/dev/sda. Anyways, I go to install and it goes through the entire process and gets ~ 95% done, then this error message pops up (I've gotten it both times I've tried to install)
```

The installation of the yaboot boot loader failed.

Check /var/log/syslog or see virtual console 4 for the details.

Warning: Your system may be unbootable!

```
How can I fix this?

---

### Post by BryannMelvin on 2007-02-18
I haven't tried this myself....from my reading I think you need the latest yaboot froma Edgy or feisty and  it has to be a Firewire external drive. What I have read sometimes conflicts. Otherwise you'll need to build a kernel I think

---

### Post by Mars8082686 on 2007-02-18
Here is some more information that it gave me, if it's any help
```

We're sorry; the installer crashed. Please file a new bug report at 
https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug (do not attach your details to any 
existing bug) and a developer will attend to the problem as soon as possible. 
To help the developers understand what went wrong, include the following detail in your bug report, 
and attach the files /var/log/syslog and /var/log/partman:


Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 385, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1171, in configure_bootloader
    raise InstallStepError(
InstallStepError: YabootInstaller failed with code 1

```

I can provide the logs if they're need. The ipod is connected via firewire, so would that nessacerily make it a firewire drive?

---

### Post by grazie on 2007-02-18
Mars8082686,

I'm assuming you're using Edgy on a Desktop CD. If not please let us know. Also, you've not said whether you've set you the bootstrap partition or you've let the installer do everything automatically. Although the installer thinks there's a bug, you may not have done the setup correctly. Post the details.

If it is a bug, you've been lucky in getting a very good description of what's gone wrong which is not that common. You may be lucky in that the bug has been fixed already. To check whether it has, you could update the installer and yaboot by using synaptic before starting the installation. However, you almost certainly will not be able to update everything. If you need some help in knowing what to update, do the following in terminal and post the output from the 2nd command below on this thread
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```
When asked Y/N to installing the list of packages, enter N. 

If there are installer & yaboot updates to pick up, once they've been downloaded, do the install again. However, there's no guarantee the problem will be fixed. If not, do exactly what the log tells you to do. If this bug effects all platforms, it will be fixed pretty quickly. If it's PPC specific, you may have to wait a while.

Another potential workaround is to do an install to a standard disk and copy the system to the fireware drive and setup yaboot yourself.

Incidentally, I wouldn't recommend using the dd if=/dev/zero of=/dev/sda in future on Mac disks, as this zaps the partition table. Gparted is great and will nearly always cope with setting up your partitions correctly.

---

### Post by Mars8082686 on 2007-02-18
I am using Ubuntu 2.6.17-10. I just downloaded the iso yesterday and I am pretty sure it is the latest release. I am letting to installer to all my partitioning from a blank drive. At first I thought it ran out of memory but when I did an df on my drive the 95 percent done install only used 60% of my disk space. (4gig ipod hard drive).

here is the result from the apt-get
```
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  linux-headers-2.6.17-11 linux-headers-2.6.17-11-powerpc
  linux-headers-2.6.17-11-powerpc64-smp linux-image-2.6.17-11-powerpc
  linux-image-2.6.17-11-powerpc64-smp
  linux-restricted-modules-2.6.17-11-powerpc
  linux-restricted-modules-2.6.17-11-powerpc64-smp
The following packages will be upgraded:
  avahi-daemon bind9-host dbus dbus-1-utils dnsutils evince firefox
  firefox-gnome-support gdm gnupg info libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core4 libavahi-glib1 libbind9-0 libdbus-1-3
  libdns21 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgtop2-7 libgtop2-common libisc11 libisccc0 libisccfg1
  libkrb53 liblwres9 libmagick9 libmono-cairo1.0-cil libmono-corlib1.0-cil
  libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil
  libmono-sqlite1.0-cil libmono-system-data1.0-cil libmono-system-web1.0-cil
  libmono-system1.0-cil libmono0 libmono1.0-cil libnspr4 libnss3 libpng12-0
  libpoppler1 libpoppler1-glib libsmbclient libsoup2.2-8
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-powerpc
  linux-headers-2.6.17-10-powerpc64-smp linux-headers-powerpc
  linux-headers-powerpc64-smp linux-image-2.6.17-10-powerpc
  linux-image-2.6.17-10-powerpc64-smp linux-image-powerpc
  linux-image-powerpc64-smp linux-powerpc linux-powerpc64-smp
  linux-restricted-modules-2.6.17-10-powerpc
  linux-restricted-modules-2.6.17-10-powerpc64-smp
  linux-restricted-modules-common linux-restricted-modules-powerpc
  linux-restricted-modules-powerpc64-smp mono-common mono-gac mono-jit
  mono-runtime poppler-utils samba-common screen smbclient tar w3m
  xserver-xorg-core
77 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 166MB of archives.
After unpacking 269MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

---

### Post by didg on 2007-02-18
What's in  /proc/scsci/scsi ?
If you have something like:
Type:   Direct-Access-RBC 
for the ipod it doesn't work because opath (called by mkofboot) expects Direct-Access for drives and is confused by -RBC.

---

### Post by grazie on 2007-02-18
Unfortunately, there's no sign of any updates for ubiquity (the installer) or yaboot, so you're out of luck. You can double check this yourself by searching for them in Synaptic after booting the Live CD. Report your installation failure as a bug as described. If you can demonstrate the same failure on x86, I'd imagine it would get fixed a lot more quickly.

If I were you, and I needed Ubuntu on the external drive now, I'd install to a standard  internal HD and move the system to the external HD. 

Incidently, you've quoted in the Ubuntu kernel version which makes it Ubuntu 6.10 Edgy Eft. And the percentage install completed and disk space used have no relationship.

---

### Post by Mars8082686 on 2007-02-18
Here is what the scsi file looked like 
```

Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02

```

---

### Post by didg on 2007-02-18
Ok, not too bad.
from a terminal output of:
mount
and
sudo mac-fdisk -l /dev/sda

---

### Post by Mars8082686 on 2007-02-18
All of these partitions were set up by the installer before it crash; I wiped the disk before attempting the install
```

/dev/sda
        #                    type name                length   base    ( size )  system
/dev/sda1     Apple_partition_map Apple                   63 @ 1       ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap untitled              1954 @ 64      (977.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 untitled           7591797 @ 2018    (  3.6G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                405672 @ 7593815 (198.1M)  Linux swap

Block size=512, Number of Blocks=7999487
DeviceType=0x0, DeviceId=0x0



```

---

### Post by didg on 2007-02-18
And the mount output?

---

### Post by Mars8082686 on 2007-02-18
heres what I get when I type mount
```

unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-powerpc/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda3 on /media/ipod type ext3 (rw,nosuid,nodev)


```

---

### Post by grazie on 2007-02-18
Looks like your problem is a known bug ([#64219]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/64219"), [#67669]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/67669") & [#76614]("https://launchpad.net/ubuntu/+source/ubiquity/+bug/76614")) and has been outstanding for quite a while. I don't hold much hope of it being fixed any time soon. Rather than raise a new bug as instructed I would confirm bug #76614.

I'm quite confident you could complete the installation quite easily by chrooting and installing yaboot yourself manually. However as I don't have an external HD to try it myself, I can't give a full set of instructions that are known to work. Maybe someone else in the community has done this already and can post the details.

---

### Post by didg on 2007-02-19
Ok, I don't know why it failed (/dev/sda2 is not mounted) but if you want to install it manually you can from a terminal:

sudo /bin/bash

umount /dev/sda3
mount /dev/sda3 /mnt
mount -o bind /proc/ /mnt/proc
mount -o bind /sys  /mnt/sys
mount -o bind /dev /mnt/dev
cd /mnt
chroot . bin/bash

cat /etc/yaboot.conf (double check that root=/dev/sda3 and partition=3) 

ofpath /dev/sda2 (only for double checking there's no error)

mkofboot -v -b /dev/sda2 (use --nonvram if you don't want to boot by default on the iPod)

exit
reboot

Note: my main Ubuntu disk is a firewire drive but it's a long time I installed it and I'm not 100% sure of the above :)

---

### Post by grazie on 2007-02-19
I think you'll need

```
$ ybin -v
```

affer the mkofboot command. Mabe didg can confirm this?

---

### Post by Mars8082686 on 2007-02-19
when I type "ofpath /dev/sda2" it says "ofpath: Driver: usb-storage is not supported" should I go ahead and mkofboot? or not? and will mkofboot mess with my internal hard drive at all? cause I don't want to mess up my OS X.

---

### Post by grazie on 2007-02-19
What machine are you trying to do this on? 

ofpath should just return the Open Firmware path of the linux device specified. Try doing the same ofpath command before chroot.

Also if you've got an internal HD, you maybe better off creating the bootstrap partition on that.

---

### Post by Mars8082686 on 2007-02-19
I am on a 2004 12 inch 1.33ghz PowerBook.

And about making a boot strap on the internal drive. What would the drawbacks to that be? I was trying to avoid tampering with my internal drive (I don't want to mess anything up) but if it would be better to do that than I might. Also I just got my 250gb USB hard drive in the mail. So I might instead try to install ubuntu on that. Any suggestions?

Edit: I decided to see if the install would work on my new USB HD. Anyways I started the install, and when I got to step 5 "Prepare Disk Space" I clicked on "Resized SCSI1 (0,0,0), partition @1 (sda) and use freed space" for "New partiton size" I used 35%(81.0GB). When I clicked next it started loading and I got the little ubuntu spiny thing. It's been loading for about 30 minutes now... is that normal? or did another error occur? it only took my 4gig drive a matter of seconds, now obviously this drive is quite larger, but I'm still a little concerned. But hopefully for now reason.

---

### Post by Mars8082686 on 2007-02-19
I've been doing some reading and multiple sources are saying that booting from USB in edgy is not supported. Is this right? if so are any previous versions of ubuntu USB supported?

---

### Post by grazie on 2007-02-19
I'm sure that machine supports booting from an external disk. I believe the standard Edgy kernel supports booting from Firewire and USB, but it's not something I've tried myself. Looking closely at the kernel config file confirms this. Earlier Ubuntu releases do not support it without a kernel rebuild.

30 minutes to format 81G seems a bit long, but does your machine support USB2 (mine doesn't)? If not it's going to be very slow using USB1. You'd be much better off using Firewire if the disk enclosure supports both.

I'd be happy to set up the bootstrap partition on the internel drive, but it doesn't sound like you're too confident. Did you try the ofpath command before the chroot command?

Incidently, your almost certainly going to get the same ubiquity bug when installing on the big USB drive.

---

### Post by Mars8082686 on 2007-02-19
> **grazie said:**
> 
Incidently, your almost certainly going to get the same ubiquity bug when installing on the big USB drive.
Yea.... I did get the same bug :-(. 


> **grazie said:**
> 
I'd be happy to set up the bootstrap partition on the internel drive, but it doesn't sound like you're too confident.
I'm willing to set the bootstrap up on the internel drive. I only have 150mb's of none partitioned space on that drive, and I just didn't want to have to reformat my HFS+ partiton. If all I have to do is make a small bootstrap on my internal and be able to use my external usb hard drive, then thats prob what I want to do. the installer got 95% done before it crashed, would I still have to re-install it on my external, or would I just have to create the bootstrap then be able to boot from my usb HD?

---

### Post by didg on 2007-02-19
> **Mars8082686 said:**
> when I type "ofpath /dev/sda2" it says "ofpath: Driver: usb-storage is not supported" should I go ahead and mkofboot? or not? and will mkofboot mess with my internal hard drive at all? cause I don't want to mess up my OS X.

No you shouldn't it will fail.


after the whole mount chroot, can you run:
 sh -x /usr/sbin/ofpath /dev/sda2 2>output
and post output?

Note: 
1) ybin and mkofboot are the same program (mkofboot is a symlink), the diff is that mkofboot format the partition first.

2) edgy can run from an external partition, I do, but it can be a little hard to setup. 

3) an other option is to find the openfirwmare name from /proc/device-tree (it's what ofpath should do).
cf [https://help.ubuntu.com/community/BootFromFirewireHardDisk](https://help.ubuntu.com/community/BootFromFirewireHardDisk)

find /proc/device-tree/ -name disk@\* | grep -i firewire

but openfirmware is rather buggy and if you don't get it right you get really weird output when booting . 

What's work for me:
output of:
find /proc/device-tree/ -name disk@\* | grep -i firewire 
/proc/device-tree/*pci@f2000000/pci-bridge@d/firewire@a/node@00d04b340508b41d/sbp-2@c000/disk@0*

you will get something else, it's ok. 
my root is 9 (you 3) and boot 12 you (2)

my yaboot.conf
boot=/dev/sda**12**
ofboot=*/pci@f2000000/@d/firewire@a/node@00d04b340508b41d/sbp-2@c000/disk@0*:**12**
device=*/pci@f2000000/@d/firewire@a/node@00d04b340508b41d/sbp-2@c000/disk@0*:
partition=**9**
root=/dev/sda**9**

Note the ':' after the device name.
follow by standart yaboot stuff.

yes I know there's no pci-bridge in yaboot but I don't remember if it works with it. Maybe some variables are not needed but once I got this stuff working, after many trials, I didn't change anything.

then mkofboot -v
without -b because ofboot is defined in yaboot.conf, it works, at least for me :)

---

### Post by Mars8082686 on 2007-02-21
Here was the output I recieved
```

+ PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin
+ PRG=ofpath
+ VERSION=1.0.7
+ DEBUG=0
+ export LC_COLLATE=C
+ command -v readlink
+ true
+ [ 1 != 0 ]
+ true
+ device=/dev/sda2
+ break
+ [ ! -e /dev/sda2 ]
+ [ ! -b /dev/sda2 ]
+ uname -s
+ [ Linux != Linux ]
+ uname -m
+ uname -m
+ [ ppc != ppc -a ppc != ppc64 ]
+ [ ! -f /proc/uptime ]
+ ckdevfs /dev/sda2
+ return 1
+ cat /proc/cpuinfo
+ grep pmac-generation
+ v=pmac-generation	: NewWorld
+ echo NewWorld
+ [ NewWorld = NewWorld ]
+ SUBARCH=NewWorld
+ [ ! -d /proc/device-tree ]
+ checkutils
+ command -v find
+ command -v find
+ [ -x /usr/bin/find ]
+ command -v head
+ command -v head
+ [ -x /usr/bin/head ]
+ command -v tail
+ command -v tail
+ [ -x /usr/bin/tail ]
+ [  = 1 ]
+ return 0
+ DEVICE=sda2
+ DEVNODE=sda
+ PARTITION=2
+ newworld
+ scsiinfo
+ [ ! -f /proc/scsi/scsi ]
+ SUBNODE=a
+ smalltr a
+ echo 1
+ return 0
+ SUBDEV=1
+ [ 0 = 1 ]
+ DEVCOUNT=0
+ linecount /proc/scsi/scsi
+ [ 1 = 0 ]
+ cat /proc/scsi/scsi
+ local file=Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02
+ local v=Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02
+ [ -z Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02 ]
+ command -v wc
+ command -v wc
+ [ -x /usr/bin/wc ]
+ echo Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02
+ wc -l
+ lines=4
+ [ 0 = 0 ]
+ echo 4
+ unset lines
+ return 0
+ SCSILINES=3
+ cat /proc/scsi/scsi
+ grep Direct-Access
+ linecount
+ [ 0 = 0 ]
+ cat
+ local file=  Type:   Direct-Access                    ANSI SCSI revision: 02
+ local v=  Type:   Direct-Access                    ANSI SCSI revision: 02
+ [ -z   Type:   Direct-Access                    ANSI SCSI revision: 02 ]
+ command -v wc
+ command -v wc
+ [ -x /usr/bin/wc ]
+ echo   Type:   Direct-Access                    ANSI SCSI revision: 02
+ wc -l
+ lines=1
+ [ 0 = 0 ]
+ echo 1
+ unset lines
+ return 0
+ [ 1 -gt 1 ]
+ cat /proc/scsi/scsi
+ tail -n 3
+ PROCSCSI=Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02
+ smallseq 1
+ local v=1
+ local n=1
+ echo 1
+ [ 1 -gt 1 ]
+ return 0
+ echo Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02
+ head -n 3
+ tail -n 3
+ DEVINFO=Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access                    ANSI SCSI revision: 02
+ [ 0 = 1 ]
+ echo Direct-Access ANSI SCSI revision: 02
+ v=Direct-Access ANSI SCSI revision: 02
+ echo Direct-Access
+ DEVTYPE=Direct-Access
+ [ 0 = 1 ]
+ echo 00 Lun: 00 Vendor: Apple Model: iPod Rev: 1.62 Type: Direct-Access ANSI SCSI revision: 02
+ v=00 Lun: 00 Vendor: Apple Model: iPod Rev: 1.62 Type: Direct-Access ANSI SCSI revision: 02
+ echo 00
+ n=00
+ echo 0
+ DEVID=0
+ [ 0 = 1 ]
+ echo 0 Channel: 00 Id: 00 Lun: 00 Vendor: Apple Model: iPod Rev: 1.62 Type: Direct-Access ANSI SCSI revision: 02
+ v=0 Channel: 00 Id: 00 Lun: 00 Vendor: Apple Model: iPod Rev: 1.62 Type: Direct-Access ANSI SCSI revision: 02
+ echo 0
+ DEVHOST=0
+ [ 0 = 1 ]
+ [ Direct-Access = Direct-Access ]
+ DEVCOUNT=1
+ [ 0 = 1 ]
+ [ 1 = 1 ]
+ DEVICE_HOST=0
+ DEVICE_ID=0
+ [ 0 = 1 ]
+ break
+ [ 0 = 1 ]
+ ls /proc/scsi/usb-storage/0
+ cat
+ x=/proc/scsi/usb-storage/0
+ echo usb-storage/0
+ y=usb-storage/0
+ echo usb-storage
+ SCSI_DRIVER=usb-storage
+ [ 0 = 1 ]
+ ls /proc/scsi/usb-storage/0
+ cat
+ grep -n 0\>
+ v=1:/proc/scsi/usb-storage/0
+ echo 1
+ SCSI_HOSTNUMBER=1
+ [ 0 = 1 ]
+ return 0
+ scsi_ofpath
+ echo ofpath: Driver: usb-storage is not supported
ofpath: Driver: usb-storage is not supported
+ return 1
+ return 1
+ exit 1


```

---

### Post by didg on 2007-02-21
Oh, It's really an USB Ipod, don't know why I thought it was a firewire one.

opath doesn't understand USB...

I believe that most newer Macs can't boot directly from USB either, you have to use of console. 

In my previous post you have to replace the line
find /proc/device-tree/ -name disk@\* | grep -i firewire 

by
 find /proc/device-tree -name "*disk*"  |grep usb

BTW you have to boot your Mac with the iPod connected and switch on.

---

