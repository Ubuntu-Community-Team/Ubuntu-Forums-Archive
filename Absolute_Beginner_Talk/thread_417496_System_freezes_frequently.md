---
title: "System freezes frequently"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Buster95 on 2007-04-21
System freezes frequently while using Edgy 6.10 on a laptop. No add-ons (as far as I know). ADSL connection via Netgear DG 834G. The freezes are total. Nothing works except the start button, which can still force a shutdown and reboot.

Tried to log process events to get a clue as to what was doing it and got the following log message which I presume relates to the touchpad. I didn't have a mouse connected at the time. There was no freeze associated with the logging at the time. Obviously, if the system froze, I'd have lost all the log anyhow.

Can anyone give me a clue as to what it means?

dexter@dexter-laptop:~$ tail -f /var/log/messages
Apr 22 07:46:59 dexter-laptop kernel: [17180591.668000] Linking with NETGEAR
Apr 22 07:47:02 dexter-laptop kernel: [17180594.224000] Linking with NETGEAR
Apr 22 07:47:04 dexter-laptop kernel: [17180595.848000] psmouse.c: bad data from KBC - bad parity
Apr 22 07:47:04 dexter-laptop kernel: [17180595.848000] psmouse.c: bad data from KBC - bad parity
Apr 22 07:47:04 dexter-laptop kernel: [17180595.852000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Apr 22 07:47:04 dexter-laptop kernel: [17180595.860000] psmouse.c: bad data from KBC - bad parity
Apr 22 07:47:04 dexter-laptop kernel: [17180595.860000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Apr 22 07:47:04 dexter-laptop kernel: [17180595.864000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Apr 22 07:47:04 dexter-laptop kernel: [17180595.872000] psmouse.c: bad data from KBC - bad parity
Apr 22 07:47:04 dexter-laptop kernel: [17180595.872000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 4
Apr 22 07:47:04 dexter-laptop kernel: [17180595.876000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
Apr 22 07:47:04 dexter-laptop kernel: [17180595.876000] psmouse.c: issuing reconnect request
Apr 22 07:47:04 dexter-laptop kernel: [17180596.548000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x81a0b1, caps: 0xa04713/0x204000
Apr 22 07:47:04 dexter-laptop kernel: [17180596.584000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

---

### Post by Sef on 2007-04-21
What kind of laptop are you using?

---

### Post by Buster95 on 2007-04-21
It's just a "Stylenote" (Clevo?) unit using an Intel Core Duo T2250 processor.

---

### Post by Buster95 on 2007-04-24
Any suggestions on this freezing problem. My searches point to a dual core processing problem. 

My last freeze occurred when I was changing the time! That was the only process running.

Cheers

Also experienced a freeze BEFORE logging in

---

### Post by Buster95 on 2007-04-27
After much experimenting, I find that my system freezes seem to be random. They can occur any time. I even got one hangup on start up when the Ubuntu screen loaded up. Mostly it seems to occur when starting an application. They can occur as frequently as every few minutes, yet sometimes the system lasts for hours. I still can't find a reproducible failure pattern.

After reviewing other "freeze" reports, I tried disabling my wireless link and connecting by an ethernet cable. It still froze. I then disabled the ethernet link as well and didn't get a freeze, even when I started Firefox and some other applications a few times.

Is it possible that my connection is somehow triggering the freeze? Or, could it be that Firefox causes it when it handshakes with the modem/router?

Apart from trying different applications to see if I can reproduce it, I'm not sure how to troubleshoot this problem.

My system is plain vanilla Edgy with no add-ons (as far as I know) or any other tricky stuff. Loaded from a disk that runs successfully on another computer.

Appreciate any guidance.

---

### Post by r.k.maroon on 2007-04-27
Could you find out what ethernet-chip is in the laptop?  I'm guessing it's an integrated card? Also the output of "lsmod" could help.  It might be that the wrong module is loaded for your ethernet-card and causing a pretty serious lock-up.  A bit worrisome that it isn't causing a more nicely failing kernel panic or somesuch in that case ....

I still think it's worth a shot though.

---

### Post by Buster95 on 2007-04-27
> **r.k.maroon said:**
> Could you find out what ethernet-chip is in the laptop?  I'm guessing it's an integrated card? Also the output of "lsmod" could help.  It might be that the wrong module is loaded for your ethernet-card and causing a pretty serious lock-up.  A bit worrisome that it isn't causing a more nicely failing kernel panic or somesuch in that case ....

I still think it's worth a shot though.

Thanks for the response,
You are right. It's an integrated card. When I get home and back onto that infernal machine, I'll try to find out and post it. The laptop is one of those Taiwanese clone units. The device manager can't recognise most of the bits.

Also, I share your suspicion about the ethernet card. I had quite an adventure getting the internet connection to work at all. I had to disable ipv6 and then use OpenDNS before it would resolve a website, even though I could ping it. Even now, I can't send large messages or attachments via webmail or T'Bird. There's something dodgy going on in there, but I can't find it.

Haven't had a kernel panic yet.

Cheers

---

### Post by Buster95 on 2007-04-27
In response to request for lsmod data. Hope it means more to you than to me.
Cheers

dexter@dexter-laptop:~$ lsmod
Module                  Size  Used by
isofs                  38076  1 
udf                    89348  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  2 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
af_packet              24584  4 
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            30360  0 
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  1 snd_via82xx
snd_ac97_bus            3456  1 snd_ac97_codec
snd_mpu401_uart        10240  1 snd_via82xx
snd_rawmidi            27264  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
joydev                 11200  0 
tsdev                   9152  0 
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
r8187                  46596  0 
snd_pcm                84612  5 snd_via82xx,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  2 snd_seq,snd_pcm
ieee80211_rtl          85640  1 r8187
snd                    58372  15 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  3 snd_via82xx,snd_hda_intel,snd_pcm
sg                     37404  0 
sdhci                  20108  0 
mmc_core               32136  1 sdhci
via_rhine              26116  0 
psmouse                41352  0 
serio_raw               8452  0 
mii                     6912  1 via_rhine
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
evdev                  11392  1 
pcspkr                  4352  0 
ext3                  142856  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  4 r8187,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  1 
cdrom                  38944  1 ide_cd
via82cxxx              10500  0 [permanent]
sd_mod                 22656  3 
generic                 6276  0 
sata_via               10500  2 
libata                 74892  1 sata_via
scsi_mod              144648  3 sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by LuisGMarine on 2007-04-27
I know this might be a bit off topic, but when I first installed Ubuntu I seemed to be having some issues about my desktop locking up on random times and places.  I could sometimes runt he system for 5 minutes before it would lock up, and other times I could go on for as long as an hour before it locked up again.

My cure?  I just upgraded to the nvidia drivers and it seemed to fix the whole problem!  So like I said, you might have already pin-pointed the cause, but give upgrading your video drivers a shot and see if it works.

-LuisGMarine

---

### Post by Buster95 on 2007-04-28
I don't know whether this has anything to do with my frequent crashes. Can anyone guide me on what this might mean?
Thanks

dexter@dexter-laptop:~$ tail -f /var/log/messages
Apr 28 17:55:20 dexter-laptop gconfd (dexter-4771): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Apr 28 17:55:20 dexter-laptop gconfd (dexter-4771): Resolved address "xml:readwrite:/home/dexter/.gconf" to a writable configuration source at position 1
Apr 28 17:55:20 dexter-laptop gconfd (dexter-4771): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Apr 28 17:55:20 dexter-laptop gconfd (dexter-4771): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Apr 28 17:55:20 dexter-laptop gconfd (dexter-4771): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Apr 28 17:55:21 dexter-laptop kernel: [17179627.520000] Linking with NETGEAR
Apr 28 17:55:24 dexter-laptop kernel: [17179630.072000] Linking with NETGEAR
Apr 28 17:55:25 dexter-laptop kernel: [17179630.440000] Associated successfully
Apr 28 17:55:25 dexter-laptop kernel: [17179630.440000] Using G rates
Apr 28 17:55:29 dexter-laptop gconfd (dexter-4771): Resolved address "xml:readwrite:/home/dexter/.gconf" to a writable configuration source at position 0

---

### Post by Buster95 on 2007-04-29
Still searching for clues here.
Regarding the following lshw command, the ethernet interface is identified (VT 6102 (Rhine II) and vendor (Via Technologies). However, the presence of the wireless network is acknowledged, but the product and vendor is not identified. Does that imply a problem?

Second question; running /var/log/messages gives a never-ending "linking with Netgear" message every two to three seconds (I'm using a Netgear DG834G as my modem/wireless router). Why? Does that imply that it's having trouble acquiring it?

dexter@dexter-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 7c
       serial: 00:90:f5:57:ba:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine ip=192.168.0.6 multicast=yes
       resources: ioport:4800-48ff iomemory:cb400400-cb4004ff irq:50
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:12:7d:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.171 multicast=yes wireless=802.11b/g link..

---

### Post by qrees on 2008-01-20
I have simillar problem. System is no longer freezing after I have removed via82cxxx module. The problem is, that without it, there is no DMA, so system is just unusable... Maybe someone knows if this module can be replaced with other (is this possible at all??). Or maybe there is some other solution...

---

### Post by hobo on 2008-01-20
Why not run hardware diags first to determine that the laptop is not at fault? 
D/L UBCD and boot it up.

 [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by qrees on 2008-01-21
> **hobo said:**
> Why not run hardware diags first to determine that the laptop is not at fault? 
D/L UBCD and boot it up.

 [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Because windows is working fine with DMA turned on, so it's software problem.

---

