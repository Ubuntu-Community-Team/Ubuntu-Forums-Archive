---
title: "My wireless works with WPA, but not with anything else"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2006-12-17
Hey guys. I've tried just about every tutorial available to try and get WPA wireless working on this damn machine, but so far no luck. I even tried airhack (which looks totally illegal), and even that didn't work. I'm just about to give up, so I'm going to post every output I can and hope that one of you will be able to help me.
```

uname -a
Linux keith-laptop 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux

ifconfig -v
eth0      Link encap:Ethernet  HWaddr 00:40:CA:CE:DF:29
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33887361 (32.3 MiB)  TX bytes:3262537 (3.1 MiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:505 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:37548 (36.6 KiB)  TX bytes:37548 (36.6 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:07:C4:D1
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:0 errors:92 dropped:0 overruns:0 frame:0
          TX packets:1383995 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:58127722 (55.4 MiB)
          Interrupt:193 Base address:0x4000

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"WF"
          Mode:Managed  Frequency=2.452 GHz  Bit Rate:11 Mb/s   Tx-Power:1 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
##The network "WF" was my dorm at college, however I'm 200 miles away from it now. I doubt I'm going to connect to that router.

lsmod
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
via                    47968  1
drm                    73236  2 via
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
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
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
dm_mod                 58936  1
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
af_packet              22920  10
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_viapro              8980  0
i2c_core               21904  2 i2c_acpi_ec,i2c_viapro
snd_via82xx            28824  2
gameport               15496  1 snd_via82xx
joydev                 10048  0
snd_via82xx_modem      15368  0
snd_ac97_codec         93216  2 snd_via82xx,snd_via82xx_modem
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  1
snd_mixer_oss          18688  1 snd_pcm_oss
snd_mpu401_uart         7808  1 snd_via82xx
tsdev                   8000  0
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
via_ircc               26900  0
snd_pcm                89864  4 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
pcmcia                 40508  0
rtc                    13492  0
irda                  187068  1 via_ircc
snd                    55268  14 snd_seq_oss,snd_seq,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         10632  3 snd_via82xx,snd_via82xx_modem,snd_pcm
rt2500                176612  1
soundcore              10208  2 snd
pcspkr                  2180  0
psmouse                36100  0
serio_raw               7300  0
crc_ccitt               2304  1 irda
via_rhine              23940  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
mii                     5888  1 via_rhine
yenta_socket           28428  1
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
amd64_agp              12356  1
agpgart                34888  2 drm,amd64_agp
evdev                   9856  2
ext3                  135816  2
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  3 ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  5
via82cxxx               9988  0 [permanent]
generic                 5124  0
thermal                13576  0
processor              23360  2 powernow_k8,thermal
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

iwscan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:0F:B3:14:FF:32
                    Mode:Managed
                    ESSID:"Goodwin"
                    Encryption key:on
                    Channel:9
                    Quality:0/100  Signal level:-17 dBm  Noise level:-192 dBm
##"Goodwin" is the network I'm wanting to connect to.

cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto ra0
iface ra0 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid Goodwin
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 1939b423c8bf5554a974f4d46c7612e3ff84dae5e34d67737a76d5ec2904f467

cat /etc/resolv.conf
search domain.actdsltmp
nameserver 216.165.129.157
nameserver 216.170.153.146
nameserver 192.168.0.1
nameserver 192.168.0.1

```
I know that's a ridiculous amount of stuff to look through, but it'd be muuuuuch appreciated if someone can help me figure this out. Thanks!

---

### Post by k1001001 on 2006-12-21
After numerous attempts to get wireless going, and after downloading several programs, I think I've killed my wireless card. It won't even connect to unsecured networks anymore. I'm wondering if there is a way to get this working without wiping my hard drive and re-installing Ubuntu. I can post some more information if needed. Thanks!

---

### Post by bernied on 2006-12-21
you'll need to post a few details, like
- what model is the card - more detail is better?
- what is the output of lspci (from a terminal window)?
- do you know what driver it uses? is the driver loaded?
- what have you tried so far - a link to a web-page can be helpful?
- have you used a live-cd, where the card 'just worked'? If so, which live-cd?
- and what security settings do you have on the wifi access point? can you make wireless work with security disabled?

Please don't wipe your hard-drive and reinstall, please persist.

In my experience, wireless cards are especially troublesome mostly because the manufacturers are not interested in helping the linux communities - it's the same situation as with graphics cards. It took me ages to make a Netgear WG511 card work, because Netgear made about four different versions of this thing, with different hardware in each. I had the v2 (made in China), which was different from the v2 (made in Taiwan). It can make you want to poke your own eyes out.

---

### Post by k1001001 on 2006-12-22
I don't really know how to check the model of the card, but lspci lists it as this:
Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)

Here's the entire output:
```

0000:00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890  South]
0000:00:09.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 0 1)
0000:00:0b.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 50)
0000:00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

```

I don't know how to find the driver either. I know I followed one of the HowTos on this forum, and it told me to download a driver and then use ndiswrapper. If you could tell me how to find that, it'd probably be a lot more helpful that my description.

I've tried many many numerous attempts to connect to a network running WPA-PSK security. That's what caused the problem with my wireless. It would work fine on unsecured wireless networks, and I didn't try it on WEP, but it at least worked on unsecured networks. I've tried several HowTos on this forum, but none of them worked. I also downloaded network-manager-gnome, Knetwork Manager, Wifi-Radar, airhack (which looks totally illegal), and some other program (I forgot the name), but none of those worked either. What really killed my wireless was when I let another guy (my personal Linux guru) try to get it working. I don't know what HowTo he was looking at, but whatever he did killed my wireless permanently. I can detect networks, but I just can't connect to them.

It worked once upon a time, including on the Live DVD that I have, but now it does not seem to want to work at all. You'll probably need more information than what I've provided, so just tell me what you need to know. I know how to use terminal pretty well, but I do not know what all commands will give me the information you need.

EDIT: An interesting update
I followed [this]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") tutorial, which has gotten me closer to connecting that anything recently. I set my wireless router to unsecured ([screenshot]("http://img.photobucket.com/albums/v62/k1001001/wirelesssecurity.png")) and I tried to connect, but it asked for a passkey when trying to connect ([screenshot]("http://img.photobucket.com/albums/v62/k1001001/keyrequired.png")). It also does not have the option to connect to WPA networks, only WEP in 128-bit passphrase, 64/128 bit hex key, and 64/128 bit ASCII key. I do not know how to use WEP keys, so I really have no idea how I could set a WEP key. None the less though, I still cannot connect with no security at all.

---

### Post by bernied on 2006-12-22
I suspect that the card was working fine, with the correct driver, you had just not figured out how to do the WPA part (which I also find difficult). But I think since then, several different jabs at the problem have made it worse, not better.

The driver for this card is rt2500, a linux open source driver, which is why it works from a live dvd. In this case the manufacturers have been very cooperative and helped linux developers to produce an open source driver - so I apologise for my rant earlier, it clearly does not apply to ralink. (see here: [http://sourceforge.net/projects/rt2400](http://sourceforge.net/projects/rt2400))

So the first thing to check is whether this driver is loaded (this would probably be a module, unless your guru has recompiled your kernel and built the driver in), to see if a module is loaded, you use the lsmod command, like so:
```
lsmod
```this should produce a huge list of modules that are running in the kernel. If this doesn't work, try ```
sudo lsmod
```which means do the same thing, only with administrative privileges, you'll need to enter your password. (I don't have a ubuntu install available here, so don't know what needs administrative privileges)
Because this is a huge list and you might miss it scanning by eye, you can direct the output to a searching command, called grep, like so (use sudo again if you needed it before)
```
lsmod | grep rt2500
```so the | character is an instruction to 'pipe' the output from one application to another, in this case it means list the modules, then pipe the output to grep, and look for a line with 'rt2500' in it.

Did you get any response? Was there a line for the driver? (post it here)

If it is there, then the driver is loaded, but is it being used? Were there any other modules listed with it on the right hand side (the 'used by' column)? I wonder whether another driver is being used for the hardware, perhaps ndiswrapper. ndiswrapper is a neat tool that takes windows hardware drivers and 'wraps' them so that they can be used within linux. This is great for hardware that doesn't have a linux driver (related to my rant about manufacturers earlier). So you followed a howto that told you to use ndiswrapper, this should have worked, but only if you used a windows driver that works with the card.

BUT, your card does have a linux driver, so you do not need to use ndiswrapper. It's worth having a look about to see if ndiswrapper is running as well, because it may be competing with the rt2500 driver for control of the card, which will be confusing. I think this is a module, so use the same command as before (again use sudo if you needed it before)
```
lsmod | grep ndis
```Is there any output? I might be wrong about it being this being a kernel module, maybe it is running as a normal application, you can list applications that are running with the ps command, but it normally only lists applications that you yourself have started, so use the -e (for everybody) option. I also like the -f option, as it gives you the entire command that was used to run the application, so
```
ps -ef
``` will give you a list of all running processes, some of them you might find familiar. because it's a long list, again you can pipe the output to grep to search for what you want
```
ps -ef | grep ndis
```notice when you do this you get the command 'grep ndis' as output, this is because the grep command is an application, and the command you used to start it has 'ndis' in it.

Was there another line? Is ndiswrapper running as an application (process)? 
If so, the first number on its line is it's process ID, you can use that number to stop (kill) it.

But, we're still in diagnostic stage, so don't kill anything yet.
So far, we should know whether
- the rt2500 module is running (loaded)
- the ndiswrapper module is loaded
- ndiswrapper is running as a process (application)

Once we figure out the hardware stuff, we also need to get the networking part sorted. The output to the following might be helpful for that (I'll explain what this stuff means when we get to use it). I recommend that you read the manual (man) pages for each of these commands though - to read a manual page, type 'man command' where command is the thing you want to know about, eg 'man ifconfig'
```
sudo ifconfig -a
sudo iwconfig -a
cat /etc/network/interfaces
```

---

### Post by k1001001 on 2006-12-22
Thanks so much for taking the time to do this.

Here is the output for lsmod | grep rt2500:
```
rt2500                176612  1
```

lsmod | grep ndis:
```
ndiswrapper           177364  0
usbcore               130820  5 ndiswrapper,usb_storage,ehci_hcd,uhci_hcd
```

ps -ef | grep ndis:
```
keith     5735  5513  0 12:56 pts/0    00:00:00 grep ndis
```

ps -ef | grep rt2500:
```
keith     5897  5513  0 13:03 pts/0    00:00:00 grep rt2500
```

So apparently the driver is loaded somewhere, but it is not running.

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:40:CA:CE:DF:29
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1171 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:931754 (909.9 KiB)  TX bytes:168581 (164.6 KiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:193 errors:0 dropped:0 overruns:0 frame:0
          TX packets:193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9672 (9.4 KiB)  TX bytes:9672 (9.4 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:07:C4:D1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1091222 (1.0 MiB)
          Interrupt:193 Base address:0xc000

```

iwconfig (-a is not an option)
```

lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"WF"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:54 Mb/s   Tx-Power:0 dBm 
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-192 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```
This part I find to be the weirdest. The network "WF" was my dorm network at college, but it is 250 miles away. For some reason though, this is the only network that iwconfig will show.

cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug #subsystem.
#mapping hotplug
#script grep
#map eth0

#auto ra0

#iface ra0 inet dhcp
#pre-up ifconfig ra0 up
#pre-up ifconfig ra0 down
#pre-up ifconfig ra0 up
#pre-up ifconfig ra0 down
#pre-up iwconfig ra0 essid "Goodwin"
#pre-up iwconfig ra0 mode Managed
#pre-up iwpriv ra0 set AuthMode=WPAPSK
#pre-up iwpriv ra0 set EncrypType=TKIP
#pre-up iwpriv ra0 set WPAPSK="key"
#pre-up ifconfig ra0 up

```
The tutorial I posted told me to comment out every line except those pertaining to "lo" so that's what I did.

Maybe I just need to reinstall the Linux driver that you posted a link to, and then have it actively loaded. After I do that, then Network Manager could possibly be up and running again. Could you help me do that?

---

### Post by bernied on 2006-12-23
> Here is the output for lsmod | grep rt2500:
```
rt2500 176612 1
```
lsmod | grep ndis:
```
ndiswrapper 177364 0 
usbcore 130820 5 ndiswrapper,usb_storage,ehci_hcd,uhci_hcd
```
So the rt2500 driver is loaded, no need to install this again. Curiously, the ndiswrapper driver is also loaded, but it is being used by the USB system, so be very careful about changing it - you might lose functionality of a USB device (ndiswrapper works for devices other that wireless drivers). There are commands you can issue to ndiswrapper to find out what it is running.
> The tutorial I posted told me to comment out every line except those pertaining to "lo" so that's what I did.
This is a bit tricky - I imagine that this was some graphic software that controls network devices, and over-rides the init system. Without knowing what this is, and whether or not it is running, I can't comment on it. Can you remember what it was?

What I suggest now might conflict with software that you've installed, but I don't know what you installed. Do you want to try anyway? I'm going to suggest that you set up your wireless manually, then you know what you've done, and you have more control.

You need to know your SSID (wireless network name) and your WPA PSK (pre-shared key), then put them into a configuration file:
```
sudo nano /etc/wpa_supplicant.conf
```
Is this file empty, or is there something already there? If there is already an entry, you can leave it there, you just need to edit (or create) the one for the network you want to connect to today. So you need the following information in the file, remember to replace 'your-SSID' with the name of your wireless network, and 'your-PSK' with your actual pre-shared key:
```
network={
        ssid="your-SSID"
        scan_ssid=1
        key_mgmt=WPA-PSK
        psk="your-PSK"
}
```
Hit Ctrl-O to save the file, then Ctrl-X to exit nano.
Then, try to associate the device with the network:
```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i ra0 -D wext
```Is the output positive or negative - does it seem happy? If it doesn't work try changing the -D option to '-D rt2500', or leaving the -D option out completely.

So this command tells wpa_supplicant, which is a program to connect to WPA networks, to use the config file that you just created (-c parameter), to connect the interface (-i) ra0, using the wext driver (-D). I'm uncertain about this driver part, I'm not sure whether this should be rt2500 or not. See if it works first.

If it does work, write the rest of this down, you're now going to try to use your connection, but this involves disconnecting your wired connection.

Pull out the ethernet cable on your wired connection.
Turn off the wired connection.
```
sudo ifconfig eth0 down
```
Bring up the wireless
```
sudo ifconfig ra0 up
```

Please let me know the results of all othe above.

If this worked the next step is to make it permanent, and to make sure you can use different wireless networks. You haven't made any permanent changes yet (except for editing/creating the wpa_supplicant.conf file), so when you restart everything will be as it was before.

---

### Post by k1001001 on 2006-12-23
I think the reason ndiswrapper is loaded to something associated with USB is because I followed [this]("http://www.ubuntuforums.org/showthread.php?t=241565") tutorial in an attempt to set up a Linksys USB wireless receiver. Then I also tried to change the configuration for my integrated wireless card. Neither worked.

I changed the /etc/wpa_supplicant.conf file, then ran the wpa_supplicant command. It came back saying "Operation not supported." a lot. This was the output:
```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i ra0 -D wext

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWENCODEEXT]: Operation not supported
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - CTRL-EVENT-TERMINATING - signal 2 received
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x0 - Failed to disable WPA in the driver.
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 -
```

Then I tried changing wext to rt2500 as you suggested, but this didn't seem to work at all.
```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i ra0 -D rt2500

Unsupported driver 'rt2500'.
```

With no -D option:
```
sudo wpa_supplicant -c /etc/wpa_supplicant.conf -i ra0

ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to set encryption.
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Failed to initiate AP scan.
```

As far as commenting out everything except "lo", I'm not quite sure what you are asking. "lo" is the local loopback, or what gives the IP address of 127.0.0.1.

---

### Post by k1001001 on 2006-12-23
Sorry for double post, but I got it going! I re-read the tutorial for Rt2500 cards [here]("http://www.ubuntuforums.org/showthread.php?t=241565"). User lkh gave me what worked in post #6. After rebooting and unplugging my ethernet cord, it worked. The only downside I see now is connecting to other networks. I guess I will have to reconfigure the RT2500STA.dat file every time I need to connect to another network. Who knows if this will work for unsecured networks either.

Thanks a lot for your help though, bernied. You were very helpful and explained each step very well. Maybe someone else with a messed-up wireless connection will be able to use this thread to get their wireless going.

---

### Post by bernied on 2006-12-23
Hooray! Glad you got it going. And also glad you didn't give up.

---

### Post by k1001001 on 2007-01-16
Hi all. Getting WPA wireless to work on this computer was a pain, so much so that I've killed every other type of wireless networking available, including unsecured networks. Oh the irony.

I got WPA to work by doing post #6 at [this]("http://www.ubuntuforums.org/showthread.php?t=241565") thread. I've tried every other possible method, and this is the only way I could get my computer to connect wirelessly to a WPA-secured network, which is what I use at home and my apartment at college. However, I can't connect to my school's wireless network now. Network Manager is useless, so I can't use this method. It looks like the only way I can connect to any wireless network is through editing the /etc/Wireless/RTA2500/RTA2500STA.dat file. Here's how it looks now:
```
# Copy this file to /etc/Wireless/RT2500STA/RT2500STA.dat
# This file is a binary file and will be read on loading rt2500.o module.
# Use "vi -b RT2500STA.dat" to modify settings according to your need.


#CountryRegion=0
#WirelessMode=0
#TXBurst=0
#TurboRate=0
#BGProtection=0
#ShortSlot=0
#TxRate=0
#PSMode=CAM

##(Old dorm network)
#SSID=WF
#NetworkType=Infra
#Channel=0
#AuthMode=WPAPSK
#EncrypType=TKIP
#DefaultKeyID=1
#Key1Type=0
#Key1Str=
#Key2Type=0
#Key2Str=
#Key3Type=0
#Key3Str=
#Key4Type=0
#Key4Str=
#WPAPSK=key
#RTSThreshold=2312
#FragThreshold=2312
#PSMode=CAM
#RFMON=0

##(This is my apartment network)
[Default]
ProfileID=myProfile
SSID=interweb
NetworkType=Infra
PreambleType=Auto
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=key

##(This is my home network)
#ProfileID=myProfile
#SSID=Goodwin
#NetworkType=Infra
#PreambleType=Auto
#AuthMode=WPAPSK
#EncrypType=TKIP
#WPAPSK=key
```
Any ideas as to how I could get this set-up to work with an unsecured network?

---

### Post by k1001001 on 2007-01-17
bump

---

### Post by k1001001 on 2007-01-17
Hi all. Getting WPA wireless to work on this computer was a pain, so much so that I've killed every other type of wireless networking available, including unsecured networks. Oh the irony.

I got WPA to work by doing post #6 at [this]("http://www.ubuntuforums.org/showthread.php?t=241565") thread. I've tried every other possible method, and this is the only way I could get my computer to connect wirelessly to a WPA-secured network, which is what I use at home and my apartment at college. However, I can't connect to my school's wireless network now. Network Manager is useless, so I can't use this method. It looks like the only way I can connect to any wireless network is through editing the /etc/Wireless/RTA2500/RTA2500STA.dat file. Here's how it looks now:
```
# Copy this file to /etc/Wireless/RT2500STA/RT2500STA.dat
# This file is a binary file and will be read on loading rt2500.o module.
# Use "vi -b RT2500STA.dat" to modify settings according to your need.


#CountryRegion=0
#WirelessMode=0
#TXBurst=0
#TurboRate=0
#BGProtection=0
#ShortSlot=0
#TxRate=0
#PSMode=CAM

##(Old dorm network)
#SSID=WF
#NetworkType=Infra
#Channel=0
#AuthMode=WPAPSK
#EncrypType=TKIP
#DefaultKeyID=1
#Key1Type=0
#Key1Str=
#Key2Type=0
#Key2Str=
#Key3Type=0
#Key3Str=
#Key4Type=0
#Key4Str=
#WPAPSK=key
#RTSThreshold=2312
#FragThreshold=2312
#PSMode=CAM
#RFMON=0

##(This is my apartment network)
[Default]
ProfileID=myProfile
SSID=interweb
NetworkType=Infra
PreambleType=Auto
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=key

##(This is my home network)
#ProfileID=myProfile
#SSID=Goodwin
#NetworkType=Infra
#PreambleType=Auto
#AuthMode=WPAPSK
#EncrypType=TKIP
#WPAPSK=key
```
Any ideas as to how I could get this set-up to work with an unsecured network?

---

### Post by CCBalla10 on 2007-01-17
have you tried Wifi-radar?  Applications>Add/Remove>Wifi-radar...lets you customize profiles for each network!

---

### Post by aysiu on 2007-01-17
I've merged all your wireless threads together so that people who are trying to help you can go to one place.

---

