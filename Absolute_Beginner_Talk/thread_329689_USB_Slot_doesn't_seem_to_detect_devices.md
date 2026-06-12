---
title: "USB Slot doesn't seem to detect devices"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-01-02
I tried to open my brother's sony network walkman usb device and Ubuntu didn't respond. There were no Media devices detected whatsoever. I tried to print but Ubuntu still still doesn't seem to be connected to my Printer. I connected my USB mouse and the mouse lighted up; the bad thing is that, Ubuntu doesn't react to any mouse movement. 

What could my problem be and how can I solve it?

---

### Post by jblebrun on 2007-01-02
> **wersdaluv said:**
> I tried to open my brother's sony network walkman usb device and Ubuntu didn't respond. There were no Media devices detected whatsoever. I tried to print but Ubuntu still still doesn't seem to be connected to my Printer. I connected my USB mouse and the mouse lighted up; the bad thing is that, Ubuntu doesn't react to any mouse movement. 

What could my problem be and how can I solve it?

Can you try plugging in the devices and then posting the tail-end of the output of dmesg here? (Just the last 20-30 lines should be plenty, no need to put the whole thing). 

Also, post the output from the command 

lsmod

---

### Post by wersdaluv on 2007-01-02
dmesg:

[17179599.416000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179599.516000] NET: Registered protocol family 10
[17179599.516000] lo: Disabled Privacy Extensions
[17179599.520000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179599.520000] IPv6 over IPv4 tunneling driver
[17179599.548000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179599.548000] agpgart: Device is in legacy mode, falling back to 2.x
[17179599.548000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179599.548000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179599.780000] uhci_hcd 0000:00:10.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[17179599.996000] apm: BIOS not found.
[17179609.548000] ra0: no IPv6 routers present
[17179611.724000] Bluetooth: Core ver 2.8
[17179611.724000] NET: Registered protocol family 31
[17179611.724000] Bluetooth: HCI device and connection manager initialized
[17179611.724000] Bluetooth: HCI socket layer initialized
[17179611.788000] Bluetooth: L2CAP ver 2.8
[17179611.788000] Bluetooth: L2CAP socket layer initialized
[17179611.816000] Bluetooth: RFCOMM socket layer initialized
[17179611.816000] Bluetooth: RFCOMM TTY layer initialized
[17179611.816000] Bluetooth: RFCOMM ver 1.7
[17180947.960000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17180947.960000] agpgart: Device is in legacy mode, falling back to 2.x
[17180947.960000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17180947.960000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17181142.156000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17181142.156000] agpgart: Device is in legacy mode, falling back to 2.x
[17181142.156000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17181142.156000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode


lsmod:

Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  8 
via                    48224  2 
drm                    74644  3 via
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
ndiswrapper           208656  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
af_packet              24584  4 
joydev                 11200  0 
snd_via82xx            30360  2 
snd_via82xx_modem      16648  0 
gameport               17160  1 snd_via82xx
pcmcia                 40380  0 
usbhid                 45152  0 
snd_ac97_codec         97696  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            3456  1 snd_ac97_codec
snd_mpu401_uart        10240  1 snd_via82xx
snd_pcm_oss            47360  0 
snd_pcm                84612  5 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
via_agp                11264  1 
via_rhine              26116  0 
agpgart                34888  2 drm,via_agp
tsdev                   9152  0 
snd_seq_midi            9984  0 
snd_rawmidi            27264  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25348  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
mii                     6912  1 via_rhine
i2c_viapro              9876  0 
i2c_core               23424  2 i2c_ec,i2c_viapro
rt2500                188004  1 
snd                    58372  15 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
snd_page_alloc         11400  3 snd_via82xx,snd_via82xx_modem,snd_pcm
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
via_ircc               28948  0 
evdev                  11392  1 
pcspkr                  4352  0 
irda                  214332  1 via_ircc
psmouse                41352  0 
serio_raw               8452  0 
crc_ccitt               3200  1 irda
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
via82cxxx              10500  0 [permanent]
generic                 6276  0 
thermal                15624  0 
processor              31560  1 thermal
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

### Post by jblebrun on 2007-01-02
Hmm... I'm at a loss.... this line looks fishy:
[17179599.780000] uhci_hcd 0000:00:10.1: Unlink after no-IRQ? Controller is probably using the wrong IRQ. 

It looks like you're using a USB network card though, is that true? If so, is it working OK? 

Also, plug your USB mouse in. After the light comes on, go into a terminal window and type 
**cat /dev/input/mice**

Then move the mouse and see if you get a bunch of garbage characters (which would indicate the the USB mouse is working, and that something is wrong with your X configuration).

---

### Post by wersdaluv on 2007-01-03
For some reason, when I booted my laptop a while ago, the usb mouse is already working. There is just one big problem; whenever I move the usb mouse, the mouse pointer responds very slowly. What can I do?

---

### Post by gachmadi on 2007-01-03
Same issue with me.  After I upgraded to 6.10 USB seems slow and splash sound loops.  I have to unplugged usb devices first then plug back in after Ubuntu desktop loaded.
Weird thing when I boot with 6.10 live CD didn't get the problem.  It seems I have to rolling back to 6.06.

---

