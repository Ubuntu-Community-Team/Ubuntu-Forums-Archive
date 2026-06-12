---
title: "Shutdown due to overheating?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by mexicola on 2008-01-25
I'm running Gutsy 7.10 on a LG W1 laptop, Intel Core Duo T2350 @ 1.86GHz, 1GB RAM, Mobility Radeon X1600.

I'm trying to play WarCraft II through Wine, but my laptop shuts down every time after about 10-15 minutes due to overheating (At least I think, it shuts down fast, didn't get to read the entire error message). What the hell? I could play this game in Windows like 10 years ago, no problem, and now it shuts down because of overheating? What's going on?

I don't *have* to play this game, but, you know... I would like to solve this issue. Could it be some hardware malfunctioning? It's almost brand new.


Thanks!

---

### Post by xeth_delta on 2008-01-25
> **mexicola said:**
> I'm running Gutsy 7.10 on a LG W1 laptop, Intel Core Duo T2350 @ 1.86GHz, 1GB RAM, Mobility Radeon X1600.

I'm trying to play WarCraft II through Wine, but my laptop shuts down every time after about 10-15 minutes due to overheating (At least I think, it shuts down fast, didn't get to read the entire error message). What the hell? I could play this game in Windows like 10 years ago, no problem, and now it shuts down because of overheating? What's going on?

I don't *have* to play this game, but, you know... I would like to solve this issue. Could it be some hardware malfunctioning? It's almost brand new.


Thanks!

The first obvious question, and I apologize for asking, is: are the fans running properly?

You can have a look at the system messages in the file "/var/log/messages". It might not be over-heating after all.

---

### Post by mcduck on 2008-01-25
> **mexicola said:**
> I'm running Gutsy 7.10 on a LG W1 laptop, Intel Core Duo T2350 @ 1.86GHz, 1GB RAM, Mobility Radeon X1600.

I'm trying to play WarCraft II through Wine, but my laptop shuts down every time after about 10-15 minutes due to overheating (At least I think, it shuts down fast, didn't get to read the entire error message). What the hell? I could play this game in Windows like 10 years ago, no problem, and now it shuts down because of overheating? What's going on?

I don't *have* to play this game, but, you know... I would like to solve this issue. Could it be some hardware malfunctioning? It's almost brand new.


Thanks!
In my opinion any computer hardware that overheats without misuse or overclocking is malfunctioning.

Computers are meant to be able to run at 100% CPU use and heavy graphics card use for weeks, if not years, and this applies to laptops as well.

If the machine is really shutting down because of overheating I recommend contacting the manufacturer of the machine, or who ever is responsible for replacing faulty hardware in your country.

---

### Post by mexicola on 2008-01-25
Yes, fans are running. I don't know how well they get regulated (what's the word?) though, they are at a pretty constant level. When I unplug the AC, running on battery, it seems like the fans boost up to full power. I don't know if this is relevant to my issues...


I found the log, here's the last 5 minutes before shutdown:

Jan 26 09:50:50 HAL9000 kernel: [ 6124.148000] ACPI: Hot trip point
Jan 26 09:52:35 HAL9000 kernel: [ 6228.880000] ACPI: Critical trip point
Jan 26 09:52:35 HAL9000 kernel: [ 6228.912000] ACPI: Hot trip point
Jan 26 09:52:36 HAL9000 kernel: [ 6229.888000] ACPI: Hot trip point
Jan 26 09:52:38 HAL9000 exiting on signal 15

Looks like rap lyrics have polluted my laptop.

Are you getting anything? What's ACPI?

Thanks again.

---

### Post by BillDozer on 2008-01-25
[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface")

---

### Post by xeth_delta on 2008-01-25
> **mexicola said:**
> Yes, fans are running. I don't know how well they get regulated (what's the word?) though, they are at a pretty constant level. When I unplug the AC, running on battery, it seems like the fans boost up to full power. I don't know if this is relevant to my issues...


I found the log, here's the last 5 minutes before shutdown:

Jan 26 09:50:50 HAL9000 kernel: [ 6124.148000] ACPI: Hot trip point
Jan 26 09:52:35 HAL9000 kernel: [ 6228.880000] ACPI: Critical trip point
Jan 26 09:52:35 HAL9000 kernel: [ 6228.912000] ACPI: Hot trip point
Jan 26 09:52:36 HAL9000 kernel: [ 6229.888000] ACPI: Hot trip point
Jan 26 09:52:38 HAL9000 exiting on signal 15

Looks like rap lyrics have polluted my laptop.

Are you getting anything? What's ACPI?

Thanks again.

Quoting from the internet:
> The Advanced Configuration and Power Interface (ACPI) specification is an open industry standard first released in December 1996 developed by HP, Intel, Microsoft, Phoenix, and Toshiba that defines common interfaces for hardware recognition, motherboard and device configuration and power management. According to its specification, "ACPI is the key element in Operating System-directed configuration and Power Management (OSPM)".

> The Advanced Configuration and Power Interface Specification, Revision 3.0b describes the structures and mechanisms necessary to design operating system-directed power management and make advanced configuration architectures possible. ACPI applies to all classes of computers. If you want to design and build an ACPI-compatible system, you need the ACPI Specification.
[http://www.acpi.info/spec.htm]("http://www.acpi.info/spec.htm")

The messages you posted do seem to suggest some sort of over-heating, at least that is what the software is thinking. Does playing the same game in Windows have the same effect?

---

### Post by xeth_delta on 2008-01-25
If you want to check your CPU temperature you can do that by sending the output of a certain file to the terminal. To find out what it should be, please type:
```
find /proc/acpi/thermal_zone/* | grep -i temp
```

Alternatively you could install computertemp, it is in the repositories. It is a gnome applet that lets you see temperatures in your computer. I have not tried it myself, though.

---

### Post by mexicola on 2008-01-25
No, I haven't tested WarCraft II in Windows. Didn't think I would have to - I've played Garrys Mod (in Windows, maybe 3 or 4 months ago) and successfully fired that Nuke-thingy without facing overheating. I have just recently deleted my Windows install though, and reinstalling it would be some kind of a last resort...

Could Wine be the problem? I'm running Wine 0.9.53 and Ubuntu's running fairly smooth on other tasks, such as encoding video. My old install shut down now and then due to something about Network Manager/net bus/card bus error, perhaps they're related somehow. And I get a "PCI: BIOS BUG #81[...] found" on start-up.

Bah, guess I'm in denial about my hardware malfunction. Unfortunately, my laptop came pre-installed with Vista, and by removing Vista... I'm not sure, but I think my warranty's dead.


Anyway, thanks for your help! Any further help (if possible) would be much appreciated.

---

### Post by mexicola on 2008-01-25
> **xeth_delta said:**
> If you want to check your CPU temperature you can do that by sending the output of a certain file to the terminal. To find out what it should be, please type:
```
find /proc/acpi/thermal_zone/* | grep -i temp
```

Alternatively you could install computertemp, it is in the repositories. It is a gnome applet that lets you see temperatures in your computer. I have not tried it myself, though.


Output:

/proc/acpi/thermal_zone/TZ0/temperature
/proc/acpi/thermal_zone/TZ1/temperature
/proc/acpi/thermal_zone/TZ2/temperature

:confused:


Computertemp installed, I'll see what I can make out of it.


Thanks.

---

### Post by xeth_delta on 2008-01-25
> **mexicola said:**
> Output:

/proc/acpi/thermal_zone/TZ0/temperature
/proc/acpi/thermal_zone/TZ1/temperature
/proc/acpi/thermal_zone/TZ2/temperature

:confused:


Computertemp installed, I'll see what I can make out of it.


Thanks.

TZ0, TZ1, TZ2 represent, if I am not mistaken the temperatures of the core and the CPU per total. Which is which one, I can't tell for sure right now. To read the values, for example for TZ1:

```
cat /proc/acpi/thermal_zone/TZ1/temperature
```

---

### Post by mexicola on 2008-01-25
It's definitely hot, but I don't know if it's too hot: TZ0 is at about 70 C, TZ1+2 is at about 60 C. Currently idle. What do you think?

---

### Post by xeth_delta on 2008-01-25
> **mexicola said:**
> It's definitely hot, but I don't know if it's too hot: TZ0 is at about 70 C, TZ1+2 is at about 60 C. Currently idle. What do you think?

60C idle is not too much, actually my computer's CPU is at around 57-60 while idle.
What is the temperature under load?

---

### Post by mcduck on 2008-01-25
> **mexicola said:**
> It's definitely hot, but I don't know if it's too hot: TZ0 is at about 70 C, TZ1+2 is at about 60 C. Currently idle. What do you think?
Core 2 Cpu's have max temp of 100°C so that should be fine, as long as the cooling is able to keep it under that on full load.

I remember seeing somebody on the forums having troubles where the system shut the power down because it was for some reason using way too low temperature limit. Perhaps you have the same problem. Sadly, I can't remember anything more about that at the moment so I'm not able to provide any exact help, but you could try to see if you can find that thread from this forum..

---

### Post by mexicola on 2008-01-25
Under load the temperature is:

TZ0 - 80 C
TZ1 - 70 C
TZ2 - 60 C

The system works fine under these temps, but when I reached:

TZ0 - 80 C
TZ1 - 70 C
**TZ2 - 80 C**

it shuts down.

However, this time I got to read the error message more thoroughly. It said something about overheating and 80 C, so I guess that's the limit then. Is it possible to change it? Should I change it?


Thank you very much for your help.

---

### Post by mexicola on 2008-01-25
> **mcduck said:**
> Core 2 Cpu's have max temp of 100°C so that should be fine, as long as the cooling is able to keep it under that on full load.

I remember seeing somebody on the forums having troubles where the system shut the power down because it was for some reason using way too low temperature limit. Perhaps you have the same problem. Sadly, I can't remember anything more about that at the moment so I'm not able to provide any exact help, but you could try to see if you can find that thread from this forum..

I see. I'm going to do some searches.


Thank you.

---

### Post by mexicola on 2008-01-25
No luck on the searches. I found one poster who was trying to bring down the cpu temps, and I'm trying to adjust the cpu temp limit. But if I could somehow get the temps lower, that would be even greater, but it seemed very hard to do, and it could cause malfunction, so I'll avoid that one.

One thing, I just found out, if I unplug the AC power supply, TZ2 immediately drops to about 40 C. And if I plug it back in, it immediately goes back up to 60 C. Idle that is. Loaded it's 80 C. I have no idea why, I'm totally clueless. :confused:

---

### Post by xeth_delta on 2008-01-25
> **mexicola said:**
> Under load the temperature is:

TZ0 - 80 C
TZ1 - 70 C
TZ2 - 60 C

The system works fine under these temps, but when I reached:

TZ0 - 80 C
TZ1 - 70 C
**TZ2 - 80 C**

it shuts down.

However, this time I got to read the error message more thoroughly. It said something about overheating and 80 C, so I guess that's the limit then. Is it possible to change it? Should I change it?


Thank you very much for your help.

At least we know know what is happening. What I don't know is if there would be agood idea to do so. Maybe with 5 C at the most. I haven't noticed the CPU from my laptop reaching 80C, but I can put it under load and tell you a bit later. It is also a Core 2 Duo, but at 2GHz.
There should be some files under /proc/thermal that control the critical point. Inserting a new value in that file might do the trick to change it. What I think, nevertheless that would be an even better idea is to make the fan run at a higher speed at lower temperatures. That way temperatures should be lower, too. Again, there are some files in /proc/thermal controlling that. Unfortunately i can not tell you which those are, as for my Macbook they are placed in a different directory and have other names. I am able to control fan speed, though, and so should be once we figure out how.

Just one advice, be very careful when doing any changes in there, nobody wants a damaged laptop ;)

Xeth

---

### Post by mexicola on 2008-01-25
Thanks for the advice.

I'm currently following this guide: [http://ubuntuforums.org/showthread.php?t=42737&highlight=increase+fan+speed]("http://ubuntuforums.org/showthread.php?t=42737&highlight=increase+fan+speed")
Hopefully it will help me increase my CPU fan speed.


Any easier solution is much welcome though, that guide is some hard reading for å newbie.

---

### Post by BillDozer on 2008-01-28
> **mexicola said:**
> Yes, fans are running. I don't know how well they get regulated (what's the word?) though, they are at a pretty constant level. When I unplug the AC, running on battery, it seems like the fans boost up to full power. I don't know if this is relevant to my issues...

Somwhere there are Power Management options, I do not have access to my Ubuntu right now, but try and look in the System menus or on the screen saver dialog. Sounds like you maybe have set it to a too low setting which will not control your fans properly.

---

### Post by the_blur on 2008-01-30
I get the same thing, as son as my CPU hits 72C my computer hardcore just cuts out. Help!

HP ZD8000 Prescott lappy.

I'm sort of at a loss here. Everything else works perfectly, I am finally learning some linux, if I could just get rid of this bug, it would be great.

In winxp I can play games for hours without tripping the heat sensor into shutting down my compy...

lspci (fwiw):

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

More stuff:

default@L1:/proc/acpi/thermal_zone/THRM$ cat trip_points
critical (S5):           81 C
passive:                 81 C: tc1=4 tc2=3 tsp=40 devices=CPU0 
default@L1:/proc/acpi/thermal_zone/THRM$ 

(Is this why the fan is turning on so late? can I add/make the active trip point around 70C?)

default@L1:/proc/acpi/thermal_zone/THRM$ cat cooling_mode
0 - Active; 1 - Passive

default@L1:/proc/acpi/processor/CPU0$ cat throttling
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

default@L1:/proc/acpi/processor/CPU0$ cat limit
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0

default@L1:/proc/acpi/processor$ lsmod
Module                  Size  Used by
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
snd_rtctimer            4384  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
af_packet              24840  4 
nls_iso8859_1           5120  2 
nls_cp437               6784  2 
vfat                   14080  2 
fat                    54300  1 vfat
ipv6                  273892  12 
fglrx                 656352  51 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  5 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  1 
button                  8976  0 
container               5504  0 
ac                      6148  0 
battery                11012  0 
dock                   10656  0 
video                  18060  0 
sbs                    19592  0 
p4_clockmod             6436  1 
speedstep_lib           6404  1 p4_clockmod
freq_table              5792  3 cpufreq_stats,cpufreq_ondemand,p4_clockmod
cpufreq_userspace       5280  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
pata_pcmcia            14336  2 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
pcmcia                 41388  1 pata_pcmcia
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_rtctimer,snd_pcm,snd_seq
bcm43xx               127336  0 
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
joydev                 11328  0 
ieee80211softmac       31360  1 bcm43xx
sdhci                  18828  0 
yenta_socket           27532  3 
rsrc_nonstatic         14080  1 yenta_socket
mmc_core               28420  1 sdhci
ieee80211              35656  2 bcm43xx,ieee80211softmac
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
hci_usb                18332  2 
tifm_7xx1               8576  0 
snd                    54660  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              57060  7 rfcomm,l2cap,hci_usb
tifm_core              11268  1 tifm_7xx1
serio_raw               8068  0 
soundcore               8800  1 snd
pcmcia_core            40980  4 pata_pcmcia,pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  4224  0 
psmouse                39952  0 
snd_page_alloc         11400  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  0 
agpgart                35016  2 fglrx,intel_agp
evdev                  11136  5 
usbhid                 29536  0 
hid                    28928  1 usbhid
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  7 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
8139cp                 25088  0 
ata_piix               17540  2 
8139too                27776  0 
mii                     6528  2 8139cp,8139too
ata_generic             8452  0 
libata                125168  3 pata_pcmcia,ata_piix,ata_generic
scsi_mod              147084  6 usb_storage,sbp2,sg,sd_mod,sr_mod,libata
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  7 usb_storage,libusual,hci_usb,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by mexicola on 2008-01-31
> **BillDozer said:**
> Somwhere there are Power Management options, I do not have access to my Ubuntu right now, but try and look in the System menus or on the screen saver dialog. Sounds like you maybe have set it to a too low setting which will not control your fans properly.

I fixed the low fan-speed problem by doing some changes in BIOS. They are now set at "cool" (highest) permanently, and the fans seem to function independently from the OS, but it's still not sufficient:

TZ0 temp idle ~60 C, and load ~70 C, but I still reach 80 C + under heavy load, which causes system shutdown. Heavy load being Wine, Americas Army, and sometimes VirtualBox.

My conclusion is that Linux just isn't for gaming. :(

If there ever is a solution to this issue, I would very much like to hear it! Although I doubt it will be any time soon. I'm going to stick with Wintendo for games, Ubuntu for everything else, unless there's already a solution out there that I haven't found.

Thank you.

---

### Post by xeth_delta on 2008-01-31
> **mexicola said:**
> I fixed the low fan-speed problem by doing some changes in BIOS. They are now set at "cool" (highest) permanently, and the fans seem to function independently from the OS, but it's still not sufficient:

TZ0 temp idle ~60 C, and load ~70 C, but I still reach 80 C + under heavy load, which causes system shutdown. Heavy load being Wine, Americas Army, and sometimes VirtualBox.

My conclusion is that Linux just isn't for gaming. :(

If there ever is a solution to this issue, I would very much like to hear it! Although I doubt it will be any time soon. I'm going to stick with Wintendo for games, Ubuntu for everything else, unless there's already a solution out there that I haven't found.

Thank you.

The behaviour you are experiencing on your computer is not quite normal. Mine has never shut down with VirtualBox or playing FlightGear (flight simulator) on Linux.

Let me see what else I can find out and I will be back at you with some reply. The following two days I will be rather busy, but I will see what I can do.

Xeth

---

### Post by xeth_delta on 2008-01-31
the_blur, My laptop reaches 72 degrees without any issues, I think it even passes a bit over that temperature. The same thing as to mexicola, I will see what I can find out, and will try to reply soon, but the following two days will be very busy for me.

Xeth

---

### Post by Mad_Dawg on 2008-01-31
I don't know much about laptops, but is there a possibility of dust in it?  The first thing I do when I have a similar problem in my desktop is blow the dust out of the computer, then it is fine.

---

### Post by mexicola on 2008-01-31
> **xeth_delta said:**
> The behaviour you are experiencing on your computer is not quite normal. Mine has never shut down with VirtualBox or playing FlightGear (flight simulator) on Linux.

Let me see what else I can find out and I will be back at you with some reply. The following two days I will be rather busy, but I will see what I can do.

Xeth


Well, I haven't actually experienced shut downs since I adjusted the fan-speed in BIOS, but I've reached 80C +, and that's when the whole system starts to lag. So naturally I exit the current program to avoid a brutal shut down. It cools down to ~70 C in a minute or two, and it functions normally again.

I haven't ruled out hardware malfunction yet, though.

I would appreciate that. Thank you very much for your help!

---

### Post by Perkins on 2008-05-19
It depends a lot on the type of laptop.  Some of the ones that try to combine big features with low cost or low weight are actually capable of overheating themselves.  For example, I have a Toshiba Portege, and if I do anything too intensive with it for prolonged periods, it will overheat and halt the processor.  In my case, the easy solution was to prop it up a bit off the desk and put a big fan under it.  

If you want something portable, there are laptop cooling pads that run off of a USB port.  External fans will reduce wear and tear on your machine anyway so it will last longer.

Be very careful about adjusting the temperature sensors, the values they report are not always the actual temperature of the innermost parts of your processor.  If the OS is shutting down, you can probably adjust it without too many problems.  If it's a BIOS setting, then you probably want to double-check the temperature yourself if you can find a way.

---

