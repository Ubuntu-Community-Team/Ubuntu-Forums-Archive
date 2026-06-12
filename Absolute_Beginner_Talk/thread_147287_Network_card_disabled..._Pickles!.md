---
title: "Network card disabled... Pickles!"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-19
I've gone thru the tutorials, wiki, troubleshooters, wireless installation guides, etc, but no good. When I run:
```
john@laptop:~$ sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:06:5b:e1:ba:40
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.1.223 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network:1 DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:2c:52:6b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper ip=192.168.1.123 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f8ffc000-f8ffdfff irq:5

```
```
john@laptop:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```
 Also, as soon as I run sudo modprobe ndiswrapper, my cat5 connection dies...

sudo lspci -v gets this:
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at f8ffc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

---

### Post by varunus on 2006-03-19
Can you post the output of "lsmod" in a terminal?  Also "ifconfig" in a terminal.

Does typing "sudo iwconfig wlan0 essid NAME_OF_SSID_HERE" change the SSID value of wlan0?  Also, does typing "sudo ifconfig wlan0 up" let you give it an SSID value?

---

### Post by Papa-san on 2006-03-20
results of lsmod:
```
john@laptop:~$ lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_ich           5132  0
speedstep_lib           4228  1 speedstep_ich
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_ich,cpufreq_stats
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
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
yenta_socket           22540  2
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9504  2 tpm_atmel,tpm_nsc
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
tsdev                   7616  0
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
evdev                   9088  0
snd_seq_midi            8608  0
snd_rawmidi            22816  1 snd_seq_midi
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21764  2 snd_pcm,snd_seq
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    48644  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9184  1 snd
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
dm_mod                 50364  4
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
ide_disk               16128  3
ide_generic             1664  0
piix                    9476  1
ide_core              125268  3 ide_disk,ide_generic,piix
unix                   24624  675
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

```

john@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:5B:E1:BA:40
          inet addr:192.168.1.223  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fee1:ba40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1805 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1471002 (1.4 MiB)  TX bytes:239618 (234.0 KiB)
          Interrupt:11 Base address:0xec80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18976 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1421105 (1.3 MiB)  TX bytes:1421105 (1.3 MiB)

I am not sure where to find the name of ssid(?)

---

### Post by varunus on 2006-03-20
Ok, lets try the following.  First, type "sudo ifconfig wlan0 up" in a terminal.  Then, type "sudo iwlist wlan0 scan" in a terminal.  Do you see a list of wireless networks come up?

If so, can you open the GNOME networking tool in System->Administration->Networking and configure your wireless from there?

---

### Post by Papa-san on 2006-03-20
OK...
I'm not sure what I'm supposed to do in the networking panel. I thought I had everything right. I ran the things you suggested, and got this: john@laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:12:17:C8:CE:62
                    ESSID:"Rage"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:0/100  Signal level:-29 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:54 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by varunus on 2006-03-20
Huh...it looks to me like your wireless should be working if you have everything configured.  As you can see from that output, your card detects one network in range, with name "Rage".  If the GNOME networking panel isn't letting you set this up, then I don't know what's wrong, honestly.  How do you have it set up?  Can you post screenshots?

Do you have "default gateway" set to wlan0 in the networking panel?  This needs to be the case to use your wireless.

Also, if you'd like to try configuring it from the terminal:
type, first of all:
```
sudo ifconfig wlan0 up
#that enables the wireless card

sudo iwconfig wlan0 essid Rage
#this tells it to use the rage network

sudo dhclient wlan0
#this gets an IP address automatically

```
After that, you should have internet...

---

### Post by Papa-san on 2006-03-20
OK... I tried it both ways, and it didn't work.
The wlan0 tends to come up after boot as 'inactive'. When I disable the eth0, enable the wlan0 and set it as default, the setting doesn't 'take' right. (It hangs when trying to make the changes. It seems I might have screwed something else up.  
I don't know how to do or send (post) screenshots, but I will look it up and try to do it. Anything in particular to show?

(P.S.- thanks for the help!)

---

### Post by mweston on 2006-03-20
I'm having a similar problem. Using NDISWRAPPER, I got the wireless to work...kind of. 

I can't seem to connect with my access point. Wlan 0 scan sees it, but "sudo ifconfig wlan0 up" gives an error - unrecognised command "up"- and "sudo dhclient wlan0 " comes back with:

/etc/dhcp3/dhclient.conf line 1: no option named dhcp-class identifier
send dhcp-class-identifier "NetcfgDHClient"
    ^
/etc/dhcp3/dhclient.conf line 1: semicolon expected
^
Listening on LPF/wlan0/00:11:50:07:5b:46
Sending on LPF/wlan0/00:11:50:07:5b:46
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 676 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 676 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 676 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 676 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 676 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 676 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I'm at a loss - I don't understand the errors.  Please advise.
Thanks,

---

### Post by Papa-san on 2006-03-21
This is what I get with the same commands. I tried it last night, and it took out my eth0 as well:

```
john@laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:2c:52:6b
Sending on   LPF/wlan0/00:90:4b:2c:52:6b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
When I entered the lines that were suggested in the terminal, the wireless showed up, bumped the eth0 and nothing would connect.

What is this sit0 that doesn't have a hardware addy?  And why is it seeking DHCP? I thought I set it to the other type...?!?

---

