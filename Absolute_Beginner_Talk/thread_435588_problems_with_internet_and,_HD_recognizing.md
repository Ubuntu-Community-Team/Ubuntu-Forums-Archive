---
title: "problems with internet and, HD recognizing"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by tommasoviola on 2007-05-07
:)  could you help me?

my new kubuntu doesnt recognize my hd but the one in wich it is installed. I tried with a script like this that some help ful friend posted me:  sudo fdisk -l but still when I open the system manager window this doesn allow me (once linked as administrator) to enable othe HD that he does see. So kubuntu seems to see my HD but I can't enable them. I'm new as you know. What am I missing?


Another problem I have is with network management. I have a D-Link DSL 504-T router and in windows I set IP and Gateway and everything as it should and it is working as it should. I tryed to do the same in kubuntu but it doesn't work even if it says that he's seeing everything as working. I think I need some basic fact.
thanks 

tommi

---

### Post by steve.horsley on 2007-05-07
The command **sudo fdisk -l **does nothing except write a list of the disk drives and partitions that exist. Seeing this list - knowing exactly what is there -  is always the first step in solving problems with seeing disks. If you can post the output of this command here, it will help us. Second, please post the output of the command **df -h** which will tell us what disk partitions are currently mounted, and where. Third, please post the contents of the file /etc/fstab which tells the computer what partitions to mount and where to mount them.

Also, can you tell us exactly which disk partitions it is that you want to see that you don't at the moment. Then with the information above, we should be able to tell you how to fix your problem.


I looked at a description of the D-Link router, and it seems to have a built-in DHCP server, so I think your ethernet should be configured for DHCP, not for a fixed IP address. I don't know how to do this in Kubuntu.
It may be useful to see the output of these commands:
[B]ifconfig
sudo dhclient eth0
route -n
cat /etc/resolv.conf [/B]

---

### Post by tommasoviola on 2007-05-10
I tryed to do what you asked and that's what I've got:

tommi@tommikubu:~$sudo*fdisk**l
Disk*/dev/sda:*122.9*GB,*122941242880*bytes
255*heads,*63*sectors/track,*14946*cylinders
Units*=*cylinders*of*16065***512*=*8225280*bytes

*Device*Boot*Start*End*Blocks*Id*System
/dev/sda1*1*7426*59649313+*83*Linux
/dev/sda2*14276*14946*5389807+*5*Extended
/dev/sda3***7427*14275*55014592+*83*Linux
/dev/sda5*14570*14946*3028221*82*Linux*swap*/*Solaris
/dev/sda6*14276*14569*2361492*82*Linux*swap*/*Solaris

Partition*table*entries*are*not*in*disk*order

Disk*/dev/hda:*163.9*GB,*163928604672*bytes
255*heads,*63*sectors/track,*19929*cylinders
Units*=*cylinders*of*16065***512*=*8225280*bytes

*Device*Boot*Start*End*Blocks*Id*System
/dev/hda1***1*7649*61440561*7*HPFS/NTFS
/dev/hda2*7650*19928*98631067+*f*W95*Ext'd*(LBA)
/dev/hda5*7650*17848*81923436*7*HPFS/NTFS
/dev/hda6*17849*19928*16707568+*7*HPFS/NTFS

Disk*/dev/hdd:*81.9*GB,*81964302336*bytes
255*heads,*63*sectors/track,*9964*cylinders
Units*=*cylinders*of*16065***512*=*8225280*bytes

*Device*Boot*Start*End*Blocks*Id*System
/dev/hdd1*1*3322*26683933+*7*HPFS/NTFS
/dev/hdd2*3323*9964*53351865*f*W95*Ext'd*(LBA)
/dev/hdd5*3323*6642*26667868+*7*HPFS/NTFS
/dev/hdd6*6643*9964*26683933+*7*HPFS/NTFS
tommi@tommikubu:~$





tommi@tommikubu:~$*df**h
Filesystem*Size*Used*Avail*Use%*Mounted*on
/dev/sda3*52G*1,8G*48G*4%*/
varrun*506M*84K*506M*1%*/var/run
varlock*506M*4,0K*506M*1%*/var/lock
udev*506M*192K*506M*1%*/dev
devshm*506M*0*506M*0%*/dev/shm
lrm*506M*19M*488M*4%*/lib/modules/2.6.15*26*386/volatile
tommi@tommikubu:~$

tommi@tommikubu:~$*ifconfig
eth0*Link*encap:Ethernet*HWaddr*00:11:2F:D6:91:63
*UP*BROADCAST*RUNNING*MULTICAST*MTU:1500*Metric:1
*RX*packets:17*erors:0*dropped:0*overruns:0*frame:0
*TX*packets:13*erors:0*dropped:0*overuns:0*carrier:0
*colisions:0*txqueuelen:1000
*RX*bytes:2306*(2.2*KiB)*TX*bytes:4498*(4.3*KiB)
*Interupt:177

lo*Link*encap:Local*Loopback
*inet*addr:127.0.0.1*Mask:255.0.0.0
*UP*LOOPBACK*RUNNING*MTU:16436*Metric:1
*RX*packets:19*errors:0*dropped:0*overruns:0*frame:0
*TX*packets:19*erors:0*dropped:0*overuns:0*carier:0
*colisions:0*txqueuelen:0
*RX*bytes:1356*(1.3*KiB)*TX*bytes:1356*(1.3*KiB)

tommi@tommikubu:~$*



tommi@tommikubu:~$*sudo*dhclient*eth0
Internet*Systems*Consortium*DHCP*Client*V3.0.3
Copyright*2004*2005*Internet*Systems*Consortium.
Al*rights*reserved.
For*info,*please*visit*htp:/www.isc.org/products/DHCP

Listening*on*LPF/eth0/00:11:2f:d6:91:63
Sending*on*LPF/eth0/00:11:2f:d6:91:63
Sending*on*Socket/falback
DHCPDISCOVER*on*eth0*to*255.255.255.255*port*67*interval*8
DHCPDISCOVER*on*eth0*to*255.255.255.255*port*67*interval*11
DHCPDISCOVER*on*eth0*to*255.255.255.255*port*67*interval*14
DHCPDISCOVER*on*eth0*to*255.255.255.255*port*67*interval*11
DHCPDISCOVER*on*eth0*to*255.255.255.255*port*67*interval*17
No*DHCPOFFERS*received.
No*working*leases*in*persistent*database***sleeping.
tommi@tommikubu:~$*



tommi@tommikubu:~$*route**n
Kernel*IP*routing*table
Destination*Gateway*Genmask*Flags*Metric*Ref*Use*Iface

when*trying*to*reach*any*of*the*disk*I*see*(saving*documents*and*so*on.)*an*eror*windows*pops*up*
telling:
Could*not*mount*device
the*reported*error*was
mount:*can't*find*/dev/hda5*in*ets/fstab*or*/etc/mtab

#*/etc/fstab:*static*file*system*information.
#*<file*system>*<mount*point>*<type>*<options>*<dump>*<pass>
proc*/proc*proc*defaults*0*0
/dev/sda3*/*ext3*nouser,defaults,erors=remount*ro,atime,auto,rw,dev,exec,suid*0*1
/dev/sda6*none*swap*sw*0*0
/dev/hdc*/media/cdrom0*auto*user,atime,auto,rw,dev,exec,suid*0*0

this sounds a bit like arabic for me but what I understand is that kubuntu sees my hd but there is something that I must do to make them work properly.
Beside that I also see eth0 working in dhcp mode and it is flaged in green as working but still when I type some url in konqueror it says that the host is unknown..

sorry for teasing you and thanks again!!

---

### Post by drowner on 2007-05-10
My WORD you have a lot of partitions!

Your Linux *IS* seeing them, you just need to mount them, so you can read and write to them.

Where would you like to put them? All 9, or so, of them?

Then we can edit a file called fstab, which will tell ubuntu where to mount them.

---

### Post by tommasoviola on 2007-05-10
my aim is to eliminate microsoft from my pc in the future. so.. yes I'll probably want to mount them all except from the one (sistema) in wich XP is on. I don't know how to do it, I thought that going into system settings and telling to enable that hd that I see (icon) would be enough but it says that there is a problem in recognizing it. Still I'm missing something..
This may appear easy for you but not for me.
Once I login as administrator mode I made something to make a gray dot at the end of every partition he sees. Trying to click on enable once selected doesn't give any result..
What did I do wrong?
ciao
tommi

---

