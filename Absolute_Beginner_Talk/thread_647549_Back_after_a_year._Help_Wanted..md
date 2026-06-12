---
title: "Back after a year. Help Wanted."
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2007-12-22
About one year ago , a little longer, my laptop stoped taking a charge (Dell Inspiron 6000) and so it sat.  Just the other week i rbought it to staples and they now service dell laptops.  My laptop doesnt seem to charge the batter still but when its plugged in it will run off of AC powwer,

 But i also found out that now i have absolutly NO SOUND on my laptop.  

also,  i should  update the computer but when i try to it says that the following updates will be skipped.  Compiz and Totem.  I cant figure out how to update laptop and get around those 2 items.

Its been a while so i am a little rusty but i could use alot of help.  

Also i am still using the ubuntu version from a year ago, i believe it is the drapper drake version but i  dont remember

thank you to anyone who can help with any of my problems.

---

### Post by shareMenaPeace on 2007-12-22
Hello,
i suggest to search the forum for you notebook model and than for the soundcard name and model.

---

### Post by tgalati4 on 2007-12-22
You need to provide us some information:

From a terminal, post the output of:

>lspci -vv

and

>lsmod

---

### Post by StGeorge on 2007-12-22
forget it.
laptops and ubuntu do not mix yet.
i have 2 ibms that do not work with alsa drivers. work ok with windows.
keep ubuntu 4 anything that works.
if u have driver problem, forget it.
dell have same probs.
install simple win os 1st. ie 98 on fat32.
then install ubuntu no later than 6.06.
then have a machine that does all in different os.

---

### Post by spydon on 2007-12-22
> **StGeorge said:**
> forget it.
laptops and ubuntu do not mix yet.
i have 2 ibms that do not work with alsa drivers. work ok with windows.
keep ubuntu 4 anything that works.
if u have driver problem, forget it.
dell have same probs.
install simple win os 1st. ie 98 on fat32.
then install ubuntu no later than 6.06.
then have a machine that does all in different os.

My laptops work perfectly with Gutsy, I think most HP laptops do.

---

### Post by bigken on 2007-12-22
so do most dells

---

### Post by shareMenaPeace on 2007-12-22
so does asus :)

---

### Post by bigken on 2007-12-22
I would download the gusty live cd see if it fixes the problem

---

### Post by lgambett on 2007-12-22
Acer Aspire 3630 & HP Pavillon DV 6000 work out of the box with any Ubuntu > 6.10

---

### Post by LaRoza on 2007-12-22
My ThinkPad, and many others, work perfectly with Ubuntu.

@OP Try the most recent version of Ubuntu, or if your specs aren't high, try Xubuntu.

---

### Post by eternicode on 2007-12-22
> **StGeorge said:**
> forget it.
laptops and ubuntu do not mix yet.

Dell E1705.  Runs Kubuntu Feisty nigh-flawlessly.  Or does Kubuntu not count as Ubuntu? :-P

Not sure about your sound issues, but does the updater say "why" compiz and totem will be skipped?  If you're using a GUI updater, try aptitude from the command line, it gives more detail.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by adam.tropics on 2007-12-22
> **StGeorge said:**
> forget it.
laptops and ubuntu do not mix yet.
i have 2 ibms that do not work with alsa drivers. work ok with windows.
....

Wow, I think your the first person i have come across (without specifically looking) who has anything bad to say about ibm/lenovo and Linux. 

@OP....welcome back, long time no see! I'd download the current version and give it a fresh go. Backup anything important first, but I assume that if its been sat there a year, there's not much you need on it!

---

### Post by wormser on 2007-12-22
I have an Dell Inspiron 6000.  Everything worked fine under Feisty.  During the upgrade to Gusty I believe it blew my sound hardware.  Now I have not sound in Windows (I never boot into it any more)  or on a live Slax CD.

My 6000 sound [thread]("http://ubuntuforums.org/showthread.php?t=620618").  The [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176238").  Go through my thread to see if you can fix the sound.  Test a different Linux live CD to see if sound works or Windows.  If you think your hardware is blown then confirm my bug report.

---

### Post by louieb on 2007-12-22
> **StGeorge said:**
> ...i have 2 ibms that do not work with alsa drivers...
IBM T30 ThinkPad - sound  - wireless   worked out of the box 1st with Feisty and after the upgrade to Gutsy  still works.

---

### Post by jerrynewt on 2007-12-22
Toshiba Satellite Pro 6100 dual boot with Gutsy and XP. Everything worked out of the box after Gutsy install, so smooth it scared me !! Also Gutsy boots and runs twice as fast as XP.

---

### Post by bobpur on 2007-12-22
Acer Travelmate 4230-6179 and Toshiba Tecra S2 both work great dual booting Ubuntu and Windows XP.

---

### Post by IrishGangsta on 2007-12-23
mike@Finnegan:~$ lsmod
Module                  Size  Used by
rfcomm                 40216  0 
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0 
i915                   20608  1 
drm                    73236  2 i915
ipv6                  265728  8 
speedstep_centrino      8400  1 
cpufreq_userspace       4696  1 
cpufreq_stats           5636  0 
freq_table              4740  2 speedstep_centrino,cpufreq_stats
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
i2c_core               21904  1 i2c_acpi_ec
af_packet              22920  4 
dm_mod                 58936  1 
md_mod                 72532  0 
sbp2                   24196  0 
parport_pc             35780  0 
lp                     11844  0 
parport                36296  3 ppdev,parport_pc,lp
ipw2200               107308  0 
ieee80211              37064  1 ipw2200
ieee80211_crypt         6272  1 ieee80211
ieee80211_1_1_13       38216  0 
ieee80211_1_1_13_crypt     6784  1 ieee80211_1_1_13
pcmcia                 40508  0 
sdhci                  14848  0 
mmc_core               30104  1 sdhci
yenta_socket           28428  1 
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
joydev                 10048  0 
tsdev                   8000  0 
b44                    25740  0 
mii                     5888  1 b44
snd_intel8x0           33692  1 
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
psmouse                36100  0 
pcspkr                  2180  0 
serio_raw               7300  0 
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
rtc                    13492  0 
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
intel_agp              22940  1 
agpgart                34888  3 drm,intel_agp
sg                     37920  0 
sr_mod                 16932  0 
cdrom                  38560  1 sr_mod
evdev                   9856  2 
ext3                  135688  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ohci1394               35124  0 
ieee1394              299832  2 sbp2,ohci1394
ehci_hcd               34184  0 
uhci_hcd               33680  0 
usbcore               130692  3 ehci_hcd,uhci_hcd
sd_mod                 19984  3 
generic                 5124  0 
ata_piix               11012  4 
ahci                   17284  0 
libata                 78992  2 ata_piix,ahci
scsi_mod              139496  6 sbp2,sg,sr_mod,sd_mod,ahci,libata
thermal                13576  0 
processor              23360  2 speedstep_centrino,thermal
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
mike@Finnegan:~$ lspci -vv
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Dell: Unknown device 0188
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <available only to root>

0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 193
        Region 0: Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at ec38 [size=8]
        Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <available only to root>

0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 193
        Region 4: I/O ports at bf80 [size=32]

0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 177
        Region 4: I/O ports at bf60 [size=32]

0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 201
        Region 4: I/O ports at bf40 [size=32]

0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 169
        Region 4: I/O ports at bf20 [size=32]

0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 0188
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 193
        Region 0: Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=03, subordinate=07, sec-latency=32
        Memory behind bridge: dfd00000-dfdfffff
        Prefetchable memory behind bridge: 0000000030000000-0000000031f00000
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <available only to root>

0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Inspiron 6000 laptop
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 193
        Region 0: I/O ports at ed00 [size=256]
        Region 1: I/O ports at ec40 [size=64]
        Region 2: Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Conexant: Unknown device 5423
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 177
        Region 0: I/O ports at ee00 [size=256]
        Region 1: I/O ports at ec80 [size=128]
        Capabilities: <available only to root>

0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) (prog-if 80 [Master])
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 177
        Region 0: I/O ports at <ignored>
        Region 1: I/O ports at <ignored>
        Region 2: I/O ports at <ignored>
        Region 3: I/O ports at <ignored>
        Region 4: I/O ports at bfa0 [size=16]
        Capabilities: <available only to root>

0000:00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
        Subsystem: Dell: Unknown device 0188
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 4: I/O ports at 10c0 [size=32]

0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Inspiron 6000 laptop
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 201
        Region 0: Memory at dfdfe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
        Subsystem: Dell Inspiron 6000 laptop
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at dfd00000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=03, secondary=04, subordinate=07, sec-latency=176
        Memory window 0: 30000000-31fff000 (prefetchable)
        Memory window 1: 32000000-33fff000
        I/O window 0: 00001400-000014ff
        I/O window 1: 00001800-000018ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0000:03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08) (prog-if 10 [OHCI])
        Subsystem: Dell: Unknown device 0188
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 1000ns max)
        Interrupt: pin B routed to IRQ 201
        Region 0: Memory at dfdfc800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <available only to root>

0000:03:01.2 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17) (prog-if 01)
        Subsystem: Dell Inspiron 6000 laptop
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin C routed to IRQ 177
        Region 0: Memory at dfdfc700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
        Subsystem: Intel Corporation: Unknown device 2721
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (750ns min, 6000ns max), Cache Line Size: 0x10 (64 bytes)
        Interrupt: pin A routed to IRQ 177
        Region 0: Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

mike@Finnegan:~$

---

### Post by tgalati4 on 2007-12-23
Well, you have an ICH6 Intel embedded sound chip.  Ubuntu loads the correct drivers and sound does not work.  You may have to add some exception switches.  There are quite a few to go through.  Test them all to see if one will work for you.

Don't forget to activate all sound device channels (Volume Mixer-->Edit-->Preferences), then unmute all channels.

Do a search on ICH6 or ICH7 in the forums for examples of these switches.

Take the battery out of your laptop to reset the sound hardware then see if it works in Windows.

---

### Post by mmb1 on 2007-12-23
To get the neccesary info about your sound card, type "alsamixer" into the terminal and post the output.

---

### Post by IrishGangsta on 2007-12-24
what happens if i run the command sudo rm -rf   because i did

---

### Post by louieb on 2007-12-24
> **IrishGangsta said:**
> what happens if i run the command sudo rm -rf   because i did
:lolflag: You must have a 4 leaf clover in your pocket.  Done in just a sightly different way and its bye bye to everything on your  hard drive. 

Just like my kids:  tell them bad things are going to happen if you do this or that and .... oh well some people  are bull headed and just have to see for themselves.

:guitar:Did you know Thomas Edison tried 10,000 ways to make a light bulb before he found a way that worked.

---

### Post by Josh1 on 2007-12-24
> **StGeorge said:**
> forget it.
laptops and ubuntu do not mix yet.
i have 2 ibms that do not work with alsa drivers. work ok with windows.
keep ubuntu 4 anything that works.
if u have driver problem, forget it.
dell have same probs.
install simple win os 1st. ie 98 on fat32.
then install ubuntu no later than 6.06.
then have a machine that does all in different os.

Laptops and Ubuntu work fine together. :confused:

---

### Post by kpkeerthi on 2007-12-24
> 
forget it.
laptops and ubuntu do not mix yet.
i have 2 ibms that do not work with alsa drivers. work ok with windows.
keep ubuntu 4 anything that works.
if u have driver problem, forget it.
dell have same probs.
install simple win os 1st. ie 98 on fat32.
then install ubuntu no later than 6.06.
then have a machine that does all in different os.

That is not true. My dell laptop worked out-of-the box with edgy and feisty.

As for your question... type **alsamixer** in a termial and check if you have some channels muted and unmute them if required.

---

### Post by stalkingwolf on 2007-12-24
BS.  Ihave a Toshiba 8200 and a EVO that are both dual booting 7.04 with out a hitch.

---

### Post by IrishGangsta on 2007-12-24
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.10 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Intel ICH6                                                             &#9474;
&#9474; Chip: SigmaTel STAC9752,53                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master                                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     >
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;              &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;    pre 3D    &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;      &#9500;&#9472;&#9472;&#9508;              &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;MM&#9474;                        &#9474;MM&#9474;      &#9474;OO&#9474;              &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;    3<>3       0         0        0               94<>94             0<>0     &#9474;
&#9474; < Master >Master M  3D Contr 3D Contr 3D Contr    PCM    PCM Out    Line     &#9474;


how can I tell if anything is muted or not.  
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

