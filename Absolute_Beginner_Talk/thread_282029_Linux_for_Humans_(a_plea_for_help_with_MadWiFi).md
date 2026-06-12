---
title: "Linux for Humans? (a plea for help with MadWiFi)"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by nuclearj on 2006-10-22
I having some difficulty figuring out how to get my D-Link G510 Ver B1 wireless card to work.  I've been going in circles for 3 hours!

I just switched to Ubuntu two days ago, installation was fairly smooth, had some issues with installing automatix (i did it, but it was not pretty) and now I'm trying to install my wireless card.

If i understand this correctly MadWifi is what i need to get this thing going.  I went to dowlnload it and the **only** place to get it from is the Univeristy of Kent in England?  And the DL won't start!!!  What kind of BS is that?  I'll host the doggone file for cryin out loud.  I guess I just have to wait 'til i can access the file.

And in my travels I learned that Dapper came with MadWifi installed but that there are issues, and you need to type in all this gobbledygok to get it to work???  I think it has a little ways to go to be human friendly.  I contemplated going back to windows!  That is user friendly at leat.  Alas, i will keep pusing forward into this brick wall i see every where ](*,) until it breaks and then I'm a better person for it.

By the way, if anyone can send me that MadWifi file somehow I would greatly appreciate it.  Thanks for listening, I feel a little better now.:-|

---

### Post by jordanmthomas on 2006-10-22
does [this]("http://snapshots.madwifi.org/madwifi-ng-current.tar.gz") link not work for you?

If not, I can host it at my googlepages site for you.

---

### Post by nuclearj on 2006-10-22
Thank you so much it did work.  Now that i have the file i've put a crack in the wall.  Keep you fingers crossed.

---

### Post by nuclearj on 2006-10-22
Okay so i looked at the readme file and the install file...  It is all over my head... if some one could hold my hand and walk me through this.. I think i have to build a driver or some thing...  HELP!:confused:

---

### Post by taurus on 2006-10-22
What does the INSTALL say?

---

### Post by nuclearj on 2006-10-22
MADWIFI: Multimode Atheros Driver for WiFi on Linux (VAP branch)
================================================================

* Copyright (c) 2002-2005 Sam Leffler.  All rights reserved.

Read the file COPYRIGHT for the complete copyright.


Requirements
------------

- Kernel sources of the target kernel (some Linux distributions provide
  headers, makefiles and configuration data - it should suffice).
- Wireless Extensions support (14 or later, 17 preferred) - option
  CONFIG_NET_RADIO in kernel .config file.
- Sysctl support - option CONFIG_SYSCTL in kernel .config file.
- Crypto API support - option CONFIG_CRYPTO in kernel .config file (AES
  support is used if present, otherwise the AES-CCMP cipher module falls
  back to a private implementation).
- gcc of same version that was used to compile the kernel (ignoring this
  will cause "Invalid module format" errors during module load).

2.4.x kernels starting with 2.4.22 and 2.6 kernels should work without
problems.  Other kernel versions may require modifications, e.g. for
crypto support and/or updated wireless extensions.


Building the driver
-------------------

The driver is built using the Linux kernel build mechanism.  This means
you must have some part of the kernel source distribution installed on
the machine where you want to build the driver.  In particular, the
kernel include files, makefiles, build scripts and configuration must be
available.

This will be present if you built your kernel from source.  Otherwise
you may need to install an additional kernel development package from
your distribution that would match your kernel.  For example, the
development package for the default kernel is called linux-headers on
Debian and kernel-devel on Fedora Core.  Installing a package with full
kernel sources should not be generally necessary.

Note: in the following examples "trouble%" stands for your system
prompt; you're not expected to type that as part of the actual command.

Most people can just type:

  trouble% make

in the top-level MadWifi source directory to build all the modules for
the currently running system.

You MUST do a "make clean" before compiling for a different version of
Linux, e.g. building for 2.6 after building for 2.4.

If you want to compile MadWifi for a different kernel, you need to
specify the location of the kernel build tree, e.g.:

  trouble% make KERNELPATH=/usr/src/linux-2.6.3

Note that you can also specify this path by setting an environment
variable; e.g.

  trouble% export KERNELPATH=/usr/src/linux-2.6.3
  trouble% make

If the kernel was built outside the source directory, KERNELPATH should
point to the output directory where .config is located, not to the
sources.

MadWifi currently provides three different rate control algorithms,
ONOE, AMRR and SAMPLE.  SAMPLE is the most advanced one and is used by
default.  In order to make MadWifi use AMRR instead, you have to specify
that via the ATH_RATE environment variable; e.g.

  trouble% export ATH_RATE=ath_rate/amrr
  trouble% make

NOTE: Changing the rate control is only required (and recommended) for
      users who want to setup an access point using MadWifi in difficult
      (e.g. lossy) environments and who know what they are doing.

This distribution includes support for a variety of target platforms.
Because of the binary nature of the HAL not all platforms are supported
(the list grows as time permits).  The supported target platforms can be
found with:

  trouble% ls hal/pub/*.inc

A target specifies the CPU architecture, byte order, and the ABI/file
format.  For most popular platforms, the build system will find the
appropriate files.  When cross-compiling or compiling for less common
platforms, the target platform may need to be specified using the TARGET
variable, e.g:

  trouble% make TARGET=armv4-le-elf

Consult the contents of the .inc file to find out what the target
platform is and what toolchain was used to build the HAL object module. 
Beware of mixing toolchains; some target platforms require that the HAL
and driver be built with the same toolchain (i.e. compiler, assembler,
and linker) and the same compiler flags.  If you get warnings about
incompatible compiler flags, chances are that you are compiling for a
wrong target or using an incompatible compiler.

The build system is designed to support cross-building without any
modification to the distribution files.  If you cannot do what you need
by setting environment variables please send patches to show where
things failed to do the right thing.


Building the software will generate numerous loadable modules:

  ath_pci		Atheros driver for PCI/Cardbus devices
  ath_hal		Atheros HAL
  wlan			802.11 support layer
  wlan_wep		WEP cipher support
  wlan_tkip		TKIP cipher support
  wlan_ccmp		AES-CCMP cipher support
  wlan_xauth		external authenticator
  wlan_acl		MAC ACL support for AP operation
  wlan_scan_ap		AP scanning support
  wlan_scan_sta		station scanning support

and, depending on the rate control algorithm you choose (see above), one
of these:

  ath_rate_onoe		ONOE rate control
  ath_rate_amrr		AMRR rate control
  ath_rate_sample	SAMPLE rate control

The ath_pci module must be loaded either manually or by the system, e.g.
through the hotplug or card manager support.  The remaining modules are
loaded automatically as needed, so after doing a "make install" you only
need to run following:

  modprobe ath_pci

For automatic module loading you may need to modify your system's
configuration files so the necessary modules are loaded when an Atheros
device is recognized.  The exact procedure varies from system to system.

There are module parameters available to fit your needs, e.g. you can
set the countrycode manually if your card's EEPROM does not contain the
correct one for your location.  See
[http://www.unicode.org/onlinedat/countries.html](http://www.unicode.org/onlinedat/countries.html) to find your code.

To activate German frequencies you would specify:

  modprobe ath_pci countrycode=276

To see available parameters type:

  modinfo ath_pci

Further information on how to work with the driver can be found in the
file README.  In addition, the project's wiki has a lot of valuable
information:

[http://madwifi.org/](http://madwifi.org/)

---

### Post by aysiu on 2006-10-22
If you want a rant, post a rant, and I'll put it in the Cafe or the Backyard.

Since this seems to be more of a support request, I've retitled the thread appropriately.

---

### Post by orb9220 on 2006-10-22
> I having some difficulty figuring out how to get my D-Link G510 Ver B1 wireless card to work. I've been going in circles for 3 hours!

I have that exact card and wireless worked out of the box. I did not need to config Madwifi or anything else. Are you saying that it is not connecting?


> If i understand this correctly MadWifi is what i need to get this thing going. I went to dowlnload it and the only place to get it from is the Univeristy of Kent in England? And the DL won't start!!! What kind of BS is that? I'll host the doggone file for cryin out loud. I guess I just have to wait 'til i can access the file.


No not required

If you have the D-Link DWL g-510 b1 based on the atheros chip then it should work out of the box.

---

### Post by nuclearj on 2006-10-22
Yeah that makes sense, it is a plea for help...  Anyone?

---

### Post by diepruis on 2006-10-22
What have you tried doing so far? How did you try to connect?

---

### Post by nuclearj on 2006-10-22
> **diepruis said:**
> What have you tried doing so far? How did you try to connect?

Well I have my box connected via ethernet so I've tried disabling the ethernet connection and activate the wireless connection to connect.  (Sytem > Administration > Networking)  But when I open firefox it does not connect.  I'll switch the ethernet back on and open firefox and it works.  Thats about the scope of my "expertise" in Ubuntu.  I tried typing some thing in the terminal but didn't get very far.  I also tried cursing alot... that didn't help much.  And thank you to everyone who has helped me out, with support like this I'll make it over that learning curve.

PS: Orb9220, since it worked out of the box for you, should I reinstall Dapper?  I noticed you are using Edgy, you think that is the difference?

---

### Post by diepruis on 2006-10-22
Could you please go into the terminal and post the output of iwconfig and ifconfig?

---

### Post by nuclearj on 2006-10-22
nuclearj@Venice:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

nuclearj@Venice:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:04:0A:7D
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fe04:a7d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5875 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5357315 (5.1 MiB)  TX bytes:943107 (921.0 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:472 (472.0 b)  TX bytes:472 (472.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.70.1  Bcast:172.16.70.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.219.1  Bcast:172.16.219.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by diepruis on 2006-10-23
> **nuclearj said:**
> nuclearj@Venice:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


I don't know how to configure this card, but that output tells me that the driver (kernel module) isn't loaded. I'll hazard a guess that you might have misidentified your card. Please post the output of "lspci -n" so I can check your chipset [here](http://kmuto.jp/debian/hcl/index.cgi). Could you also post the output of "lsmod"?

If it's correctly identified, I'll try and help you with the installation.

---

### Post by nuclearj on 2006-10-23
> **diepruis said:**
> I don't know how to configure this card, but that output tells me that the driver (kernel module) isn't loaded. I'll hazard a guess that you might have misidentified your card. Please post the output of "lspci -n" so I can check your chipset [here](http://kmuto.jp/debian/hcl/index.cgi). Could you also post the output of "lsmod"?

If it's correctly identified, I'll try and help you with the installation.

Well I purchased a D-Link G510 / HW Ver B1 / FW Ver 2.11  I'm 100% sure of that.  It says so on the serial code

Here's the terminal stuff:

nuclearj@Venice:~$ lspci -n
0000:00:00.0 0600: 8086:2560 (rev 01)
0000:00:02.0 0300: 8086:2562 (rev 01)
0000:00:1d.0 0c03: 8086:24c2 (rev 01)
0000:00:1d.1 0c03: 8086:24c4 (rev 01)
0000:00:1d.2 0c03: 8086:24c7 (rev 01)
0000:00:1d.7 0c03: 8086:24cd (rev 01)
0000:00:1e.0 0604: 8086:244e (rev 81)
0000:00:1f.0 0601: 8086:24c0 (rev 01)
0000:00:1f.1 0101: 8086:24cb (rev 01)
0000:00:1f.3 0c05: 8086:24c3 (rev 01)
0000:00:1f.5 0401: 8086:24c5 (rev 01)
0000:01:08.0 0200: 8086:1039 (rev 81)
nuclearj@Venice:~$ lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
vmnet                  37284  13
vmmon                 111980  0
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ipv6                  265728  6
af_packet              22920  2
dm_mod                 58936  1
md_mod                 72532  0
lp                     11844  0
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
tsdev                   8000  0
e100                   40580  0
mii                     5888  1 e100
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
floppy                 62148  0
pcspkr                  2180  0
i2c_i810                5252  0
i2c_algo_bit            9608  1 i2c_i810
psmouse                36100  0
rtc                    13492  0
soundcore              10208  1 snd
serio_raw               7300  0
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
i2c_core               21904  2 i2c_acpi_ec,i2c_algo_bit
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  1
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  3 ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
nuclearj@Venice:~$

---

### Post by diepruis on 2006-10-24
That's weird, Linux doesn't seem to recognize that the device is in the PCI slot...

I might be missing something, or lspci might be broken, but could you check and see if the card is installed correctly?

Wait... I just though of something. Is this actually a PCI card or a USB stick?

---

### Post by nuclearj on 2006-10-24
I took out the wireless card and put it onto my other machine.  So that is why it does not recognize the card.  I'll install the card and type that stuff again.

---

### Post by dca on 2006-10-24
I don't know how much this will help but:  as many people have stated, the D-Link G510 Atheros and G520 (I believe) should work out of the box only requiring you to fill in the blanks as far as your security settings on the router go...  What happens when you put the LiveCD in and attempt to config (just to test) from there.  Make sure no ethernet cable connected to NIC.  Oddly, on my wife's PC (P4, 3GHz dealie) it let me config and use from LiveCD....????  If that works you may have to reinstall the OS...  I don't know, my two cents...

---

### Post by nuclearj on 2006-10-24
> **dca said:**
> I don't know how much this will help but:  as many people have stated, the D-Link G510 Atheros and G520 (I believe) should work out of the box only requiring you to fill in the blanks as far as your security settings on the router go...  What happens when you put the LiveCD in and attempt to config (just to test) from there.  Make sure no ethernet cable connected to NIC.  Oddly, on my wife's PC (P4, 3GHz dealie) it let me config and use from LiveCD....????  If that works you may have to reinstall the OS...  I don't know, my two cents...

Okay so I just booted from the liveCD to configure my card... I don't know how to configure it.  What I did was go the System > Administration > Networking.  I changed the default gateway device from eth0 to ath0.  Then I double clicked on wireless connection.  I selected my network (it knows its out there) and then put in the password under WEP Key.  It is set to hexadecimal.  The thing of it is though my network is set to the other "key type" WAP TKIP I think I hope that makes sense.  Well after i clicked okay it went to the activation screen and it took about 2 minutes before it went away.  I went to check the connection but there was nothing there.

So to sum it all up, i think i'm not configuring it correctly,  I'll try to remove the password from the network temporarlily to see if it will connect.

---

### Post by nuclearj on 2006-10-24
> **diepruis said:**
> That's weird, Linux doesn't seem to recognize that the device is in the PCI slot...

I might be missing something, or lspci might be broken, but could you check and see if the card is installed correctly?

Wait... I just though of something. Is this actually a PCI card or a USB stick?

Here is the new printout.

ubuntu@ubuntu:~$ lspci -n
0000:00:00.0 0600: 8086:2560 (rev 01)
0000:00:02.0 0300: 8086:2562 (rev 01)
0000:00:1d.0 0c03: 8086:24c2 (rev 01)
0000:00:1d.1 0c03: 8086:24c4 (rev 01)
0000:00:1d.2 0c03: 8086:24c7 (rev 01)
0000:00:1d.7 0c03: 8086:24cd (rev 01)
0000:00:1e.0 0604: 8086:244e (rev 81)
0000:00:1f.0 0601: 8086:24c0 (rev 01)
0000:00:1f.1 0101: 8086:24cb (rev 01)
0000:00:1f.3 0c05: 8086:24c3 (rev 01)
0000:00:1f.5 0401: 8086:24c5 (rev 01)
0000:01:02.0 0200: 168c:001a (rev 01)
0000:01:08.0 0200: 8086:1039 (rev 81)
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
wlan_wep                6912  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ipv6                  265728  6
ppdev                   9220  0
lp                     11844  0
i915                   20608  1
drm                    73236  2 i915
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ac                      5252  1 acpi_sbs
dm_mod                 58936  1
md_mod                 72532  0
tsdev                   8000  0
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  4 wlan_wep,ath_pci,ath_rate_sample
af_packet              22920  4
ath_hal               148816  3 ath_pci,ath_rate_sample
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
psmouse                36100  0
shpchp                 45632  0
pcspkr                  2180  0
floppy                 62148  0
snd_intel8x0           33692  3
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
serio_raw               7300  0
rtc                    13492  0
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
pci_hotplug            29236  1 shpchp
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
i2c_i810                5252  0
i2c_algo_bit            9608  1 i2c_i810
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
i2c_core               21904  2 i2c_acpi_ec,i2c_algo_bit
evdev                   9856  1
e100                   40580  0
mii                     5888  1 e100
squashfs               44980  1
unionfs                89884  1
loop                   17288  2
nls_cp437               5888  1
isofs                  37688  1
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  3 ehci_hcd,uhci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  2
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
ubuntu@ubuntu:~$

---

### Post by nuclearj on 2006-10-25
Okay so I finally figured out that I needed to configure my wireless router.  It was set to WPA-PSK (TKIP) for the security.  I guess this card only supports WEP.  So I switched the router to WEP and presto!  Thanks to everyone who donated their time.  :-D

---

### Post by diepruis on 2006-10-25
Great! Glad to have been of some help.

---

### Post by mr_forest on 2006-11-13
hi all, i'm having quite the same problem here, and just can't figure out what i'm missing.

first of all, some outputs:

 $ lspci -n
00:00.0 0600: 1106:0259
00:00.1 0600: 1106:1259
00:00.2 0600: 1106:2259
00:00.3 0600: 1106:3259
00:00.4 0600: 1106:4259
00:00.7 0600: 1106:7259
00:01.0 0604: 1106:b198
00:06.0 0200: 168c:0013 (rev 01)
00:10.0 0c03: 1106:3038 (rev 80)
00:10.1 0c03: 1106:3038 (rev 80)
00:10.2 0c03: 1106:3038 (rev 80)
00:10.3 0c03: 1106:3104 (rev 82)
00:11.0 0601: 1106:3177
00:11.1 0101: 1106:0571 (rev 06)
00:11.5 0401: 1106:3059 (rev 50)
00:11.6 0780: 1106:3068 (rev 80)
00:12.0 0200: 1106:3065 (rev 74)
01:00.0 0300: 1106:3118 (rev 02)

(already submitted in kmuto.jp/debian/hcl, seems ath_pci should fit)

$lsmod |grep ath
ath_pci                80540  0 
ath_rate_sample        17160  1 ath_pci
wlan                  144924  2 ath_pci,ath_rate_sample
ath_hal               148816  2 ath_pci,ath_rate_sample

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:D0:01:BE:06  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe81:be06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:36 txqueuelen:1000 
          RX bytes:1007828 (984.2 KiB)  TX bytes:205632 (200.8 KiB)
          Interrupt:11 Base address:0xe200 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

$ uname -r
2.6.15-26-386


if someone please could help me figure out.. i'd be really grateful..

thanks, francesco

---

### Post by diepruis on 2006-11-13
I don't have time to help more extensively now, but it sounds like you're missing firmware. Does anyone know if this card uses firmware and if so how do you install it. I'll help you later if I can find something on the net and when I have time.

---

### Post by diepruis on 2006-11-13
Did some more googling and it doesn't seem to be a firmware problem. Are you using madwifi? If not, try this link: [http://madwifi.org/wiki/Compatibility#DWLG650](http://madwifi.org/wiki/Compatibility#DWLG650). You probably are though, in which case I can't help you. Sorry.

---

