---
title: "&quot;SIOCGIFFLAGS error: No such device&quot;"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by muzungu on 2006-05-18
WARNING: Absolute newbie alert ;)

I've successfully installed Ubuntu on a Dell Inspiron 7500. At the time of installation I didn't have a Wifi PC card; I've since purchased a Netgear model and connected the laptop to my wireless network, and the internet.

But...

The network icon in the titlebar of my screen is showing some kind of error, and when I click on it I'm getting the message "SIOCGIFFLAGS error: No such device". A screengrab is attached.

There's probably a quick, easy solution to this that I'm completely oblivious to, right? 

Many thanks.

---

### Post by skippy81 on 2006-05-18
Hello mate.

Ok lets start at the begining.  Like windows, linux requires drivers for items of hardware.  Assuming all you have done is plug the network card in, I find it unlikely that it is set up properly, normally at the very least you would have to load a kernel driver module for it using "modprobe".

Can you please do the following:

1) Open a terminal window and type "lspci" copy and paste the output to this forum. 
2) Next do "lsmod" again paste the info to this forum. 
3) Finally let us know what hardware you have. 
     a) The model number AND revision number of the netgear card.
     b) Any other network cards you have in your PC.

Thx

---

### Post by muzungu on 2006-05-18
[QUOTE=skippy81]Can you please do the following:

1) Open a terminal window and type "lspci" copy and paste the output to this forum.[/QUOTE]

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:04.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:04.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)
0000:00:10.0 Communication controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
0000:06:00.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)

> 2) Next do "lsmod" again paste the info to this forum.

Module                  Size  Used by
usbhid                 30688  0
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  4
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
af_packet              20232  2
pcspkr                  3652  0
rtc                    11832  0
floppy                 52692  0
snd_es1968             26368  1
gameport               14472  1 snd_es1968
snd_ac97_codec         72188  1 snd_es1968
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_es1968,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd_page_alloc         10120  2 snd_es1968,snd_pcm
snd_mpu401_uart         6784  1 snd_es1968
snd_rawmidi            22816  1 snd_mpu401_uart
snd_seq_device          8204  1 snd_rawmidi
snd                    48644  11 snd_es1968,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
i2c_piix4               8336  0
i2c_core               19728  2 i2c_acpi_ec,i2c_piix4
prism54                47752  0
firmware_class          9472  1 prism54
yenta_socket           22540  3
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
uhci_hcd               28048  0
usbcore               104188  3 usbhid,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  837
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

> 3) Finally let us know what hardware you have. 
     a) The model number AND revision number of the netgear card.

It's a Netgear Wireless-G PC Adaptor, Model #WG511NAR (refurbished). Sorry, but I don't know where the revision number would be...

>      b) Any other network cards you have in your PC.

There's just the one PC card slot. There's an ethernet PC card that I yanked to make room for the Netgear one.

Thanks for your assistance, and your quick reply :-D

---

### Post by muzungu on 2006-05-20
Since this error was caused by my WiFi card not being present at the time of installation, I decided to reinstall with the card in place.

... And it now appears to be up and running without issue. Who knew?!

:mrgreen:

---

### Post by Flying caveman on 2006-05-20
I just started having the same problem:neutral:  my wireless card was workin' now its not.  Airlink wireless pci card AWLH 3025 Although I think Ubuntu original was detecting it and calling it something else.

> [SIZE="1"]sherman@ubuntu:~$ lsmod
Module                  Size  Used by
af_packet              20232  2
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
joydev                  9280  0
analog                 10528  0
gameport               14472  1 analog
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
ohci1394               30644  0
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
nvidia               3711364  12
agpgart                32328  2 intel_agp,nvidia
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usbhid                 30688  0
e100                   32768  0
mii                     5248  1 e100
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104316  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  710
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
[/SIZE]

---

