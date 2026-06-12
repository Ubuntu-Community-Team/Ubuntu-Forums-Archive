---
title: "Hello and what have I done"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-06-18
hi,
Just loaded Ubuntu on my computer - fiesty fawn.
A few quick questions to follow.
It was easier than I thought. really happy i got there.
I have two sata drives.
main drive 250 gig for windows xp pro ('h' drive  = sda)
second drive 160 gig for linux umbutu.("c" drive = sdb)
had no problems having intel core 2 duo and a gigabyte mother board.
was able to boot back into windows to join the forum.
1) xp can't see the 'c'rive now - is that a problem?
loaded off a full DVD so not sure if all the programmes were loaded - have they?

2)  - had to use the low graphics mode as i figure it didn't recognise my ati 9250 card, so how do i get it to recognise it and get the graphics running?

3) selected import account which was my windows xp pro - what have I done?

4) selected full partioning of my sata drive all 160 gig of it - what have I done?

5) eneterd a user name and password but with the live cd ingaged didn't recognise me, said something about wrong entry - not sure - can I change it latter? can I get back into it if I have the wrong user and password or wrong caps lock etc - dumb question.

6) can i boot into ubuntu then into xp for security and firewall?

7) how do i get the antivirus working in ubutu?

Thats all for now.
Working slowly, may try to get back into ubutu.

Cheers and best wishes
Bill

---

### Post by shearn89 on 2007-06-18
Hey, I'm not totally knowledgeable about Ubuntu, but i'll do my best to answer your questions:

> 1) xp can't see the 'c'rive now - is that a problem?
loaded off a full DVD so not sure if all the programmes were loaded - have they?

Probably not, as when Ubuntu partitioned the disk, it will have partitioned it as a Primary partition, which i imagine is not able to be seen by Windows. There's no real way to tell if you've loaded all the programs - if at some point you find you're missing something, you can always install it then.

> 2) - had to use the low graphics mode as i figure it didn't recognise my ati 9250 card, so how do i get it to recognise it and get the graphics running?
Check these forums - you may have to install "restricted" drivers that don't automatically install with ubuntu due to licensing issues (i think?)

> 
3) selected import account which was my windows xp pro - what have I done?

no idea here i'm afraid, as i installed ubuntu on an old laptop (check my sig.), so just wiped everything without worrying...

> 
4) selected full partioning of my sata drive all 160 gig of it - what have I done?

This will have taken the disc, allocated Xgb for the system files, Ygb for your /home (user) files, and Zgb for Swap space. No space will be left on the drive.

> 
5) eneterd a user name and password but with the live cd ingaged didn't recognise me, said something about wrong entry - not sure - can I change it latter? can I get back into it if I have the wrong user and password or wrong caps lock etc - dumb question.

I'm not certain here, but I know you can change usernames/passwords later - i think there's a user-manager app somewhere (try the System -> Administration menu). Have you tried loading without the live-cd if you've installed ubuntu to the hard drive?

> 
6) can i boot into ubuntu then into xp for security and firewall?
7) how do i get the antivirus working in ubutu?

Ubuntu basically doesn't need antivirus, as its not a fertile environment for them to grow in (i think), as there's no registry to change, and you're always logged on as a user, its very hard to get virus to work. Plus, the people that code them are more likely to target the [propaganda] Evil Microsoft Corporation [/propaganda]. I imagine the same goes for the security, and I'm not sure about the firewall. But i know you can't (easily) boot into XP from ubuntu.

---

### Post by wapfu on 2007-06-18
Hi,
Thanks for the quick reply.
so i've alloctaed the whole drive just for the operating system?
If so can I repartion it to add some more files? - if so how.

How do i get the internet to work - I have an adsl modem but firefox wouldn't connect - must be a driver missing somewhere.

point me in the right direction if possible.

Thanks
Best regards
bill

---

### Post by notbitmonk on 2007-06-18
Well, once you installed Ubuntu and used all the drive without partitioning it, you won't be able to repartition it without erasing it entirely (at least I have tried and have not been able).  If you just installed Ubuntu, you might as well reinstall it in the drive and do a manual partition when asked to.  About Ubuntu not seeing the Windows drive, I believe it has to do formatting of the drive.  Windows may have formatted the drive as NTFS which Ubuntu is not able to see (at least that is what happens to me).  I also found that things didn't work as expected on the first installation but it worked better the second time around.

---

### Post by LaRoza on 2007-06-18
> **wapfu said:**
> hi,
Just loaded Ubuntu on my computer - fiesty fawn.
A few quick questions to follow.
It was easier than I thought. really happy i got there.
I have two sata drives.
main drive 250 gig for windows xp pro ('h' drive  = sda)
second drive 160 gig for linux umbutu.("c" drive = sdb)
had no problems having intel core 2 duo and a gigabyte mother board.
was able to boot back into windows to join the forum.
1) xp can't see the 'c'rive now - is that a problem?
loaded off a full DVD so not sure if all the programmes were loaded - have they?

2)  - had to use the low graphics mode as i figure it didn't recognise my ati 9250 card, so how do i get it to recognise it and get the graphics running?

3) selected import account which was my windows xp pro - what have I done?

4) selected full partioning of my sata drive all 160 gig of it - what have I done?

5) eneterd a user name and password but with the live cd ingaged didn't recognise me, said something about wrong entry - not sure - can I change it latter? can I get back into it if I have the wrong user and password or wrong caps lock etc - dumb question.

6) can i boot into ubuntu then into xp for security and firewall?

7) how do i get the antivirus working in ubutu?

Thats all for now.
Working slowly, may try to get back into ubutu.

Cheers and best wishes
Bill
1. Windows cannot read ext3, but it will detect the drive in "Disk Management"
2. Not sure about the card, search or wait for an answer
3. Never imported, can't answer
4. You used the entire drive for Ubuntu, one partition is large and in ext3, the other is small and is swap
5. Your username is all lowercase usually, you can change accounts in System->Administration-> Users and Groups
6. Not sure what you are asking, but you can boot into either OS, if Grub doesn't come up, manually select the drive before Windows loads.
7. No antivirus needed, but you can get antivirus tools to make sure Ubuntu isn't holding anything, but Windows software will defend Windows, don't worry about it.

---

### Post by LaRoza on 2007-06-18
> **wapfu said:**
> Hi,
Thanks for the quick reply.
so i've alloctaed the whole drive just for the operating system?
If so can I repartion it to add some more files? - if so how.

How do i get the internet to work - I have an adsl modem but firefox wouldn't connect - must be a driver missing somewhere.

point me in the right direction if possible.

Thanks
Best regards
bill

Yes, you can alter partitions i.e. create new ones, shrink old ones, reformat, etc.

I recommend using GParted, check my sig.

---

### Post by bobpaul on 2007-06-18
First things first, you'll want to allow all software repositories. A repository is an online storage database filled with software Ubuntu can install automatically. From the applications menu, choose Add/Remove Applications, then click the Preferences button. On the first tab (Ubuntu Software) check all of the boxes under "Downloadable from the Internet".

> **wapfu said:**
> 
1) xp can't see the 'c'rive now - is that a problem?
loaded off a full DVD so not sure if all the programmes were loaded - have they?

WindowsXP uses the NTFS file system. This is a proprietary Microsoft filesystem, but has been reverse engineered so Linux can now support full access to your NTFS drive if you install the "NTFS Configuration Tool" (Applications: Add/Remove Applications, search for "NTFS")

Linux can use many different filesystems, but the default on Ubuntu is the 3rd Extended (ext3) filesystem. Windows has no built in support for this filesystem. If you would like to access your Linux partitions from within windows, such as to share documents, movies, etc that you created in Linux, you will have to install an ext3 filesystem driver for Windows. [Ext2 ifs]("http://www.fs-driver.org/") and [Ext2fsd]("http://ext2fsd.sourceforge.net/") are both good options.

Ubuntu is not like Fedora and other linux distributions that ship lots and lots of software on  the install disks. The Ubuntu install is just the basics, even if you use the DVD--the DVD just contains both the graphical and text based installer. To download and install applications all in one step, either use Add/REmove Programs from the Applications menu, or use Synaptic from System: Control Center. Synaptic is in the system group.

> **wapfu said:**
> 
2)  - had to use the low graphics mode as i figure it didn't recognise my ati 9250 card, so how do i get it to recognise it and get the graphics running?

Applications: Add/Remove Applications, search for "graphics." You will need to install the ATI binaray X.Org Driver.

You can also use the "Restricted Drivers" tool. This is in the Control center in the System Section. (System: Control Center: System: Restricted Drivers Manager)

> **wapfu said:**
> 
3) selected import account which was my windows xp pro - what have I done?
You've imported things like bookmarks and outlook mail messages. Try Firefox (web browser) or Evolution (mail client) from Ubuntu and you should be pleasantly surprised.

> **wapfu said:**
> 
4) selected full partioning of my sata drive all 160 gig of it - what have I done?
You've set up your 160GB drive entirely for linux. Any data that was previously on that drive is now lost. Ubuntu has taken it over.

The default partitioning scheme on Ubuntu is a single partition for all of your Linux files (OS and data files) and a single partition for your swap file. You can check or modify your partition scheme using the Gnome Partitioning tool, aka GParted. From System: Control Center find "GNOME Partition Editor (in the System section).

The way it is setup right now is just fine.

> **wapfu said:**
> 
5) eneterd a user name and password but with the live cd ingaged didn't recognise me, said something about wrong entry - not sure - can I change it latter? can I get back into it if I have the wrong user and password or wrong caps lock etc - dumb question.

You can either boot from the LiveCD or boot from Recovery Mode from the boot menu to fix a forgotten password. If that's the case, search the forums or [wiki]("http://wiki.ubuntu.com") for a fix or post a new topic for that question.

> **wapfu said:**
> 
6) can i boot into ubuntu then into xp for security and firewall?

Sort of. You can use a tool like VMWare or QEMU to run Windows from within Ubuntu. Your full windows desktop will show up inside its own window and can be minimized, dragged around, etc. Windows will not have the same performance it had as if it were running on it's own. Also, you can't "boot' the windows install you have on your other SATA drive. You will need to create a "Virtual" HD (a file that VMWare tells windows is a HD) and do a new install. This is useful for running windows only applications in Ubuntu without having to reboot to Windows, but generally does not have the performance to be a permanent fix. Eventually you'll want to find the Linux application that is similar to the tool you're using in Windows.

See the [Vmware/WinXP installation Guide]("https://help.ubuntu.com/community/VMware/Player?action=show&redirect=VMWarePlayerAndWindowsHOWTO") on the Ubuntu wiki.

Note that Windows installed in this way is not necessarily more secure than installed normally. It might, however, be easier to manage and backup, but that's a whole new can of worms and worth a discussion of its own.

> **wapfu said:**
> 
7) how do i get the antivirus working in ubutu?

You don't need antivirus in Ubuntu.There are only a few hundred viruses for the Linux platform, most of them proof of concepts exploiting bugs there were fixed before any major outbreaks occurred. You 



You might also consider installing [Automatix]("http://www.getautomatix.com"). This will help you install a number of things, some of which aren't in the official Ubuntu repositories.

---

### Post by wapfu on 2007-06-18
Hi,
Thanks to all replies.
It was a launch into the unknown and really appreciate the help and guidance and reassurance.

I've noticed that I can see and open folders etc on my windows drive - a plus.

tried to connect to the internet and set up using the administrator tab as the help section suggested, still cannot connect. The mother board has a gigabyte ethernet connection and I'm using a ADSL modem.
Tried the free raoming and the (from memeory) D???C settings , to no avail - internet is still dead in the water. The hardware seems to be recognise as I think its mentioned in the hardware tree thingy.
Any suggestions as to what to do next.

Bset Regards
Bill

---

### Post by bobpaul on 2007-06-18
I'm going to have you do a couple of text commands from the terminal because that's how I know how to do everything.

The commands you'll enter will collect some basic information about your system so that we can help you figure out what's up with your ethernet.

Applications: Accessories: Terminal

You should see something like "wapfu@wapfu $ _". Type in the following, pressing enter at the end of each line:
```
echo "ifconfig results" >>net.txt
ifconfig >> net.txt
echo " " >> net.txt
echo "lspci results" >> net.txt
lspci >> net.txt
```

This will create a "net.txt" in your home folder. Attach that to your reply.

What you did:
ifconfig and lspci display the status of your current network configuration and connected pci devices respectively. You can enter just each of those words to see the output on the screen, if you would like.

---

### Post by wapfu on 2007-06-18
Thanks BobPaul,
Will action tonight (NZ time)
Best Regards
Bill

---

### Post by wapfu on 2007-06-19
Hi BobPaul,
The txt is as follows

ifconfig results
eth0      Link encap:Ethernet  HWaddr 00:1A:4D:63:1D:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000 

eth0:avah Link encap:Ethernet  HWaddr 00:1A:4D:63:1D:54  
          inet addr:169.254.3.246  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:145044 (141.6 KiB)  TX bytes:145044 (141.6 KiB)

 
lspci results
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:01.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
03:01.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

I know that the DHCP setting doen't work,
I have an old D-Link DSL-302G as the adsl.

Other than that I can say
Partion #1  Ext3 153 gig using 11 on SCSI (0,1,0)
Partion #5 swap 6 gig

And thats the c drive for linux.

Best Regards
Bill

"fortune favours the brave" - and do I feel brave

---

### Post by bobpaul on 2007-06-19
When you say the DHCP doesn't work, do you mean it doesn't work with your ADSL (ie, it doesn't work in windows either) or what exactly? How do you have it configured in Windows?

I found some information on the [Gentoo Linux]("http://gentoo-wiki.com/HARDWARE_RTL8168") wiki that might help, as it doesn't sound like a Gentoo specific problem:
> Troubleshooting

As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey) 

If that's still no good, let's see the outputs of lsmod. Now that we know which adapter you have, we can check to make sure it's module (driver) is loaded. lshw looks to provide a lot of good info, and I just discovered it myself :D. Also let's look at your network config file. So do the following to create a net2.txt

```
echo "lsmod results" >>net2.txt
lsmod >> net2.txt
echo " " >> net2.txt
echo "lshw network section" >> net2.txt
sudo lshw -C network >> net2.txt
echo " " >> net2.txt
echo "network config" >> net2.txt
cat /etc/network/interfaces >> net2.txt
```

---

### Post by wapfu on 2007-06-20
Hi BobPaul,

Managed to get all except the  network config " cat /etc/network/interfaces >> net2.txt", tried all combinations, with or without gaps , kept getting no such file or directory "cat: /etc/network/interfaces >> net2.txt" as one result.

lsmod results
Module                  Size  Used by
ipv6                  268704  10 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
acpi_cpufreq           10056  1 
cpufreq_conservative     8200  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  2 
cpufreq_stats           7360  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
sony_acpi               6284  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
button                  8720  0 
ac                      6020  0 
container               5248  0 
video                  16388  0 
dock                   10268  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
xpad                    9988  0 
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
usbhid                 26592  0 
hid                    27392  1 usbhid
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
af_packet              23816  4 
parport_pc             36388  1 
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
pcspkr                  4224  0 
serio_raw               7940  0 
psmouse                38920  0 
parport                36936  3 ppdev,lp,parport_pc
iTCO_wdt               11812  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25116  1 
agpgart                35400  1 intel_agp
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
usb_storage            72256  0 
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sd_mod                 23428  3 
ata_generic             9092  0 
libusual               17936  1 usb_storage
ata_piix               15492  2 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
r8169                  32392  0 
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  7 xpad,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  2 acpi_cpufreq,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
 
lshw network section
 
network config

I have talked with the ISP so have the  IP of the modem, Subnet mask and fault gateway addresses, they have no experience with Linux.
The windows configuration from what I could record
Realtech RTL8i68/8111 PCI-E (which linux has picked up as well)
enable IEEE 802.1
TCP/IP settings are default
Obtain automatically IP
Obtain DNS Automatically
Default use netbios

Have tried unsuccessfully entering IP addresses etc still can't connect where I thought it would help.

Best regards
Bill

---

### Post by wapfu on 2007-06-20
Hi BoBPaul,

Your help with the quote,
"Troubleshooting

As of 27 May 2007, in kernel 2.6.21.3, you may experience the issues with the r8169 driver if you dual boot Windows on some systems. Windows by defaults disables the NIC at Windows shutdown time in order to disable Wake-On-Lan, and this NIC will remain disabled until the next time Windows turns it on. The r8169 driver in the kernel does not know how to turn the NIC on from this disabled state; therefore, the device will not respond, even if the driver loads and reports that the device is up. To work around this problem, simply enable the feature "Wake-on-lan after shutdown." You can set this options through Windows' device manager.

Edit: Problem with dual-booting with Windows exist also in 2.6.19.5 and 2.6.20.8 kernel, so it is safe to assume that it will concern all 2.6 kernels until the kernel developers update the drivers for RTL8168 to the version that will be able to turn on the NIC from disabled state. (Corey)"

Works.
Eureka!!!!!!!!!!!!!!

Should have done it before.

This should be posted as a must read first for core 2 duo and gigabyte motherboards.
Your bloods worth bottling.
Thanks so very much.
Cheers
Internet or bust - here I come.

Warm regards
Bill

---

