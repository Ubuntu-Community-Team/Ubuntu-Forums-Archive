---
title: "ASUS USB-N13 Wireless Adapter"
date: 2013-01-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by tdshady on 2013-01-06
Hi, I'm very new to Ubuntu, with limited command knowledge.

I've bought a brand new PC without an operating system, and have just installed Ubuntu 12.04.

All I've done so far is plug in the ASUS usb-n13 - I haven't installed any drivers or anything at all. Without me doing anything, it has picked up the local wifis around. I select mine, it tries to connect, but can't.

I pretty much have this exact problem, except that I haven't had or tried with any previous versions of Ubuntu, and I haven't tried installing anything yet:
[http://ubuntuforums.org/showthread.php?t=2079949](http://ubuntuforums.org/showthread.php?t=2079949)

I imagine that if it can already see the wifi network, that I don't need to install a driver?

I think I have RTL8192cu, as this name is mentioned in some of the directories in the Linux directory on the installation disk. I read the readme.txt on the installation disk, but it gives no instruction using Network Manager (other than it should just work? And I'm not even sure if this is what I'm using) and I'm not sure if I'm supposed to use the command-line method or not, because it says not to use it with Network Manager (which I'm assuming is what is currently picking up the available wifi networks).

Here is my lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 0b05:17ab ASUSTek Computer, Inc.
Bus 002 Device 004: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth

Can someone please help me get this working! :confused:

---

### Post by Andrew F in Australia on 2013-01-07
Hi,

Here's the text of the installation how-to that comes with the adapter.

NOTE HOWEVER THAT THIS CRASHES ON MY SYSTEM AT THE FIRST HURDLE  (rt73.ko failed to build) 

 sudo make
[sudo] password for harold-music: 
Sorry, try again.
[sudo] password for harold-music: 
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-21-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-21-generic'
rt73.ko failed to build!
make: *** [module] Error 1


```
 Installation instructions for the Legacy rt73 module
[http://rt2x00.serialmonkey.com]


==================
Build Instructions
==================

    1. Unpack the driver sources and go to the Module directory:
          $ tar -xvzf rt73-cvs-daily.tar.gz
          $ cd ./rt73-cvs-YYYYMMDDHH/Module

    2. Compile the driver sources:
          $ make

    3. Install the driver (as root):
          # make install


====================
INVOCATION
====================
Load the driver:

    $ modprobe rt73 [ifname=<name>] [debug=<mask>] [firmName=<file>]

    <name> is the name of the device and defaults to "wlan%d". If more
    than one adapter is installed, successive devices will be named
    wlan0, wlan1, etc. If you wish to use a different scheme - say
    eth*, and there are already wired ethernet devices named eth0 and
    eth1, then specifying <name> as "eth%d" gives the adapter the name
    "eth2".

    <mask> is a decimal or hex number. See TESTING file. Ignored if
    driver compiled without debug support.

    <file> is the name of a firmware file and defaults to "rt73.bin"
    if omitted. Only the basename - not the full path - may be
    specified.

Start it up:

    $ ifup wlan0        # If using Debian - or
    $ ifconfig wlan0 up
    $ iwlist wlan0 scan

If everything is ok, you should see a list of surrounding Access
Points. It means you can jump to the configuration section. Otherwise,
check out the following install notes...

_________
NOTES:

* Firmware file (rt73.bin)

    The rt73 chipset uses a firmware file which is loaded in device
    memory using the kernel firmware_class facility. 'make install'
    copy the firmware file to the standard firmwares location:
    /lib/firmware.

    However some linux distributions divert from the standard and e.g.
    use /lib/firmware/<KERNEL_VERSION>. If this is your case, you will
    have to manually move the firmware file to the right location.
    If you have problems with firmware loading, please ask on your
    distro's support media (forum, etc).

* Driver alias

    rt73 uses wlan* as its modprobe alias. This means you can have
    several devices and they will be named wlan0, wlan1, etc.

    If for some reason you want this interface number 'static' (e.g.
    if you have several wlan devices and their numbers change on
    reboot) you can change the rt73 alias in /etc/modprobe.d/ralink
    (2.6 kernels) or /etc/modules.conf (2.4 kernels) back to wlan0 (or
    wlan1, etc).

    However the proper way to achieve this purpose is to use a udev
    rule based on the wlan MAC address, for example:
    KERNEL=="wlan*", SYSFS{address}=="00:de:ad:be:ef:00", NAME="wlan0"
    (See:
     http://www.reactivated.net/writing_udev_rules.html#example-netif)

* Module parameters

    You can load the rt73 module with two optional parameters:
       firmName=<FILE_NAME>  Use another firmware file.
       debug=<DEBUG_MASK>    Set debug verbosity (see below).


==============================
Wireless Station Configuration
==============================

The wlan interface should be configured using standard wireless
extension tools.

GUI CONFIG:

    If you're looking for a GUI config tool we provide RutilT on our
    download page
    [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads].

MANUAL CONFIG:

    1. Set the interface mode and bring it up
          # iwconfig wlan0 mode managed
          # ifconfig wlan0 up

    2. Set your target network / Access Point
       If you just want to join a wireless network, set its ESSID:
          # iwconfig wlan0 essid <ESSID>
       If you want to associate with a specific AP, set its MAC
       address:
          # iwconfig wlan0 ap <BSSID>

    3. Set encryption if needed

       a) WEP (802.11b)
          Choose the authentication mode (open/restricted):
             # iwconfig wlan0 key open
          Or:
             # iwconfig wlan0 key restricted
          Set the encryption key:
             # iwconfig wlan0 key <KEY>

       b) WPA (802.11g)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPAPSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=TKIP

       c) WPA2 (802.11i)
          Set the authentication mode:
             # iwpriv wlan0 set AuthMode=WPA2PSK
          Set the encryption key:
             # iwpriv wlan0 set WPAPSK=<KEY>
          Set the encryption type:
             # iwpriv wlan0 set EncrypType=AES

    4. Check that you're associated with an AP
          # iwconfig wlan0

If everything's ok, you can now configure the wlan0 interface
statically or dynamically (DHCP). If you need more wireless config
details and examples (Adhoc mode e.g.), see iwpriv_usage.txt (included
in driver sources). Otherwise, read the following config notes...

_________
NOTES:

* Auto-load on boot

    If you want your device to come up on boot the best is to use your
    specific linux distribution's tools (boot scripts, etc).
    If you need support doing so, ask on your distro's support media.

* wpa_supplicant

    wpa_supplicant is a userland WPA/WPA2/802.1X layer. This driver is
    not compatible with it. As most wpa_supplicant features are
    embedded into our driver, you should not need it though.
    If you need to use a feature that only wpa_supplicant provides:
       - either use our next-generation rt2x00 driver which
         is compatible with wpa_supplicant
       - or patch wpa_supplicant to make it work with rt73 (more info:
         http://mjh.name/Ralink_rt73_wpa_supplicant_rt2x00_wpa2)


==================
Misc. information
==================

* hostapd

    hostapd allows your wlan device to act like an Access Point. Legacy
    drivers are _not_ compatible with it, but our next-generation
    rt2x00 drivers are.

* Network auditing

    Our drivers allow you to peform in-depth wireless network auditing.
    Most of the following settings require that you bring the
    interface down beforehand.

    You can set a custom MAC address as you would do for any other
    ethernet interface:
       # ifconfig wlan0 hw ether <MAC_ADDRESS>

    You can put your wlan interface in promiscuous mode as you would
    do for any other interface:
       # ifconfig wlan0 promisc

    You can put your interface in monitor mode and have it listen to all
    802.11 frames around:
       # iwconfig wlan0 mode monitor

    You can also inject 802.11 frames on the fly. To enable injection,
    run:
       # iwpriv wlan0 rfmontx 1

* Testing / debugging

    If you experience any driver related problem you can ask for
    support on our mailing list or our legacy driver forum.
    Before asking for help, read the TESTING file and follow its
    advice. Do *not* post messages like: "wlan does not work. please
    help!".

```

It may be a similar fix for both.  I'll post separately.

Cheers,

AF

---

### Post by Us3r Unfriendly on 2013-01-07
I had this issue for the longest time too.  I was didledaddling with modprobe -r and removed the module that Ubuntu was using for my wifi card.  Then I retried to compiled the source and it worked.

Can you post the output of:

lsmod

sudo lshw -c network

...while the wifi card is plugged in.  Then we can blacklist the original module and compile the one that came with the card and then we'll edit your /etc/modules and place the new module in there so you can boot up with it on all the time :D

---

### Post by Us3r Unfriendly on 2013-01-07
Oh and to be exact, is this the card your using:
[http://www.asus.com/Networks/Wireless_Adapters/USBN13/](http://www.asus.com/Networks/Wireless_Adapters/USBN13/)

---

### Post by tdshady on 2013-01-10
Thanks so much for your reply!!

Andrew F in Australia: I don't think that's the same one as mine, I have rtl8192_8188cu, not rt73. Also, I did try to follow the steps that came with the installation disk:

/ASUS USB-N13/Linux/RTL8192CU_linux_v3.0.2164.20110715/RTL8192CU_8188CUS_8188CE-VAU_linux_v3.0.2164.20110715/driver/USB-N13 Linux Driver Quick Start.txt

but it says "Before installing driver, please check installed compile, make tool and kernel source code. Otherwise, you need to connect to Internet and use yum to install."

Firstly, I don't know where to check the source code, or what I would be checking. Secondly, if I could connect to the internet, then I wouldn't have a problem ;-)

I tried to follow the instructions below that message anyway, was able to do step 1 (untar the files), but step 2 (make) gives "make: *** No targets specified and no makefile found. Stop."


Us3r Unfriendly: That is EXACTLY the card I'm using. ASUS USB-N13  802.11b/g/n.

Here is the output of lsmod:
```

Module                  Size  Used by
nls_utf8               12493  1
isofs                  39553  1
bnep                   17830  2
rfcomm                 38139  0
bluetooth             158438  10 bnep,rfcomm
snd_hda_codec_hdmi     31775  1
snd_hda_codec_realtek   174055  1
arc4                   12473  2
eeepc_wmi              12949  0
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
ppdev                  12849  0
snd_hda_intel          32765  3
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17393  0
rtl8192cu              97722  0
rtl8192c_common        69519  1 rtl8192cu
snd_seq_midi           13132  0
rtlwifi                95804  1 rtl8192cu
parport_pc             32114  1
mac80211              436455  3 rtl8192cu,rtl8192c_common,rtlwifi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178679  2 rtlwifi,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 asus_wmi
mac_hid                13077  0
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                72846  0
serio_raw              13027  0
i915                  414603  3
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mei                    36570  0
lp                     17455  0
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0
hid                    77367  1 usbhid
r8169                  56321  0

```

And here is the output of sudo lshw -c network:
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 09
       serial: c8:60:00:ca:8a:e0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1.7
       logical name: wlan0
       serial: c8:60:00:d4:64:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.2.0-23-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn

```


All while the card is plugged in. Thanks so much for your advice!

---

### Post by Carolina Parakeet on 2013-01-13
I have a Asus USB-N13 B1 on 12.10.  I followed [these instructions]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/") and it has been stable for about a day so far.

---

### Post by tdshady on 2013-01-14
Thanks!!! I am away for a few days, but will try this when I get home and let you know how it goes. Cheers

---

### Post by tdshady on 2013-01-28
Oh god.

So I attempted to follow the instructions you linked to ([here]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/")), starting at Step 4 because I already had the drivers on the installation disk that came with the dongle.

It looked like it was doing things, but then I got an error message in the terminal. I wasn't able to copy/paste the error message here :-( but I continued on to Step 5 anyway, and then Step 6. Perhaps unsurprisingly (since I got an error on Step 4), things are now worse. Now Ubuntu doesn't even acknowledge that I've plugged in the dongle, let alone see any of the wireless networks :-(

---

### Post by tdshady on 2013-02-16
OK I finally got this to work!

1. I downloaded the latest driver for RTL8192CU from the RealTek website: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772)

2. I untarred the file, then went to the 'driver' directory

3. Command: make (this creates a file called '8192cu.ko')

4. I then blacklisted the dongle using Command: sudo gedit /etc/modprobe.d/blacklist.conf where I went to the end of the file and added the line: blacklist rtl8192cu

5. Back to the 'driver' directory, and typed command: ./clean

6. Back to the blacklist document, and removed the line that was added to the end of the document (blacklist rtl8192cu)

7. Back to the 'driver' directory, and typed command: insmod 8192cu.ko


And now it works!! :-D

---

### Post by chili555 on 2013-03-02
@tdshady--

I understand you are still having some difficulties. What Ubuntu version are you running?```
lsb_release -d
```What module is loaded now?```
lsmod | grep 8192
```Please confirm your device details:```
lsusb
```I see a flaw or two in your procedure; we'll try to tweak it a bit.

---

### Post by tdshady on 2013-03-02
Thanks chili555!!! Yes, seems I got excited too quickly... I only got it working for a few minutes, then it drops out again and the same problem persists :-(

Here is the output of:

lsb_release -d
```
Description:	Ubuntu 12.04.2 LTS

```
lsmod | grep 8192
```
rtl8192cu              72761  0 
rtl8192c_common        49512  1 rtl8192cu
rtlwifi                76086  1 rtl8192cu
mac80211              555198  3 rtl8192cu,rtl8192c_common,rtlwifi

```
lsusb
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bb4:0fb4 High Tech Computer Corp. 
Bus 001 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth

```

Thank you so much for your assistance!!!!!

---

### Post by chili555 on 2013-03-02
Your process above is seriously flawed; however, there is an easier way to install an updated driver. Please get a temporary wired ethernet connection and do:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```Reboot and let us have your report.

---

### Post by tdshady on 2013-03-03
Ok, I did that, here is what happened:

```
tiff:~$ sudo apt-get install linux-backports-modules-cw-3.6-precise-generic[sudo] password for tiff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-backports-modules-cw-3.6-3.2.0-38-generic linux-image-3.2.0-38-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-backports-modules-cw-3.6-3.2.0-38-generic
  linux-backports-modules-cw-3.6-precise-generic linux-image-3.2.0-38-generic
0 upgraded, 3 newly installed, 0 to remove and 61 not upgraded.
Need to get 41.4 MB of archives.
After this operation, 160 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://au.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-38-generic amd64 3.2.0-38.61 [38.5 MB]
Get:2 http://au.archive.ubuntu.com/ubuntu/ precise-updates/main linux-backports-modules-cw-3.6-3.2.0-38-generic amd64 3.2.0-38.25 [2,892 kB]
Get:3 http://au.archive.ubuntu.com/ubuntu/ precise-updates/main linux-backports-modules-cw-3.6-precise-generic amd64 3.2.0.38.46 [2,674 B]
Fetched 41.4 MB in 1min 17s (534 kB/s)                                         
Selecting previously unselected package linux-image-3.2.0-38-generic.
(Reading database ... 141342 files and directories currently installed.)
Unpacking linux-image-3.2.0-38-generic (from .../linux-image-3.2.0-38-generic_3.2.0-38.61_amd64.deb) ...
Done.
Selecting previously unselected package linux-backports-modules-cw-3.6-3.2.0-38-generic.
Unpacking linux-backports-modules-cw-3.6-3.2.0-38-generic (from .../linux-backports-modules-cw-3.6-3.2.0-38-generic_3.2.0-38.25_amd64.deb) ...
Selecting previously unselected package linux-backports-modules-cw-3.6-precise-generic.
Unpacking linux-backports-modules-cw-3.6-precise-generic (from .../linux-backports-modules-cw-3.6-precise-generic_3.2.0.38.46_amd64.deb) ...
Setting up linux-image-3.2.0-38-generic (3.2.0-38.61) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-backports-modules-cw-3.6-3.2.0-38-generic (3.2.0-38.25) ...
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
Setting up linux-backports-modules-cw-3.6-precise-generic (3.2.0.38.46) ...

```

I then rebooted, but no cigar. The wifi is still trying to connect, then asking for the password. Upon startup, little window/notification popped up saying it was disconnected from the wifi network.

What to try next?

---

### Post by chili555 on 2013-03-03
Let's try a driver parameter:```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```Now will it connect and stay? If so, we'll need to write one quick file to make it persistent.

---

### Post by tdshady on 2013-03-04
Oh god. I now have an entirely new problem.

I did the two sudo modprobes, and straight away I could see that the connection was established, and appeared to be stable. I then opened my web browser, but couldn't load anything (i.e. internet not working). I decided to reboot. The time between typing the two commands and rebooting was only a few minutes, so I didn't really get to see any hard evidence that it would connect and stay, but it did appear that way (since it was dropping out much quicker than that beforehand).

Unfortunately now Ubuntu is booting into terminal mode, and I can't get the GUI back up :-( I have tried "startx", but this just brings up the standard Ubuntu desktop background and nothing else. I also tried going to /etc/init/rc-sysinit.conf, but when I open it in vi, the DEFAULT_RUNLEVEL is already =2, so I'm confused. That's the one that's supposed to load the GUI, right?

Ahhhhh :-(

---

### Post by tdshady on 2013-03-04
OK, I found a horrible, horrible work around. If I reboot many times in a row, it eventually boots with the GUI. Any better suggestions?

The wifi is connected, and the connection is stable. I've left it for some time now and it hasn't dropped out - so that's good.

However, my ability to actually use the internet (for web browsing) is not very stable. Whether pages load or not seems completely arbitrary. I am using the same wifi network on my Windows laptop right now as I write this, which is working fine, so it's not a network problem... just seems that the connection is working intermittently, although the connection is *not* dropping out and is stable.

Ok SCRAP THAT. Just disconnected!! Was probably only connected for ~15 minutes. Longest time so far, but still dropping out :-( now it's asking for my password... not this again...

I am scared to restart or shutdown now, in fear of losing my GUI again :-(

---

### Post by chili555 on 2013-03-04
After you rebooted, did you re-apply the driver parameter?```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```If it helps, we'll write a file to make it persistent.

As to your GUI issue, I am not very experienced in such things. You might get some assistance on General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) You might find some clues in here:```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by tdshady on 2013-03-04
No, I didn't re-apply the driver parameter.

Just started up again, and reapplied the driver parameter. Something weird is happening - it's connected, and the connection appears stable (for the last 20 minutes now!), but I can't actually browse the net. Pages aren't loading. Very weird.

Any ideas?

It's past 1am here now, off to bed and try again tomorrow :-(    ...the never ending battle!

---

### Post by chili555 on 2013-03-04
See you tomorrow.

---

### Post by tdshady on 2013-03-05
I'm still having the same issues. I am now doing

```
sudo modprobe -r rtl8192cu
sudo modprobe rtl8192cu swenc=1
```

everytime I boot up. It's now not even trying to connect, it's just disconnected. When I click to try and connect, it tries, but then it just says "disconnected".

I had emailed ASUS about it, and just got a reply back today:

[TABLE="width: 99%"]
[TR]
[TD][FONT=Verdana][I]Dear Valued Customer,
Thank you for contacting ASUS Technical Service.

Sorry for the inconvenience. First please reinstall driver for a try:
[http://support.asus.com.cn/download.aspx?SLanguage=en&p=11&m=USB-N13&hashedid=8qxR0Z80mE7HdVKx](http://support.asus.com.cn/download.aspx?SLanguage=en&p=11&m=USB-N13&hashedid=8qxR0Z80mE7HdVKx)

And may i confirm this product Wireless USB-N13 can work normal in another computer or not?
If convenient, please check it can work in others operating system.
Thank you for understanding! 
Thank you for your support Asus product. Wish you have a good day.

If you continue to experience issues in the future, please do not hesitate to contact us. 
Later you may receive a satisfaction questionnaire for this service. 
Trouble you again with this rating (1 is poor ; 10 is excellent ; 7 or greater than 7 means &#8220;satisfied&#8221;), in order to provide better service for you.
Best regards
Stephen
ASUS service center[/I]

[/FONT][/TD]
[/TR]
[/TABLE]
[FONT=Verdana]Should I try installing this driver he recommended? It's Linux Driver v.2.3.0.2 but was last updated in 2010. What's your opinion? Don't want to keep stuffing around with different things in case I'm making it worse [/FONT]:-(

____
Update: Ok, if I boot up and *don't* do the two modprobe commands, it says it's connected, and it doesn't seem to be dropping out. But just like last night, it's not *actually* connected to the internet - I cannot download or install things, and can't browse the web.

[IMG]http://cdn.chud.com/3/37/37ef4c5d_fry-argh.gif[/IMG]


____
Update 2: WOW! So after half an hour of refreshing Chromium every few minutes or so, it randomly actually loaded a page!!! Only one page though. Tried to navigate somewhere else, and no cigar again. So it IS connecting to the internet SOMETIMES. Barely, just barely. The connection has not, I repeat not (!), dropped out this entire time! Small wins here and there...

____
Update 3: Ok, so ~50 minutes in, and the wifi has disconnected itself. Asking for password over and over again now, trying to connect but not connecting (same old chestnut).

---

### Post by chili555 on 2013-03-05
> Should I try installing this driver he recommended? It's Linux Driver v.2.3.0.2 but was last updated in 2010. What's your opinion?Ladies and gentlemen, please put on your rant-resistant vests. There are two versions of the USB-N13. One is a Ralink rt200usb device and one is a Realtek rtl8192cu device. The kind person referred you to the wrong driver for the wrong device:> RT28xx_MODE = STA

TARGET = LINUX

[COLOR="#FF0000"]CHIPSET = 3070[/COLOR]

#OS ABL - YES or NO
OSABL = NO

ifneq ($(TARGET),THREADX)
#RT28xx_DIR = home directory of RT28xx source code
RT28xx_DIR = $(shell pwd)
endif

RTMP_SRC_DIR = $(RT28xx_DIR)/RT$(CHIPSET)
Even if that is the device you have, on any modern kernel, 'make' yields:> /home/chili/tdshady/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:341:3: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
/home/chili/tdshady/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:357:3: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
cc1: some warnings being treated as errors
make[2]: *** [/home/chili/tdshady/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/chili/tdshady/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-25-generic'
[COLOR="#FF0000"]make: *** [LINUX] Error 2[/COLOR]
So their reply was less than helpful.

End rant.

Let's turn our attention to your router. Please be sure it is set to WPA2 only and not mixed mode WPA and WPA2. Please see attached.

Next, if your router is capable of N speeds please try resetting the router to B and G only and not N. You might also try different channels; I have the best luck with channel 11.

Is your ability to connect and stay connected better, worse or the same?

---

### Post by tdshady on 2013-03-06
Haha well I'm glad I made the right decision in ignoring his advice then!! Nice.

I think you may be a genius, but so far we only have ~70% proof of this. My router was already set to WPA2 only, but I did change the channel to channel 11 as advised, and also decreased the speed from 'Up to 300 Mbps' to 'Up to 54 Mbps'. Please see attached screenshot.

Now, I got that screenshot from installing Gimp using my wifi connection :-) and I am also posting this using my wifi connection :-D

Here's the current situation (after changing the router settings as per your advice):

**1. **I booted up, and the wifi connection was immediately established. I opened web browser, no pages loading. Wifi DISCONNECTED after only a few minutes.
**2. **I Shut Down.
**3.** Now I started keeping a log:

22:44    Booted up
22:44    Connection established
22:47    Chromium page loads x 2 (on first attempt)
22:48    Chromium trying to load page...
22:50    Wifi DISCONNECTED
23:05    Wifi remaining disconnected (after entering password and clicking 'Connect' a few times)
23:05    Reboot.

**4.** Third boot up:

23:06    Booted up. Connection established
23:07    Chromium page loads x 4
23:09    Chromium trying to load page.... eventually loaded. More page loads x3+
23:12    Begin install of Gimp from Ubuntu Software Centre, ~40MB
23:18    DISCONNECTED. Download failed at 20MB of Gimp downloaded
23:20    In terminal: sudo modprobe -r rtl8192cu
23:20    In terminal: sudo modprobe rtl8192cu swenc=1
23:21    Connection established!!
23:21    Continue download of Gimp, now 26.1MB to go. Eventually downloaded, and installed!
23:38    DISCONNECTED.
23:38    In terminal: the two modprobe commands again
23:39    Connection established!
23:51    the time right now. Connection still established :-)
23:53    Scrap that. Web pages not loading. Connection still established though...
23:55    two modprobe commands again
23:55    Connection established, and pages loading


SO.............. this method seems ok, but not very desirable. Thoughts?

---

### Post by chili555 on 2013-03-06
I am as close to uttering an impure word as I have been since I last looked at my Visa bill. I have several thoughts.

  #I wonder if this is a 64-bit issue. I'd be very interested to burn a 32-bit live CD and see if the behavior is the same, better or worse.

  #Here is a long thread that ended when the poster gave up on the native Linux driver and loaded ndiswrapper; the result was:> HAIL TO THE CONQUERING HERO! Chili you are the man!! Wifi is working like a charm now. ^^^I love the sound of that! Please see posts 46 and following. [http://ubuntuforums.org/showthread.php?t=2036445&page=5&highlight=rtl8192cu+ndiswrapper](http://ubuntuforums.org/showthread.php?t=2036445&page=5&highlight=rtl8192cu+ndiswrapper)

  #I'd consider investing $10-15 in a known working USB device.

Please let me know how you'd like to proceed; I'll be very happy to assist.

---

### Post by tdshady on 2013-03-09
Ah, well we can rule out the 64-bit issue as a possibility, because I had originally been trying on 32-bit, with exactly the same problem. I actually uninstalled 32-bit and installed 64-bit because I thought it might help (which as we both know, it didn't).

Thanks for all your assistance with this. I agree with the last thing you said - I am going to grab myself a hammer and go to town on this ASUS N-13 wifi usb. Then I'm going to go buy the longest ethernet cable I can find, and use that to connect to the internet FTW. :P

Thanks for everything chili555 I do really appreciate it!!!! :KS

---

