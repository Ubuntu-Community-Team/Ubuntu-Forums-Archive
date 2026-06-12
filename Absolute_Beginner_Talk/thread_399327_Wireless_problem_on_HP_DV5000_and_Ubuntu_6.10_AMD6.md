---
title: "Wireless problem on HP DV5000 and Ubuntu 6.10 AMD64"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by jahwire on 2007-04-02
I am using a HP DV5000 with Wifi and Ethernet built in...

I am totally new to Linux. I first installed Ubuntu 6.1 x386 on Windows XP system using Qemu and got everything to work just fine, including my wifi without doing anything special. 

Then after this test, I removed it all, partitioned my hard disk and installed Ubuntu 6.10 AMD64 on dual system with Windows XP using Wired Ethernet connection since it did not recognized my Wifi when starting from CD. I installed the 160 updates and restarted.
 
It all works great with Wired Ethernet connection to router, but refuses to connect with Wireless when I unplug wire. I went to System – Applications – Networking to enable the Wireless Card. I now have Wireless and Wired enabled. I use “Home” as the ESSIP. 

When I unplug the Ethernet connection, I loose connection. I restarted Ubuntu without the Ethernet cable connected and still don't get connection with wireless.

I got an error under Network Connection: SIOCGIFFLAGS error: No such device. I saw on the forum a link explaining the existence of a bug with Ubuntu AMD64 but don't understand how to fix it.

Any suggestions?

---

### Post by Skrynesaver on 2007-04-02
Could you open a terminal and type the command
```
lspci
```
and post a copy of the output,  This should tell us what Network Controller you are using.

---

### Post by jahwire on 2007-04-02
Here is it. I am currently connected with Wired Ethernet...

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 5a37
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation Dell Wireless 1470 DualBand WLAN (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by Skrynesaver on 2007-04-02
I was half way through a long post when I was looking something up and found this
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5)
looks very thorough, hope it helps

---

### Post by jahwire on 2007-04-02
I followed the instructions and at the end, as asked, if went to "activate the card in System/Administration/Networking. " before restarting.

The Wireless option under networking was GONE. I restarted and the wireless option is STILL GONE...

That was not the answer!! Any idea now?

---

### Post by Skrynesaver on 2007-04-02
what does lsmod say?

---

### Post by jahwire on 2007-04-02
Here it is:

Module                  Size  Used by
ipv6                  334432  8 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
powernow_k8            16576  0 
cpufreq_userspace       6560  0 
cpufreq_stats           9312  0 
freq_table              7104  2 powernow_k8,cpufreq_stats
cpufreq_powersave       3456  0 
cpufreq_ondemand       10928  1 
cpufreq_conservative    11272  0 
video                  22920  0 
tc1100_wmi             10632  0 
sbs                    20928  0 
sony_acpi               7704  0 
pcc_acpi               19968  0 
i2c_ec                  7808  1 sbs
i2c_core               29312  1 i2c_ec
hotkey                 14536  0 
dev_acpi               17540  0 
button                  9888  0 
battery                14088  0 
container               6656  0 
ac                      8328  0 
asus_acpi              21924  0 
nls_iso8859_1           6912  1 
nls_cp437               8704  1 
vfat                   17920  1 
fat                    65456  1 vfat
nls_utf8                3840  1 
ntfs                  109128  1 
af_packet              29452  2 
ndiswrapper           284824  0 
sbp2                   29448  0 
scsi_mod              181424  1 sbp2
parport_pc             43560  0 
lp                     16584  0 
parport                49932  2 parport_pc,lp
8139cp                 29696  0 
pcmcia                 49048  0 
joydev                 14208  0 
tsdev                  11136  0 
snd_atiixp             26644  1 
hci_usb                21268  2 
snd_atiixp_modem       21900  0 
snd_ac97_codec        127064  2 snd_atiixp,snd_atiixp_modem
snd_ac97_bus            4352  1 snd_ac97_codec
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
usbhid                 51360  0 
8139too                34816  0 
mii                     8192  2 8139cp,8139too
yenta_socket           33420  1 
rsrc_nonstatic         16896  1 yenta_socket
pcmcia_core            52772  3 pcmcia,yenta_socket,rsrc_nonstatic
bluetooth              64644  7 rfcomm,l2cap,hci_usb
tifm_7xx1              11264  0 
tifm_core              12928  1 tifm_7xx1
sdhci                  22796  0 
mmc_core               40456  1 sdhci
snd_pcm               108168  4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              31112  1 snd_pcm
evdev                  14592  2 
snd                    79016  9 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
snd_page_alloc         13200  3 snd_atiixp,snd_atiixp_modem,snd_pcm
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
pcspkr                  5248  0 
psmouse                51088  0 
serio_raw              10244  0 
ext3                  164880  1 
jbd                    74024  1 ext3
ehci_hcd               40456  0 
ohci1394               40776  0 
ieee1394              387704  2 sbp2,ohci1394
ohci_hcd               25988  0 
usbcore               167840  6 ndiswrapper,hci_usb,usbhid,ehci_hcd,ohci_hcd
ide_generic             2944  0 
ide_cd                 39584  0 
cdrom                  43816  1 ide_cd
ide_disk               21248  5 
generic                 7940  0 
atiixp                  9232  1 
thermal                19472  0 
processor              38280  2 powernow_k8,thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit


And I thought i knew computer... This is a real change!!

---

### Post by Skrynesaver on 2007-04-02
Drivers are still an issue for some hardware on linux so sometimes you do have to go visit the kernel, I assure you you won't be back here anytime soon.  The ndiswrapper module is loaded, so lets see what it has wrapped, 
```
ndiswrapper -l 
```

---

### Post by jahwire on 2007-04-02
Here it is:

Installed drivers:
bcmwl5          driver installed 

The driver seems to be installed properly. I had checked this earlier following instructions. 
I had the wifi working automatically when I first tested Ubuntu x386 with Qemu. Does this means that there is no driver for AMD64?

---

### Post by Kobalt on 2007-04-02
As far as I know the Dell 1470 card isn't working with the broadcom 4318 drivers... 
These instructions are working 100% with the Dell 1470 : [http://www.ubuntuforums.org/showthread.php?t=297092](http://www.ubuntuforums.org/showthread.php?t=297092), maybe you should this. 
And I recommend you to install Network-Manager (it's in the repos) in order to manage your wifi configuration/connection, that'll make it all easier.

---

### Post by jahwire on 2007-04-02
Here are a few thoughts:

I am realizing that, BESIDE THIS CURRENT ISSUE,  there are a lot of plugins for FireFox that are not 64 bits, but 32: Flash, Adobe Reader and many others... In fact, I am wondering if this is also the case with most apps out there right now. I need these plug ins. 
I saw on the forum that there are ways to get them up, but it seems like a headache. I am not sure I am willing to deal with this problem when I want to install new software! Will OpenOffice 2.2 run on AMD64?

Should I install the x386 version of Ubuntu instead? Will I see a serious difference on my Laptop? Will that make things easier at this point?

Sorry to change the issue at this point... Thanks!

---

### Post by Kobalt on 2007-04-02
You can have all those plugins working on Ubuntu 64bits pretty easily now, take a look at this for an example : [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Firefox32_in_AMD64](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Firefox32_in_AMD64)
And don't worry about OpenOffice 2.2, I think it will hit the AMD64 repos... You should have quite few problems with your 64bit system in my opinion (and your wifi doesn't seem to be related to 64bits to me).

---

### Post by jahwire on 2007-04-04
I worked on this Wireless problem for 3 days (many many hours). A real nightmare! The tutorial you mentioned is full of mistakes. I tried it a few times with AMD 64 and got my system to lock all the time at reboot. I did get it to see the wireless card at one time but it locked again and again. I feel that this tutorial should be replaced by a new one with all the corrections mentioned in the 10's of pages that follow it.

I also went to [http://www.linux-laptop.net/](http://www.linux-laptop.net/) and checked the info about my laptop. I tried the fw-cutter trick and it locked again at reboot. It even locked once when I run the command to install it.

I reformatted my hard disk partition and reinstalled Ubuntu 6.10 AMD64 so many times, I don't have enough fingers to tell you the exact number. I doubt my hard disk is "hard" now! I even tried the beta 7.04 AMD64 with same problems.

I was ready to give up and this morning I decided to repartition one last time and install Ubuntu 6.10 x386. I used the fw-cutter technique described at:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28cutter%29](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy?highlight=%28cutter%29).

I used the recommended wl_apsta.o as mentioned on the [http://www.linux-laptop.net/](http://www.linux-laptop.net/)  site under my portable. No problem.

Then I installed wifi-radar and after rebooting, it all worked great. I am now downloading the 160 updates via wireless with no problem.

Someone should tell the developers that there is something wrong with the AMD64 version...  I would rather use a 64 bits OS but right now, I want my wireless connection, and it only works on the 386 version (on my laptop).

That's all for now. Thanks for your help.

---

### Post by fulgencio on 2007-11-07
I have the same problem, can you please inform me about any solutions?
thanks.

---

