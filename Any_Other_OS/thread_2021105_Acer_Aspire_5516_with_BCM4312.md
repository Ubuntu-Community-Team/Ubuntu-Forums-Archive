---
title: "Acer Aspire 5516 with BCM4312"
date: 2012-07-08
forum: Any Other OS
---

### Post by FoAlBo on 2012-07-08
Having problems with 12.04.  10.04 worked great.  Have upgraded to 12.04 and am having problems as others with bcm.  Tried both the STA and b43 drivers.  Currently have b43 installed.  Still getting disconnected.  Tried different routers same issue.  Can someone assist.  Thanks for your help.

cat /etc/lsb-release;uname -a
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=13
DISTRIB_CODENAME=maya
DISTRIB_DESCRIPTION="Linux Mint 13 Maya"
Linux Acer5516 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 athlon i386 GNU/Linux

lspci -nnk  | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Foxconn International, Inc. T77H030.00 Wireless Mini PCIe Card [105b:e003]
	Kernel driver in use: b43-pci-bridge
--
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:0213]
	Kernel driver in use: atl1c
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
lsmod
Module                  Size  Used by
joydev                 17393  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
sparse_keymap          13658  0 
snd_seq_midi           13132  0 
binfmt_misc            17292  1 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
radeon                729591  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
psmouse                87140  0 
drm                   197692  4 radeon,ttm,drm_kms_helper
b43                   342643  0 
serio_raw              13027  0 
k8temp                 12905  0 
soundcore              14635  1 snd
sp5100_tco             13495  0 
mac80211              436455  1 b43
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
i2c_algo_bit           13199  1 radeon
cfg80211              178679  2 b43,mac80211
shpchp                 32325  0 
video                  19068  0 
wmi                    18744  0 
ati_agp                13242  0 
bcma                   25651  1 b43
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
pata_atiixp            12999  0 
atl1c                  36718  0 
ssb                    50691  1 b43

---

### Post by bkratz on 2012-07-08
Did you install the low power version of b43 installer?  See the first line under the box on this page.

[http://ubuntuforums.org/showpost.php?p=12009028&postcount=584](http://ubuntuforums.org/showpost.php?p=12009028&postcount=584)

---

### Post by FoAlBo on 2012-07-08
I installed firmware-b43-lpphy-installer

---

### Post by lilmalice on 2012-08-30
Have you figured out a fix for this issue yet?

I have installed 12.04 and 12.10... same thing. I seemed to have tried every possible scenario...

- Enabled LAN and setting it's boot priority first in the BIOS.
- Removed the STA driver and installing the b43-lpphy driver.
- Removing the default Network manager and installing Wicd.

No luck for me with the Acer Aspire 5516.

---

### Post by FoAlBo on 2012-08-30
No one able or willing to help.  Ended up re-installing 10.04.  It is supported until April 2013.  10.04 installed flawlessly found the wireless and worked immediately.  Pretty sad that 12.04 is broken and no will fix it.  Others have suggested purchasing a USB wireless device that is supported by 12.04.  Will probably do that next April.  I spent hours and hours reloading, modifying settings etc and finaly gave up.  Sorry I couldn't be of help.  If I remember next April I'll add to this thread what USB wireless device ended up working.

---

### Post by lilmalice on 2012-09-01
This really stinks. It's been driving me mad for over a week.

How is 10.04 compared to 12.04?

---

### Post by FoAlBo on 2012-09-01
10.04 is great.  Some software isn't as new, such as Open Office vs Libre Office, but it still does what I need it to do.  When the Aspire was originally purchased the first thing I did was replace Vista with Ubuntu.  Haven't regretted it one bit.

---

### Post by lilmalice on 2012-09-02
Maybe I'll give it a try, but before that, I am going to try installing the Windows driver with ndiswrapper.

Fyi, I posted a thread of my woes thus far.

[http://ubuntuforums.org/showthread.php?p=12206528#post12206528]("http://ubuntuforums.org/showthread.php?p=12206528#post12206528")

---

### Post by lilmalice on 2012-09-02
Is there another version newer than 10.04 that you know will work?

---

### Post by luisflores1961 on 2012-11-07
> **FoAlBo said:**
> No one able or willing to help.  Ended up re-installing 10.04.  It is supported until April 2013.  10.04 installed flawlessly found the wireless and worked immediately.  Pretty sad that 12.04 is broken and no will fix it.  Others have suggested purchasing a USB wireless device that is supported by 12.04.  Will probably do that next April.  I spent hours and hours reloading, modifying settings etc and finally gave up.  Sorry I couldn't be of help.  If I remember next April I'll add to this thread what USB wireless device ended up working.

I agree with the above statement, sadly looks like the "Precise pangolin" developers team has dropped the ball on their own end zone, I see it that bad. This is disappointing for all of us who have believed in the ubuntu project. There are a lot of request about this and none have given a real solution. Please get serious and make 12.04 the great operating system ubuntu deserves to be.

This is the output I get from the commands you request from us, I hope you can give 12.04 a reliable solution once for all. 

lflores@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

lflores@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
02:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)
03:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
lflores@ubuntu:~$ sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:02:00.2
       logical name: eth0
       version: 0a
       serial: 20:6a:8a:85:05:0d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
  *-network
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:ed:bd:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-32-generic firmware=N/A ip=192.168.1.67 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f0500000-f057ffff memory:dfa00000-dfa0ffff
lflores@ubuntu:~$ 
lflores@ubuntu:~$ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               320210  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     36475  1 
snd_hda_codec_realtek    73988  1 
joydev                 17693  0 
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          39352  0 
snd_hda_codec         139457  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
wmi                    19256  1 acer_wmi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                97443  0 
serio_raw              13211  0 
arc4                   12529  2 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
ath9k                 132390  0 
i915                  473298  4 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411151  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
mei                    41616  0 
drm_kms_helper         46978  1 i915
cfg80211              205544  3 ath9k,mac80211,ath
drm                   241921  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
r8169                  62099  0 
lflores@ubuntu:~$

---

### Post by luisflores1961 on 2012-11-10
I found a solution here: [https://bugs.launchpad.net/linuxmint/+bug/1040943](https://bugs.launchpad.net/linuxmint/+bug/1040943) 

It goes like this:

Open terminal and enter the following command:

sudo -s gksu gedit /etc/modprobe.d/ath9k.conf

at the end of the file add this:

options ath9k nohwcrypt=1

Save an restart your OS.

---

