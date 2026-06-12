---
title: "[SOLVED] Blekin F5D7050"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by travismoore on 2008-02-09
Need help with this here is result of lsusb:
```
travis@Travis:~$ lsusb
Bus 004 Device 002: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

I tried this guide but it worked for like 10 minutes then stopped..

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)


Any help is appreciated.

cheers,

Travis

---

### Post by travismoore on 2008-02-09
please? [-o<

---

### Post by travismoore on 2008-02-09
bump

---

### Post by travismoore on 2008-02-09
Please help me

---

### Post by justsomedude on 2008-02-09
Hey there,

sorry to hear it didn't work out for you. Network Manager on Gutsy doesn't seem to play well with RaLink chips, good news is we already installed the driver.

You could try to use WICD instead of Network Manager, or maybe Wireless Assistant. Wireless Assistant is a KDE programm, but it will work fine on Gnome.


Could you post the output of 

```
lshw
```

and

```
lsmod
```

and also

```
iwconfig
```

?

---

### Post by travismoore on 2008-02-09
lshw:
```
travis@Travis:~$ lshw
WARNING: you should run this program as super-user.
travis                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 639MB
     *-cpu
          product: AMD Athlon(tm) 64 Processor 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 15.12.2
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm ts fid vid ttp tm stc cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-pci:0
          description: Host bridge
          product: 761/M761 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-pci:0
             description: PCI bridge
             product: SG86C202
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
                vendor: Silicon Integrated Systems [SiS]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: vga cap_list
                configuration: latency=0
        *-isa
             description: ISA bridge
             product: SiS965 [MuTIOL Media IO]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 48
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 5513 [IDE]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.5
             bus info: pci@0000:00:02.5
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_sis latency=128 module=pata_sis
        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=64 maxlatency=11 mingnt=52 module=snd_intel8x0
        *-usb:0
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:1
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.1
             bus info: pci@0000:00:03.1
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:2
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.2
             bus info: pci@0000:00:03.2
             version: 0f
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80 module=ohci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 3.3
             bus info: pci@0000:00:03.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=80 module=ehci_hcd
        *-network
             description: Ethernet interface
             product: 190 Gigabit Ethernet Adapter
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 00
             serial: 00:1b:b9:a5:8f:64
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.2.6 latency=0 module=sis190 multicast=yes
        *-pci:1
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-ide:1
             description: IDE interface
             product: Silicon Integrated Systems [SiS]
             vendor: Silicon Integrated Systems [SiS]
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_sis latency=64 module=sata_sis
        *-pci:3
             description: PCI bridge
             product: PCI-to-PCI bridge
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:6a:ca:3f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

lsmod
```
travis@Travis:~$ lsmod
Module                  Size  Used by
binfmt_misc            12936  1 
ipv6                  273892  8 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
powernow_k8            16960  0 
cpufreq_stats           7232  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  1 
freq_table              5792  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
dock                   10656  0 
button                  8976  0 
container               5504  0 
video                  18060  0 
sbs                    19592  0 
ac                      6148  0 
battery                11012  0 
lp                     12580  0 
p54usb                 16256  0 
p54common              13312  1 p54usb
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
rt73usb                25344  0 
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
rt2x00usb              12032  1 rt73usb
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
rt2x00lib              19584  2 rt73usb,rt2x00usb
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
rfkill                  8208  1 rt2x00lib
snd_seq_midi            9600  0 
mac80211              171016  5 p54usb,p54common,rc80211_simple,rt2x00usb,rt2x00lib
cfg80211                7304  1 mac80211
snd_rawmidi            25728  1 snd_seq_midi
input_polldev           5896  1 rt2x00lib
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
serio_raw               8068  0 
k8temp                  6656  0 
pcspkr                  4224  0 
psmouse                39952  0 
sis190                 22276  0 
crc_itu_t               3072  1 rt2x00lib
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mii                     6528  1 sis190
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  7 
sata_sis                9988  2 
ata_generic             8452  0 
floppy                 60004  0 
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  6 p54usb,rt73usb,rt2x00usb,ehci_hcd,ohci_hcd
pata_sis               15236  4 sata_sis
libata                125168  3 sata_sis,ata_generic,pata_sis
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
thermal                14344  0 
processor              32072  2 powernow_k8,thermal
fan                     5764  0 
fuse                   47124  5 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

iwconfig:
```
travis@Travis:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

travis@Travis:~$ 

```

---

### Post by justsomedude on 2008-02-09
Okay, the driver seems to load fine but you are not connected, wanna try WICD?

---

### Post by travismoore on 2008-02-09
K sure is that in the repositories?

---

### Post by justsomedude on 2008-02-09
No. But I wrote a short walkthrough:


Go to

System --> Administration --> Synaptic Package Manager

then

Settings --> Repositories

and select the tab "Third Party Software". Click "Add..." and add:

```
deb http://apt.wicd.net gutsy extras
```

Close the two windows and hit the Reload button in the Synaptic main Window.


Then, do a search for the following two packages:

-wicd
-wpasupplicant

Mark them for installation and hit "Apply". This will install WICD (and automatically uninstall Network Manager).


Make a backup copy of /etc/network/interfaces:

```
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```


Then, open /etc/network/interfaces:

```
sudo gedit /etc/network/interfaces
```

Edit: Warning! This will probably break your connection with the cable!

You can always restore the file by doing this:

```
sudo cp /etc/network/interfaces.backup /etc/network/interfaces
```


Uncomment (meaning add the "#" character at the beginning of each line) everything except for the section for **lo**, should look something like this then:

```
auto lo
iface lo inet loopback

# iface eth1 inet dhcp
# iface eth2 inet dhcp
# iface ath0 inet dhcp
# iface wlan0 inet dhcp
```

Now you can open WICD (should be under Applications --> Internet) and configure your Network.

Go to Preferences and add wlan0 to "wireless Interface" and hit OK. Then, you should be able to configure your connection in the main window.


You can find the WICD faq here:

[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

---

### Post by justsomedude on 2008-02-09
Forgot something:

After you edit your /etc/network/interfaces, do:
```

sudo /etc/init.d/networking restart
```


As I wrote above, this may break your cable connection. Maybe editing the /etc/network/interfaces isn't necessary at all. Remember you can always restore the file by doing

```
sudo cp /etc/network/interfaces.backup /etc/network/interfaces
```

and then

```

sudo /etc/init.d/networking restart
```

---

### Post by travismoore on 2008-02-09
Its working but i seem to be having some problems.

It is not running how it should do its ranging between sluggish and ridiculously slow.

---

### Post by travismoore on 2008-02-09
Maybe its the driver setting, I don't know how to set it as.

---

### Post by travismoore on 2008-02-09
help?

---

### Post by travismoore on 2008-02-10
15 hours .. bump

---

### Post by justsomedude on 2008-02-10
Hmm, did you blacklist the existing drivers in /etc/modprobe.d/blacklist like the guide you used suggested properly? There may be conflicts with existing drivers.

Also, you could try to switch your router to another channel, maybe there is some interference.


There was another thread on this subject you posted in, the user suggested that using the already installed  rt73 driver and blacklisting the rt2500 driver would work. Thread is here:

[http://ubuntuforums.org/showthread.php?t=690438&page=2](http://ubuntuforums.org/showthread.php?t=690438&page=2)

If you do that, disable the driver you installed from the RaLink site.


Another possible solution: Using a windows driver with [Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by travismoore on 2008-02-11
> **justsomedude said:**
> Hmm, did you blacklist the existing drivers in /etc/modprobe.d/blacklist like the guide you used suggested properly? There may be conflicts with existing drivers.

Also, you could try to switch your router to another channel, maybe there is some interference.


There was another thread on this subject you posted in, the user suggested that using the already installed  rt73 driver and blacklisting the rt2500 driver would work. Thread is here:

[http://ubuntuforums.org/showthread.php?t=690438&page=2](http://ubuntuforums.org/showthread.php?t=690438&page=2)

If you do that, disable the driver you installed from the RaLink site.


Another possible solution: Using a windows driver with [Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

I already tried Ndiswrapper and i couldnt get it to load up the windows driver(followed their guide) but no joy.

I'll try that rt73 driver quick question though how to i make my ethernet work again because it makes things alot easier rather than booting in and out of windows to get stuff on the internet.

---

### Post by aeiah on 2008-02-11
i installed this on my pc over the weekend. that wireless card can use the rt2570 drivers from serial monkey (get the cvs release, not the beta). i followed this guide:

[http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)

when blacklisting, take note of the modules that show up (with lsmod | grep ), you may need to blacklist more modules than just:

blacklist rt2500usb
blacklist rt73usb
blacklist rt2500
blacklist rt2570
blacklist rt73
blacklist 2x00usb
blacklist 2x00lib

i think i had to also blacklist pri54, a prism module.

the rt drivers dont work with network manager, as already stated. you should be able to auto-connect on startup with the howto i linked, but if you're gonna be connecting to more wireless points than that, use RutilT located here: [http://cbbk.free.fr/bonrom/](http://cbbk.free.fr/bonrom/)

be sure to have the right dependencies and configure flag set. you should be able to google for ways to install it. it might even be in an apt repo

---

### Post by james_vanb on 2008-02-11
Using Belkin Wireless G USB Network Adapter #F5D7050 with Xubuntu 7.10.  Took forever to get the thing to work.  Used ndiswrapper and drivers off the install cd.  The following is the recipe I used:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

[B]REBOOT[B]

This where the guides I was following failed.  Blacklist doesn't work until you reboot.  If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd.  Open and navigate to the driver file under XP.  there will be 3 files.  Copy all 3 files to the file you created under "Home" by dragging and dropping.  

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module.  Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Reboot

You should now have a connection.  I only got roaming mode to work once and have been unable to replicat.  So, I left click on the network manager at the upper right corner and enter manual configuration.  Open wifi properties.  Untick "enable roaming".  Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours.  Set Password type to WPA personal.  Set Configuration to Automatic configuration (DHCP).  I don't use WEP yet, but if you do, you may have to enter your password in Network password.

Close and open Firefox - You should be in.

Hope this works, let me know how you did.

---

### Post by travismoore on 2008-02-11
Cheers guys will give it ago when I have a chance =D

---

### Post by travismoore on 2008-02-24
Ok well I've been pretty busy with college work and my new kitten so I've only managed to try justsomedudes suggestion so far. As i have some time today I am going to try and get it to work.

Going to have a go at aeiah's suggestion now.

---

### Post by travismoore on 2008-02-24
Ok I've encountered my first error.

Heres what i put in:
```
travis@Travis:~$ sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
```

The out come:
```
[sudo] password for travis:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  ndiswrapper-common kdebase-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64 lib64gcc1
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4 gcc-3.4-base
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2347kB of archives.
After unpacking 8843kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gcc-3.4-base cpp-3.4 gcc-3.4
Install these packages without verification [y/N]? y
Err http://archive.ubuntu.com gutsy/main gcc-3.4-base 3.4.6-6ubuntu2
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/main cpp-3.4 3.4.6-6ubuntu2
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com gutsy/main gcc-3.4 3.4.6-6ubuntu2
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.6-6ubuntu2_i386.deb  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.6-6ubuntu2_i386.deb  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.6-6ubuntu2_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
travis@Travis:~$ 

```

My guess is its trying to get the application from the internet and of course I don't have internet.

Any ideas?

Cheers,

Travis

---

### Post by travismoore on 2008-02-24
bump

---

### Post by travismoore on 2008-02-24
Help please? :confused:

---

### Post by justsomedude on 2008-02-24
Hey there,

just saw you're still working on this.

I hope you don't get annoyed with me for posting solutions that haven't helped you so far, sorry for this.

> My guess is its trying to get the application from the internet and of course I don't have internet.

Correct.

Now, the instructions I gave you in post #10 of this thread should restore your cable connection. If not, take a look at the changes you made while trying to get Ndiswrapper to work, I can't tell what other config files you changed while doing that.


The good news is that Hardy Heron will likely support your chipset out of the box, so if you can wait 6 weeks it may be the easier solution for you.

---

### Post by travismoore on 2008-02-24
> **justsomedude said:**
> Hey there,

just saw you're still working on this.

I hope you don't get annoyed with me for posting solutions that haven't helped you so far, sorry for this.



Correct.

Now, the instructions I gave you in post #10 of this thread should restore your cable connection. If not, take a look at the changes you made while trying to get Ndiswrapper to work, I can't tell what other config files you changed while doing that.


The good news is that Hardy Heron will likely support your chipset out of the box, so if you can wait 6 weeks it may be the easier solution for you.

Ha yea might be an idea to wait for that because this is becoming quite a pain to try get this working, and even if i do get it working i will probably end up upgrading to the new ubuntu in 6 weeks anyway.

---

