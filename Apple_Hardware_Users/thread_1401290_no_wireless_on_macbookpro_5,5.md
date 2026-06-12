---
title: "no wireless on macbookpro 5,5"
date: 2010-02-07
forum: Apple Hardware Users
---

### Post by ichigo on 2010-02-07
Hi,

my wireless has stopped working about a week ago. I was using the proprietary drivers that were automatically installed by ubuntu. The card still shows up in lspci, but does not in the network manager. With "lshw -C network" I get the following output:
```
           *-network UNCLAIMED
                description: Network controller
                product: BCM4322 802.11a/b/g/n Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:d3200000-d3203fff

```
I've googled for it and found out that lshw labeling the device as "unclaimed" probably points to a driver problem. Since all guides I found for this card say, things work out of the box, I don't know what I shoud do?
Any ideas?

UPDATE: Problem SOLVED: Uninstalling linux-backports-modules... did the trick

---

### Post by linuxopjemac on 2010-02-08
i would just reinstall the proprietary driver [here]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by ichigo on 2010-02-08
Thx for the hint. I've tried to install it as the readme says but get stuck at point 4.:
```
inago@Naoshima:~/Desktop/broad$ sudo modprobe lib80211
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
inago@Naoshima:~/Desktop/broad$ sudo insmod wl.ko
insmod: error inserting 'wl.ko': -1 Unknown symbol in module

```
Don't know if it helps, but the output of the compile looked like:
```
 sudo make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: &#12487;&#12451;&#12524;&#12463;&#12488;&#12522; `/usr/src/linux-headers-2.6.31-19-generic-pae' &#12395;&#20837;&#12426;&#12414;&#12377;
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/inago/Desktop/broad/wl.o
see include/linux/module.h for more information
make[1]: &#12487;&#12451;&#12524;&#12463;&#12488;&#12522; `/usr/src/linux-headers-2.6.31-19-generic-pae' &#12363;&#12425;&#20986;&#12414;&#12377;

```

---

### Post by linuxopjemac on 2010-02-08
did you install the kernel source ?

---

### Post by ichigo on 2010-02-08
> **linuxopjemac said:**
> did you install the kernel source ?

I guess you mean the linux-headers-2.6.31-19-pae package. Yes, it is installed.

---

### Post by linuxopjemac on 2010-02-08
If you compile some modules against the kernel, you need to have the kernel source installed. Correct me if I'm wrong.

---

### Post by ichigo on 2010-02-08
There's a package linux-source, which is also installed. The discription however says:
```
If you are simply trying to build third-party modules for your kernel,
you do not want this package. Install the appropriate linux-headers
package instead.
```

---

### Post by wojox on 2010-02-08
I got mine working by installing:

```
sudo apt-get install bcmwl-kernel-source
```

Reboot and should work. ;)

---

### Post by ichigo on 2010-02-08
> **wojox said:**
> I got mine working by installing:

```
sudo apt-get install bcmwl-kernel-source
```

Reboot and should work. ;)

Didn't work :(

---

### Post by linuxopjemac on 2010-02-08
what do you get with:

```
sudo ifconfig
```

and

```
sudo iwconfig
```

maybe the network manager is corrupt, I have seen problems. wicd is the program I use to connect WPA protected networks

```
sudo apt-get install wicd
```

---

### Post by ichigo on 2010-02-08
I don't think it's just the network manager since it doesn't show up in ifconfig...
```
inago@Naoshima:~$ ifconfig
eth0      Link encap:&#12452;&#12540;&#12469;&#12493;&#12483;&#12488;  &#12495;&#12540;&#12489;&#12454;&#12455;&#12450;&#12450;&#12489;&#12524;&#12473; 00:25:4b:d4:79:82  
          inet&#12450;&#12489;&#12524;&#12473;:192.168.84.194  &#12502;&#12525;&#12540;&#12489;&#12461;&#12515;&#12473;&#12488;:192.168.84.255  &#12510;&#12473;&#12463;:255.255.255.0
          inet6&#12450;&#12489;&#12524;&#12473;: fe80::225:4bff:fed4:7982/64 &#31684;&#22258;:&#12522;&#12531;&#12463;
          UP BROADCAST RUNNING MULTICAST  MTU:1500  &#12513;&#12488;&#12522;&#12483;&#12463;:1
          RX&#12497;&#12465;&#12483;&#12488;:4616 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12501;&#12524;&#12540;&#12512;:0
          TX&#12497;&#12465;&#12483;&#12488;:2961 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12461;&#12515;&#12522;&#12450;:0
          &#34909;&#31361;(Collisions):0 TX&#12461;&#12517;&#12540;&#38263;:1000 
          RX&#12496;&#12452;&#12488;:3253129 (3.2 MB)  TX&#12496;&#12452;&#12488;:487611 (487.6 KB)
          &#21106;&#12426;&#36796;&#12415;:27 &#12505;&#12540;&#12473;&#12450;&#12489;&#12524;&#12473;:0x2000 

lo        Link encap:&#12525;&#12540;&#12459;&#12523;&#12523;&#12540;&#12503;&#12496;&#12483;&#12463;  
          inet&#12450;&#12489;&#12524;&#12473;:127.0.0.1  &#12510;&#12473;&#12463;:255.0.0.0
          inet6&#12450;&#12489;&#12524;&#12473;: ::1/128 &#31684;&#22258;:&#12507;&#12473;&#12488;
          UP LOOPBACK RUNNING  MTU:16436  &#12513;&#12488;&#12522;&#12483;&#12463;:1
          RX&#12497;&#12465;&#12483;&#12488;:41 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12501;&#12524;&#12540;&#12512;:0
          TX&#12497;&#12465;&#12483;&#12488;:41 &#12456;&#12521;&#12540;:0 &#25613;&#22833;:0 &#12458;&#12540;&#12496;&#12521;&#12531;:0 &#12461;&#12515;&#12522;&#12450;:0
          &#34909;&#31361;(Collisions):0 TX&#12461;&#12517;&#12540;&#38263;:0 
          RX&#12496;&#12452;&#12488;:1437 (1.4 KB)  TX&#12496;&#12452;&#12488;:1437 (1.4 KB)

inago@Naoshima:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by linuxopjemac on 2010-02-08
so, you don't have an interface....

```
lspci -v ¦ grep broadcom
```

what about

```
sudo dmesg
```

does your machine report some problem with that card ?

---

### Post by linuxopjemac on 2010-02-08
can you give me the output of
```

sudo lsmod
```

maybe you just have to load the right module... 

```
sudo modprobe wl
```

interesting link
[http://djkaos.wordpress.com/2008/10/25/installing-broadcom-80211-linux-sta-driver/](http://djkaos.wordpress.com/2008/10/25/installing-broadcom-80211-linux-sta-driver/)

---

### Post by ichigo on 2010-02-08
there is an entry
```
03:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Apple Computer Inc. Device 008d
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at d3200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: ssb, wl

```
if I run lspci (have to write broadcom with a capital B to have it appear).
the output of dmesg is seems to be too long for my terminal. I couldn't find anything - neither by searching by hand nor by employing "dmesg | grep Broadcom".
lsmod returns:
```
Module                  Size  Used by
binfmt_misc             8356  1 
bridge                 47952  0 
ppdev                   6688  0 
stp                     2272  1 bridge
bnep                   12060  2 
snd_hda_codec_cirrus    11740  1 
snd_hda_intel          26624  5 
snd_hda_codec          78300  2 snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
hid_apple               6236  0 
snd_pcm_oss            37312  0 
snd_mixer_oss          16188  1 snd_pcm_oss
snd_pcm                75232  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
usbhid                 38304  0 
snd_seq_oss            29312  0 
applesmc               20936  0 
snd_seq_midi            6624  0 
led_class               4096  1 applesmc
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
input_polldev           3716  1 applesmc
snd_seq                51120  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               59112  0 
coretemp                5564  0 
iptable_filter          3100  0 
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    60932  23 snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               36736  1 uvcvideo
soundcore               7264  1 snd
nvidia               9857156  40 
v4l1_compat            14496  2 uvcvideo,videodev
ip_tables              11692  1 iptable_filter
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_nforce2             6880  0 
joydev                 10240  0 
shpchp                 32336  0 
bcm5974                 8892  0 
x_tables               16544  1 ip_tables
agpgart                35020  1 nvidia
btusb                  11856  2 
lp                      8964  0 
lib80211                6528  0 
parport                35340  2 ppdev,lp
nvidia_bl               7108  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usb_storage            52640  1 
forcedeth              54472  0 
ohci1394               30220  0 
ieee1394               86628  1 ohci1394

```

sudo modprobe wl returns
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting wl (/lib/modules/2.6.31-19-generic-pae/updates/dkms/wl.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and the last lines of dmesg then read:
```
[ 4846.025720] wl: disagrees about version of symbol lib80211_get_crypto_ops
[ 4846.025729] wl: Unknown symbol lib80211_get_crypto_ops

```

---

### Post by linuxopjemac on 2010-02-08
seems like a bug:
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/395630)

---

### Post by ichigo on 2010-02-08
oh, thanks for the hint. As suggested there uninstalling linux-backports-modules... helps and brings back wireless after a restart

---

### Post by linuxopjemac on 2010-02-08
change your  first post into [SOLVED]

---

### Post by ichigo on 2010-02-08
I've already marked the thread as solved...:popcorn:

I've also edited the first post and written what did the trick.

---

