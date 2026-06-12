---
title: "Wifi Help!!"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by chonzy on 2006-06-29
I have an Inspiron 1300 Laptop, running with Ubuntu 6.0.6, and i seem to be having problems with the Wireless conection, I got the actual and lastests Drivers from Dell, and I installed the driver with net ndisgtk, with the command " sudo ndiswrapper -i driver.inf", and now it apears listed on "windows wireless driver" in the System//Admin menu. But here is the problem, when i try to activate the device from Sistem//Admin//Networking, it apears to be activating, i mean the computer takes some time, but the light form the wireless card stays off, and then, when I open that dialog again, it apears as if was deactivated, like nothing ever happened...

I hope someone can help me out!!!

Cuz If i cant fix this I'll probably have to go back to :confused: M$!!

---

### Post by simone.brunozzi on 2006-06-29
Hi there,
if you google something like "inspiron 1300 ubuntu wifi" or similar, you'll get some interesting results... try those first.

Otherwise, I'm not fond of driver install, I'm not really able to help! :-)

Cheers,

---

### Post by chonzy on 2006-06-29
[QUOTE=simone.brunozzi]Hi there,
if you google something like "inspiron 1300 ubuntu wifi" or similar, you'll get some interesting results... try those first.

Otherwise, I'm not fond of driver install, I'm not really able to help! :-)

Cheers,[/QUOTE]
Already tried that, the firstt thing i did... thx anyways.

---

### Post by Jagot on 2006-06-29
I have the exact same laptop.  Some people seem to have got it working with the built-in Broadcom drivers with Dapper, but I always do it through ndiswrapper.

For some reason the Dell supplied drivers - both the one that came with the laptop itself and updated ones fro mthe support site - never worked for me - I ended up using the version of the driver from Acer's web site.

Here's what I do to get it working (this assumes you've placed the driver in a folder on the desktop):

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

That installs the driver itself.  However, we now need to blacklist the Broadcom drivers that come with Dapper otherwise they'll try and take over and it won't work:

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

You'll then need to activate in network settings and fill in any information required.  Then remember to change the default device in the network manager in the top right corner otherwise it'll appear as if its not working - by default it monitors the ethernet connection, so change to wlan0 or whatever it is.

---

### Post by chonzy on 2006-06-29
Thx for the hand Jagot, but I'm Afraid is not working either...:sad: The Wifi Antena's light won't even turn on... But now at least when i activate the wlan, it stays that way, and Wifi radar, a package i donwloaded for finding Wireless network is always telling me that it can find any networks nor IP Adress when I try to configure it manually.... I Downloaded the driver from this website, is the same as the one you (Jagot) mentioned i think 

[http://pryds.eu/ubuntu/80211g.zip](http://pryds.eu/ubuntu/80211g.zip)

I Hope someone can help me out, thx to everyone who tries =D>

---

### Post by chonzy on 2006-06-29
I read in another thread that I should post this

0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I got it from inputing in the terminal "lspci".

Then I inputed sudo ndiswrapper -l and it said that the hardware an driver were both present.

---

### Post by chonzy on 2006-06-29
***bump***

---

### Post by Slicedbread on 2006-06-29
do 'sudo gedit /etc/modprobe.d/ndiswrapper' and change wlan0 to eth1, save an then reboot.

---

### Post by x64Jimbo on 2006-06-29
the wireless led won't come on in linux unless you write a driver for it. i haven't seen my wifi led on in months. don't worry about that - it's not tied into the card. it will work without lighting up.

---

### Post by chonzy on 2006-06-29
Thx for the head up with the Antena's Light thing, well, i tried doing what Slicedbread told me to do, and nothing, after the restart, the only thing that had changed was that the wlan0 was no longer wlan0 but eth1... no further changes. I Cant even get to scan for available networks, so is quite possible that the wireless card is still unrecognized....

Keep up the help and lets hope i get to a solution :roll:

---

### Post by stupidkid on 2006-06-29
Please post your lsmod. ndiswrapper is probably conflicting with the native Linux drivers.

---

### Post by chonzy on 2006-06-29
here is the "lsmod"
> 
Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
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
ipv6                  265728  6
ndiswrapper           177364  0
af_packet              22920  25
dm_mod                 58936  1
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
b44                    25740  0
mii                     5888  1 b44
joydev                 10048  0
tsdev                   8000  0
serio_raw               7300  0
pcspkr                  2180  0
snd_hda_intel          18964  1
snd_hda_codec         142768  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
psmouse                36100  0
rtc                    13492  0
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  4 ndiswrapper,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
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

---

### Post by chonzy on 2006-06-29
**bump**

---

### Post by stupidkid on 2006-06-29
Hmm ok please post ifconfig -a and iwconfig.

And also to see if you can scan for networks run iwlist eth1 scan or iwlist wlan0 scan or w/e your interface name is.

---

### Post by chonzy on 2006-06-29
here is the ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:14:22:98:60:01
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe98:6001/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30491944 (29.0 MiB)  TX bytes:6703816 (6.3 MiB)
          Interrupt:217

eth1      Link encap:Ethernet  HWaddr 00:14:A5:5A:B2:07
          inet6 addr: fe80::214:a5ff:fe5a:b207/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Memory:dfbfe000-dfc00000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1844 (1.8 KiB)  TX bytes:1844 (1.8 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Here is the iwconfig: 

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  Nickname:"chonzy"
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I tried doing the sudo iwlist eth1 scan and it says "No scan results"

---

### Post by MarkSheely on 2006-06-29
Most everyone with a BCM4318 card has had success using the method outlined here:

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

That also seems to be where most BCM4318 users are gathering to help each other out.  

Good luck, 
Mark

---

