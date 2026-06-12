---
title: "Nic Driver Not Loading"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by NY Hopefull on 2007-03-03
Hi All:
I set up Ubunto 6.1 successfully but it did not detect my NIC (or my grapgics card). The nic is good under wWndowsXP and there are drivers availablefor Linux. Since I cannot get  to the internet from this computer while running Linux, I downloaded the driver from the web, burned it to a cd and copied it to the Ubunto desktop. Nic is a Marvell - Yukon Gigabit Ethernet 10/100/1000Base-T. 
I have tried to install the driver as sudo-i, only to be told that I need binary libraries and need to be in the same path as "lg", (whatever that is). Needless to say, this is a very frustrating experience. It is really sad that Ubunto has neglected such a fundamental issue as a simple means of driver loading.
Can anyone help me with this. I really would like to use this distro. Help. Please.

---

### Post by dbott67 on 2007-03-03
I've got a D-Link card in my computer.  I've highlighted the specific information for my PC in red, where as yours will be different.

Can you post the output of the following commands:
```
dbott@thedrake:~$ **sudo lshw -C network**
  *-network
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                                                                                                                     00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes **[COLOR="Red"]driver=8139too[/COLOR]** driververs                                                                                                                     ion=0.9.27 duplex=full ip=192.168.1.106 link=yes multicast=yes port=MII speed=10                                                                                                                     0MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:185

```
```
dbott@thedrake:~$ **lsmod**
Module                  Size  Used by
sg                     37920  0
scsi_mod              139496  1 sg
smbfs                  66552  3
snd_rtctimer            3340  0
iptable_filter          3072  0
ip_tables              22400  1 iptable_filter
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
fglrx                 388908  8
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
i2c_core               21904  1 i2c_acpi_ec
vfat                   13440  0
fat                    53020  1 vfat
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
lp                     11844  0
snd_emu10k1_synth       7296  0
snd_emux_synth         37376  1 snd_emu10k1_synth
snd_seq_virmidi         7680  1 snd_emux_synth
snd_seq_midi_emul       7168  1 snd_emux_synth
snd_seq_dummy           3844  0
snd_intel8x0           33692  4
snd_seq_oss            33536  0
[B][COLOR="Red"]8139too                26880  0
mii                     5888  1 8139too[/COLOR][/B]
snd_seq_midi            9376  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                51984  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           117284  2 snd_emu10k1_synth
snd_rawmidi            25504  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         93216  2 snd_intel8x0,snd_emu10k1
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
emu10k1_gp              3840  0
gameport               15496  2 emu10k1_gp
snd_pcm                89864  5 snd_intel8x0,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          8716  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25220  6 snd_rtctimer,snd_seq,snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9376  2 snd_emux_synth,snd_emu10k1
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd                    55268  21 snd_emux_synth,snd_seq_virmidi,snd_intel8x0,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
floppy                 62148  0
rtc                    13492  1 snd_rtctimer
pcspkr                  2180  0
psmouse                36100  0
serio_raw               7300  0
soundcore              10208  1 snd
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
snd_page_alloc         10632  3 snd_intel8x0,snd_emu10k1,snd_pcm
intel_agp              22940  1
agpgart                34888  2 fglrx,intel_agp
tsdev                   8000  0
evdev                   9856  1
usbhid                 39904  0
ext3                  135816  2
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
uhci_hcd               33808  0
usbcore               130820  5 usbhid,ehci_hcd,ohci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  4
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

```
```
dbott@thedrake:~$ **cat /etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```
```
dbott@thedrake:~$ **sudo lspci**
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
0000:02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
0000:02:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 07)
**[COLOR="Red"]0000:02:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)[/COLOR]**
0000:02:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:0d.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:0d.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:02:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
```

---

### Post by dbott67 on 2007-03-03
Update:  it appears to be a kernel issue.  The kernel 2.6.20 apparently cures it.  Check post 9 & 11 of this thread [http://www.ubuntuforums.org/showthread.php?t=365385](http://www.ubuntuforums.org/showthread.php?t=365385)

-Dave

---

### Post by NY Hopefull on 2007-03-03
Hi dbott67:
Thanks for your prompt response.
Since I'm not net/internet capable on the computer at issue, Im going to have to run back and forth between computers. I'll try to pick out what you might be looking for.
lshw found the ethernet controller correctly as the Marvell on id.4, ethr 0
driver: skge ver 1.5
lsmod shows skge - 38670, 0
cat.etc/network/interfaces:
  auto lo
  iface lo net loopback
  auto eth0
  iface eth0 inet dhcp
lspic - 
ethernet controller: Marvell etc. :unknown device 4364 (rev 12)
Hope I hit the right stuff.
Thanks

---

### Post by dbott67 on 2007-03-03
Hi NY Hopefull,

I'm not sure if you caught my 2nd post or not.  I've been doing some additional searching regarding your NIC and it appears as though many are having the same problem when using Edgy.  Updating the kernel appears to be the solution --- but how to update when you can't get online!!! :)

Anyhow, there are a few options:

1. Install the latest version of Feisty (7.04 Herd 5, I think) from here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

2. Install Dapper 6.06

3. Install a different NIC so that you can get online and then update the kernel.  Check to see if Yukon-Marvell works, if so, remove other NIC.

4. Try using ndiswrapper and the proprietary Windows drivers (which are the .inf & .sys files for your NIC).

Hope this helps,
Dave

---

### Post by NY Hopefull on 2007-03-07
Hi dbott67
Tried the up grade to herd 4 and it worked. I can now get on line.
However, I could not load the driver for my nvidia 7300 card. 
Rather than post, I'll read all of the wisdom in the other posts first.
Thanks for your help!

---

