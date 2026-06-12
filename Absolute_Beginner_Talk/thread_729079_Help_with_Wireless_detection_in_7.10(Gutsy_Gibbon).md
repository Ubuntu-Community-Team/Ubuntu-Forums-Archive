---
title: "Help with Wireless detection in 7.10(Gutsy Gibbon)!"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by VyperX on 2008-03-19
Hello, I am a noob at linux, and I just installed Ubuntu 7.10 (64-bit) on my Toshiba Satellite A215-S4767 but it doesnt detect my wireless crad but I actually have one.
When I got to Terminal and I type sudo iwlist scan it says this:

diego@Diego-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Any help will be appreciated! 

Right now I am using wired connection.

As you can see the image, it doesn't say anything about wireless. Any help please.

Link to image:
[http://img243.imageshack.us/img243/218/screenshotnetworksettinjn1.png](http://img243.imageshack.us/img243/218/screenshotnetworksettinjn1.png)

My laptop is a Toshiba Satellite A215-S4767,
AMD turion 64x2 Dual Core Mobile Technology,
250 gb HDD + 80 gb HDD (external),
ATI Radeon X1200,
**_54g Atherols Wi-Fi (802.11b/g)_**; 10/100 Ethernet; 4 USB, 1 FireWire, 1 VGA,
1 S-Video, 1 ExpressCard 34/54. 5-in-1 memory card reader,
Realtek High Definition Audio ALC268

Any help will be appreciated!

---

### Post by VyperX on 2008-03-19
Hello, I am a noob at linux, and I just installed Ubuntu 7.10 (64-bit) on my Toshiba Satellite A215-S4767 but it doesnt detect my wireless crad but I actually have one.
When I got to Terminal and I type sudo iwlist scan it says this:

diego@Diego-laptop:~$ sudo iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

Any help will be appreciated!

Right now I am using wired connection.

As you can see the image, it doesn't say anything about wireless. Any help please.

Link to image:
[http://img90.imageshack.us/img90/5549/screenshotnetworksettinhj6.png](http://img90.imageshack.us/img90/5549/screenshotnetworksettinhj6.png)

My laptop is a Toshiba Satellite A215-S4767,
AMD turion 64x2 Dual Core Mobile Technology,
250 gb HDD + 80 gb HDD (external),
ATI Radeon X1200,
54g Atherols Wi-Fi (802.11b/g); 10/100 Ethernet; 4 USB, 1 FireWire, 1 VGA,
1 S-Video, 1 ExpressCard 34/54. 5-in-1 memory card reader,
Realtek High Definition Audio ALC268

Any help will be appreciated!

---

### Post by dacorr on 2008-03-19
can you do a lspci in terminal and tell us if the wireless card is listed (expect big output so increase size of terminal window).

Could you also mention the model and manufacturer of the wireless card, it could just be a driver thing.

Dac

---

### Post by Hospadar on 2008-03-19
you may need to use the madwifi drivers for your atheros card:
Madwifi homepage

Also, go to the community docs in my sig and search for "madwifi"

Another option is ndiswrapper (also find info in the community docs)

Could you post the output of "lsmod" and "lspci"?

Furthermore, try googling stuff like "ubuntu atheros 54g" etc and see if you come up with any tutorials.

---

### Post by VyperX on 2008-03-19
Ok, my wireless card is an Atheros wireless

diego@Diego-laptop:~$ lsmod
Module                  Size  Used by
fglrx                 765588  34 
ipv6                  317192  10 
af_packet              28172  2 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_userspace       6048  0 
cpufreq_stats           8160  0 
cpufreq_powersave       3072  0 
cpufreq_conservative     9608  0 
cpufreq_ondemand       10896  1 
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
sbs                    21520  0 
ac                      7304  0 
battery                12424  0 
container               6400  0 
video                  21140  0 
button                 10400  0 
dock                   12264  0 
sbp2                   27144  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
joydev                 13440  0 
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 46232  0 
uvcvideo               52228  0 
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci                  21004  0 
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mmc_core               33416  1 sdhci
compat_ioctl32         11136  1 uvcvideo
tifm_7xx1               9856  0 
videodev               31360  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
pcspkr                  4608  0 
soundcore              10272  1 snd
tifm_core              13448  1 tifm_7xx1
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
psmouse                45596  0 
i2c_piix4              11020  0 
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
k8temp                  7680  0 
serio_raw               9092  0 
yenta_socket           30220  1 
rsrc_nonstatic         14208  1 yenta_socket
pcmcia_core            46628  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_core               30208  1 i2c_piix4
ath_pci               105392  0 
wlan                  225736  1 ath_pci
ath_hal               219888  1 ath_pci
shpchp                 38300  0 
pci_hotplug            36612  1 shpchp
evdev                  13056  5 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
ata_generic             9988  0 
sg                     41384  0 
usb_storage            81728  2 
libusual               22824  1 usb_storage
sd_mod                 32512  3 
usbhid                 32576  0 
hid                    33408  1 usbhid
ahci                   27012  0 
libata                138928  2 ata_generic,ahci
r8169                  36100  0 
scsi_mod              172856  5 sbp2,sg,usb_storage,sd_mod,libata
ohci1394               38984  0 
ieee1394              109528  2 sbp2,ohci1394
atiixp                  7824  0 [permanent]
ide_core              141200  3 ide_cd,usb_storage,atiixp
ehci_hcd               40076  0 
ohci_hcd               25092  0 
usbcore               161584  7 uvcvideo,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor




diego@Diego-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by bred on 2008-03-19
[COLOR="RoyalBlue"]try this thread dude- it works like a charm
[http://ubuntuforums.org/showthread.php?t=603154]("http://ubuntuforums.org/showthread.php?t=603154") [/COLOR]

---

### Post by handydan918 on 2008-03-19
> **bred said:**
> [COLOR="RoyalBlue"]try this thread dude- it works like a charm
[http://ubuntuforums.org/showthread.php?t=603154]("http://ubuntuforums.org/showthread.php?t=603154") [/COLOR]

Dude, did you like read the post? The link you posted has nothing to do with atheros cards. It's just a generic wireless tutorial. 
There are way too many wireless issues to come up with a single fix for all (or even most!) of them.

---

### Post by scottro on 2008-03-19
The 64 bit and that wireless are iffy.  

[http://ubuntuforums.org/showthread.php?p=4463071](http://ubuntuforums.org/showthread.php?p=4463071)

has worked for some people.  I am guessing that what you actually have is the AR5007EG.  Try doing lspci -nn and look for ID 168c:001c in the lines about that card.

---

### Post by VyperX on 2008-03-19
So what do I need to do, unninstall ubuntu & install it again or what? I have both versions 32 it and 64 bit, which one should I install? (If I need to install Ubuntu again)

---

### Post by handydan918 on 2008-03-19
> **VyperX said:**
> So what do I need to do, unninstall ubuntu & install it again or what? I have both versions 32 it and 64 bit, which one should I install? (If I need to install Ubuntu again)

You will probably have fewer issues with the 32 bit. The performance gains with 64 bit are marginal at best, anyway.

---

### Post by VyperX on 2008-03-19
Any help with my wireless issue?

---

### Post by VyperX on 2008-03-20
please I am getting desperate!

---

### Post by scottro on 2008-03-20
You've been given a few suggestions, and haven't responded with whether you've tried them or not. 

As I said, do lspci -nn.  If you get that ID I mentioned, you have an AR5007EG.  

If that's the case, then I gave a link to a thread where someone got it working in 64 bit. 

You asked if you should try 32 bit.  You were told yes, it's probably easier. 

So, I would take those steps in order.  Do lspci -nn.  If it turns out it's the 5007EG, then you can try the thread I mentioned, and if it doesn't work, then try reinstalling with 32 bit.  

The only other thing you can do is wait and see if someone else with more knowledge sees the thread and responds.  If it does turn out to be the 5006EG and you're sure of it, no doubt people with experience with those cards can help.

---

### Post by VyperX on 2008-03-20
Ok I just tried the lspci -nn and it says this:

diego@Diego-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon X1200 Series [1002:791f]
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
14:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
1a:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
1a:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
1a:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]


it says: AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)

I just installed the 32 bit ubuntu (7.10) what should I do now?

---

### Post by jan quark on 2008-03-20
can you please post the result of the terminal command

```
lspci -v | less
```

and check if the chipset of the wlan card is supported in the first place here:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by VyperX on 2008-03-20
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7128
        Flags: fast devsel, IRQ 22
        Memory at f8200000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>



In the link you gave me it doesnt say anything about atheros,

---

### Post by VyperX on 2008-03-20
Ok I just tried the lspci -nn and it says this:

diego@Diego-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc Unknown device [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon X1200 Series [1002:791f]
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
14:00.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)
1a:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
1a:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
1a:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
1a:04.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]


it says: AR5006EG 802.11 b/g Wireless PCI Express Adapter [168c:001c] (rev 01)

I just installed the 32 bit ubuntu (7.10) what should I do now?

---

### Post by scottro on 2008-03-20
Ok, the ID numbers indicate that it is almost certainly the AR5007EG, so reinstalling with the 32 bit would have been the next step that *I* would recommend.  (Merely because I was never able to get it working in 64 bit.)

So, now I'd follow the instructions at [http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007](http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007) and see how they work for you.  I've added in some Ubuntu specific stuff, so it should be alright. 

If any of it is difficult to understand, let me know, as I have done my best to provide newcomer friendly documentation.

---

### Post by VyperX on 2008-03-20
Ok I will try the guide, and if I have any issues I will let you know, thanks for the guide bud

Do you think I need a ''fresh'' install of ubuntu ( reinstall ubuntu) because I did some attempts to get my wireless working but thet didnt work, (I havent used your guide yet)

---

### Post by leroyc on 2008-03-20
The simple solution:

```
wicd
```

I swear this application is amazing. Totally beats the network manager of Gnome installed by default.

You can check the detailed description of how to easily install wicd and to configure your interface here:
[URL="http://top-web-solutions.com/ubuntu-wireless-application/"]
Ubuntu Wireless Solution[/URL]

---

### Post by VyperX on 2008-03-20
> **leroyc said:**
> The simple solution:

```
wicd
```

I swear this application is amazing. Totally beats the network manager of Gnome installed by default.

You can check the detailed description of how to easily install wicd and to configure your interface here:
[URL="http://top-web-solutions.com/ubuntu-wireless-application/"]
Ubuntu Wireless Solution[/URL]

Hello, I just tried your guide but it doesnt work at all, it doesnt detect any wireless connections.

[http://img172.imageshack.us/img172/1861/screenshotlm2.png](http://img172.imageshack.us/img172/1861/screenshotlm2.png)

In that link there is an image about wicd in my computer.

thanks.

---

### Post by scottro on 2008-03-20
Are you saying that wicd will add drivers for an unsupported network card or that it will simply be a better means of managing a detected card.  From the guide you linked to I got the impression that it's simply a better network manager.  

@Vyperx, I don't think you should have to reinstall Ubuntu yet another time.  Try the suggestions in my guide for removing previous attempts though--it is possible that one or another might conflict with what you'll try to do with my method.  

The first thing is to get the card recognized.  For that, you need drivers.  AFAICT (As far as I can tell) wicd doesn't do that unless the system already recognizes the card.  So, it's basically an improved NetworkManager--which, once again, won't help until the system sees the card.

---

### Post by VyperX on 2008-03-21
> **scottro said:**
> Are you saying that wicd will add drivers for an unsupported network card or that it will simply be a better means of managing a detected card.  From the guide you linked to I got the impression that it's simply a better network manager.  

@Vyperx, I don't think you should have to reinstall Ubuntu yet another time.  Try the suggestions in my guide for removing previous attempts though--it is possible that one or another might conflict with what you'll try to do with my method.  

The first thing is to get the card recognized.  For that, you need drivers.  AFAICT (As far as I can tell) wicd doesn't do that unless the system already recognizes the card.  So, it's basically an improved NetworkManager--which, once again, won't help until the system sees the card.

So your guide will make the system to see my card?

---

### Post by scottro on 2008-03-21
I'd give an 85 percent success rate.  (Judging from people who have tried it and responded--both to posts by others who have posted similar instructions and myself.  The AMD Turions don't always work.

As I've said somewhere along the line, including the guide itself, most of the information came from these forums.  

The trouble is that the card is not natively supported by the Linux kernel.  My way of doing it has you install the MadWiFi drivers.  It's similar to getting an installing a driver in Windows--your system won't see it, or will show it in WIndows Device Manager with a warning exclamation point until the proper driver is installed.  

So using WICD or NetworkManager won't work until the system actually recognizes the card in the same way that the Windows wireless thingie in their systray won't work (or might not even be there) until the system itself has the driver installed, and recognizes the card.  

The majority of people who do it my way (though saying "my way" is taking credit for work other people have done--I've just gathered up the steps and hopefully, put together a way to do it that's newcomer friendly, including mentioning possible problems) find that the system recognizes their card and they can then connect with the method of their choice.

---

### Post by VyperX on 2008-03-21
> **scottro said:**
> I'd give an 85 percent success rate.  (Judging from people who have tried it and responded--both to posts by others who have posted similar instructions and myself.  The AMD Turions don't always work.

As I've said somewhere along the line, including the guide itself, most of the information came from these forums.  

The trouble is that the card is not natively supported by the Linux kernel.  My way of doing it has you install the MadWiFi drivers.  It's similar to getting an installing a driver in Windows--your system won't see it, or will show it in WIndows Device Manager with a warning exclamation point until the proper driver is installed.  

So using WICD or NetworkManager won't work until the system actually recognizes the card in the same way that the Windows wireless thingie in their systray won't work (or might not even be there) until the system itself has the driver installed, and recognizes the card.  

The majority of people who do it my way (though saying "my way" is taking credit for work other people have done--I've just gathered up the steps and hopefully, put together a way to do it that's newcomer friendly, including mentioning possible problems) find that the system recognizes their card and they can then connect with the method of their choice.

Ok, I am going to try your guide and I am going to tell you my progress report ( if you want), I am going to try your guide right now, so hopefully I can tell you my progress report in about 1 hour.

Thnaks for your help bud:)

---

### Post by scottro on 2008-03-21
Yes, please let me (and others) know.  It gives us all a better idea of whether these instructions are good or not. 

While your thanks is appreciated, (of course):) wait till it works.  

Anyway, my trying to help you is paying back all the mentors who have helped me in the past.

---

### Post by VyperX on 2008-03-21
> **scottro said:**
> Yes, please let me (and others) know.  It gives us all a better idea of whether these instructions are good or not. 

While your thanks is appreciated, (of course):) wait till it works.  

Anyway, my trying to help you is paying back all the mentors who have helped me in the past.


Ok I am havind an issue,  I dont understand these parts of the guide ''Save it somewhere. If you're in Gnome, the default will be your Desktop''
 Untar the file, cd into the directory and run make; make install. If using a system based on RedHat, make sure you have root's path.

As some of the commands in make install, e.g., depmod need either /usr/sbin/ or /sbin it's necessary to be sure that those directories are in your path. In RedHat and its offshoots, only root's path has that. So, if you did an su, rather than an su -, you might wind up with some command not found errors. For a more in depth explanation, see my page about paths in RH based distros. For now, if using Fedora or another RH based distribution, make sure to do su - and not just su.

To untar, build and install the source file we just downloaded, do

Code:
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make
make install

---

### Post by scottro on 2008-03-21
Ok, that's fine.  That will help me make it better. 
You download the file.  I suggest that you save it somewhere.  I then say that if you're using Gnome, the default desktop in Fedora and Ubuntu, the default place to save it is on your desktop. 

The next paragraph is for Fedora and other RedHat based distributions.  For Ubuntu users, you go to the next paragraph.  

To untar, build and install the source file we do

Then I list the commands.  Earlier in the guide, I say that if you're using Ubuntu, most of these commands will require you to use sudo.  

So, what would make this clearer?  This guide is being written for newcomers like yourself, so your input is important here.   (I know that I HATE things that assume you know what they're talking about and you don't.) 

Thanks.

---

### Post by VyperX on 2008-03-21
> **scottro said:**
> Ok, that's fine.  That will help me make it better. 
You download the file.  I suggest that you save it somewhere.  I then say that if you're using Gnome, the default desktop in Fedora and Ubuntu, the default place to save it is on your desktop. 

The next paragraph is for Fedora and other RedHat based distributions.  For Ubuntu users, you go to the next paragraph.  

To untar, build and install the source file we do

Then I list the commands.  Earlier in the guide, I say that if you're using Ubuntu, most of these commands will require you to use sudo.  

So, what would make this clearer?  This guide is being written for newcomers like yourself, so your input is important here.   (I know that I HATE things that assume you know what they're talking about and you don't.) 

Thanks.

Make sure you have the necessary tools to compile source code.
sudo apt-get install build-essential linux-headers-`uname -r`

for this part I need to put the Ubuntu cd right?

Thanks

---

### Post by VyperX on 2008-03-21
Ok I just typed the sudo thing and it just doesnt work:

diego@Diego-laptop:~$ sudo tar zxvf madwifi-ng-r2756+ar5007.tar.gz
[sudo] password for diego:
tar: madwifi-ng-r2756+ar5007.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by scottro on 2008-03-21
Ok, to answer your first question, you shouldn't need the CD if you have some kind of Internet connection.  (Actually, you probably need the Internet connection, because the tools you're getting with apt-get install, the headers and so forth, have to match the kernel you are using.)

Now, when you downloaded it, it was probably saved on your Desktop.  When you open a terminal, you're actually in your $HOME directory.   If you type 
ls
you should see various things, including a directory marked Desktop.  
Try cd Desktop

Then do ls again. 
You want to make sure you're in the same directory as the tarball that you downloaded.

---

### Post by Papa-san on 2008-03-21
> **leroyc said:**
> The simple solution:

```
wicd
```

I swear this application is amazing. Totally beats the network manager of Gnome installed by default.

You can check the detailed description of how to easily install wicd and to configure your interface here:
[URL="http://top-web-solutions.com/ubuntu-wireless-application/"]
Ubuntu Wireless Solution[/URL]

I can let you know that WICD is only a network manager. It will not work unless you have the proper drivers installed already. Yet I do agree that once you get it working, WICD is an awesome one, and I would definitely recommend it!!!

---

### Post by VyperX on 2008-03-21
> **scottro said:**
> Ok, to answer your first question, you shouldn't need the CD if you have some kind of Internet connection.  (Actually, you probably need the Internet connection, because the tools you're getting with apt-get install, the headers and so forth, have to match the kernel you are using.)

Now, when you downloaded it, it was probably saved on your Desktop.  When you open a terminal, you're actually in your $HOME directory.   If you type 
ls
you should see various things, including a directory marked Desktop.  
Try cd Desktop

Then do ls again. 
You want to make sure you're in the same directory as the tarball that you downloaded.

Ok, so for this:
tar zxvf madwifi-ng-r2756+ar5007.tar.gz
cd madwifi-ng-r2756+ar5007
make
make install

I need to type sudo for each one? Example:
sudo tar zxvf madwifi-ng-r2756+ar5007.tar.gz
sudo cd madwifi-ng-r2756+ar5007
sudo make
sudo make install

---

### Post by scottro on 2008-03-21
No, but it won't hurt. 

I would use sudo for make (though that might not be necessary).

So 
tar zxvf madwifi-blahblah
cd madwifi-blahblah
sudo make
sudo make install 

Then, when done
sudo modprobe ath_pci

(but make sure to disable any atheros stuff already running.   (see step 7 of the guide.)

---

### Post by VyperX on 2008-03-21
> **scottro said:**
> No, but it won't hurt. 

I would use sudo for make (though that might not be necessary).

So 
tar zxvf madwifi-blahblah
cd madwifi-blahblah
sudo make
sudo make install 

Then, when done
sudo modprobe ath_pci

(but make sure to disable any atheros stuff already running.   (see step 7 of the guide.)

for step 6 I need to reboot my computer right? because when I got to restricted drivers, and I disable Atheros Hardware Access Layer (HAL) it says I need to restart the computer.

---

### Post by scottro on 2008-03-21
Probably.  You might be able to get away without it, but it can't hurt.  
I'm going to be out for awhile, so try following the instructions as best you can.  (You're doing fine so far.)

---

### Post by VyperX on 2008-03-21
> **scottro said:**
> Probably.  You might be able to get away without it, but it can't hurt.  
I'm going to be out for awhile, so try following the instructions as best you can.  (You're doing fine so far.)

So basically I just continue without restarting the computer at any time?

---

### Post by VyperX on 2008-03-21
Help, look whats going on:

diego@Diego-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ sudo modprobe ath_pci
[sudo] password for diego:
diego@Diego-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
diego@Diego-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: No such device
diego@Diego-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ iwlist ath0 scan
ath0      Interface doesn't support scanning.

diego@Diego-laptop:~/Desktop/madwifi-ng-r2756+ar5007$ dmesg |grep HAL
[   26.748000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

---

### Post by scottro on 2008-03-21
Ok, my last post on this before I go to sleep.

Have you rebooted? 

I would try this.  Reboot.  Make sure you disabled any Ubuntu restricted ath drivers (as mentioned in the guide, go to system and look for hardware or restricted drivers.)
At that point, once again do sudo modprobe ath_pci  
Then do lsmod |grep ath
Hopefully, you're going to see ath_pci.  :)  Then try the other stuff, the iwlist and all that. 

I do realize it's frustrating, but for a beginner you're doing quite well, and you have the right attitude, you keep on trying instead of saying, "Oh darn, this Linux stuff is no good."

As I said, it seems to have about an 85% success rate.  Turions seem to have the most problems.  

So do the restart and the modprobe again, and see where you're at.

---

### Post by VyperX on 2008-03-22
> **scottro said:**
> Ok, my last post on this before I go to sleep.

Have you rebooted? 

I would try this.  Reboot.  Make sure you disabled any Ubuntu restricted ath drivers (as mentioned in the guide, go to system and look for hardware or restricted drivers.)
At that point, once again do sudo modprobe ath_pci  
Then do lsmod |grep ath
Hopefully, you're going to see ath_pci.  :)  Then try the other stuff, the iwlist and all that. 

I do realize it's frustrating, but for a beginner you're doing quite well, and you have the right attitude, you keep on trying instead of saying, "Oh darn, this Linux stuff is no good."

As I said, it seems to have about an 85% success rate.  Turions seem to have the most problems.  

So do the restart and the modprobe again, and see where you're at.

Ok, I just got it, but, I can see wireless networks now, but do I need to enable the Atheros Hardware Access Layer (HAL) again?


THANKS VERY MUCH FOR YOUR SUPPORT!!

---

### Post by scottro on 2008-03-22
I've had mixed experience with this.  On the latest Hardy, I have to do it each time.  The thing is, I update it each time I boot into it, which isn't that often. 
So, since things have been updated, the module has to be reinstalled, so I don't leave it enabled.  

There's probably a modprobe.conf entry that should be made, but I'm not sure what it is.  (In the other distros I use, I don't have to modprobe each time--I think the only reason that I have to with Hardy is because of the frequent updates that happen during an Alpha release.)
If you're running Gutsy, I *think* you will be OK, but I'm not sure.  At any rate, if, when you reboot, if it doesn't see the card, run the modprobe ath_pci again. 

Hopefully, someone else will see this and be able to give you a better answer--that answer isn't a good one, but actually, I don't use Ubuntu that much.  <blush>.

---

### Post by dptxp on 2008-03-22
Wifi works with my Atheros card, Ubuntu 7.10 64bit.
I have my restricted driver enabled.
The only problem I have is that everytime I boot, I have to enter the WPA key.
It does not save.

---

### Post by Geos on 2008-03-22
> **VyperX said:**
> Ok, I just got it, but, I can see wireless networks now, but do I need to enable the Atheros Hardware Access Layer (HAL) again?


THANKS VERY MUCH FOR YOUR SUPPORT!!

Hi Vyper,

I have wireless working on 'Gutsy' with the same chipset and with the Atheros Hardware Access Layer enabled.
I used 'ndiswrapper' though, but the same drivers by the looks. Works great !!
I am a newbie in ubuntu though but will detail how I got it going if you require.

---

### Post by VyperX on 2008-03-22
> **Geos said:**
> Hi Vyper,

I have wireless working on 'Gutsy' with the same chipset and with the Atheros Hardware Access Layer enabled.
I used 'ndiswrapper' though, but the same drivers by the looks. Works great !!
I am a newbie in ubuntu though but will detail how I got it going if you require.

What happens if I dont enabke the Atheros Hardware Access Layer (HAL)?

---

### Post by VyperX on 2008-03-22
> **scottro said:**
> I've had mixed experience with this.  On the latest Hardy, I have to do it each time.  The thing is, I update it each time I boot into it, which isn't that often. 
So, since things have been updated, the module has to be reinstalled, so I don't leave it enabled.  

There's probably a modprobe.conf entry that should be made, but I'm not sure what it is.  (In the other distros I use, I don't have to modprobe each time--I think the only reason that I have to with Hardy is because of the frequent updates that happen during an Alpha release.)
If you're running Gutsy, I *think* you will be OK, but I'm not sure.  At any rate, if, when you reboot, if it doesn't see the card, run the modprobe ath_pci again. 

Hopefully, someone else will see this and be able to give you a better answer--that answer isn't a good one, but actually, I don't use Ubuntu that much.  <blush>.

Ok, as Ubuntu 8.04, is going to be available in April (the ''official'' one) do you thing it will be like a problem if I update from 7.10 to 8.04 from ubuntu updates? (problems with my wireless card?)

Thanks.

P.S= what do you us instead of Ubuntu? and why?

---

### Post by Geos on 2008-03-22
> **VyperX said:**
> What happens if I dont enabke the Atheros Hardware Access Layer (HAL)?

Well I just disabled the HAL and rebooted and it is still working okay. Must not be needed when using the seperate drivers via 'ndiswrapper' or 'madwifi' . I am not sure...

---

### Post by VyperX on 2008-03-22
> **Geos said:**
> Well I just disabled the HAL and rebooted and it is still working okay. Must not be needed when using the seperate drivers via 'ndiswrapper' or 'madwifi' . I am not sure...

So there's no need to enable it again?

---

### Post by psp219 on 2008-03-22
well i cant see the picture for some reason id ont know why

---

### Post by Geos on 2008-03-22
> **VyperX said:**
> So there's no need to enable it again?

I don't have it enabled on mine and wireless is working great, but again, being a newbie I am unsure as to what this HAL actually does.

Do you have your wireless connection working now and are you using madwifi? or ndiswrapper?

---

### Post by VyperX on 2008-03-22
> **Geos said:**
> I don't have it enabled on mine and wireless is working great, but again, being a newbie I am unsure as to what this HAL actually does.

Do you have your wireless connection working now and are you using madwifi? or ndiswrapper?

I am using madwifi

---

