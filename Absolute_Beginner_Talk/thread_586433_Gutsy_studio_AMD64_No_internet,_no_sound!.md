---
title: "Gutsy studio AMD64: No internet, no sound!"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by sangram on 2007-10-22
Hi

I got the AMD64 version of Gutsy to install fine, but it won't connect to the internet or recognise my soundcard.

Please help. I have the source code of ALSA 1.0.15, but have no idea how to install them from the terminal, and I couldn't find a binary. Some help would be great.

Detailed information:

Hardware: K8N-E deluxe motherboard (NF3 Pro250GB) with Athlon 64 3200+. Onboard ethernet, NVidia FX5200, 1 GB RAM and **E-mu 1212m soundcard**.

Machine application: Standalone music player. Does not **need** internet connection.

Version: 7.10 Studio, AMD64 alternate install CD.

Install went very smooth, I didn't configure the network at the time of install, as I figured that I would not need it at all, but left the ethernet enabled in BIOS (in regular mode it's disabled).

Alsa 1.0.14 is supposed to support the soundcard out of the box. LSPCI shows it up as an Audigy and not an E-mu, but there's no sound (Could not open device for writing). I really can't figure out how to use ALSA, there's no 'icon' for it in any of the menus. Soundcore is loaded and enabled, but the ALSA website isn't much help telling me how to load any of the tools or utilities.

I don't really need the internet on that machine, but for troubleshooting it would be nice to have. The problem is that even ping does not work. ifconfig shows the card up fine, and the network settings are all fine. The machine is not generating any ping request when I press 'Ping' in the network tools window though.

Would be nice to be troubleshooting on the same machine as the internet connection, as it takes a lot of time to transfer data between the machines, plus I only have one monitor.

I would like to upgrade to ALSA 1.0.15, I've downloaded the source code and have absolutely no idea what to do next. If I can do that and get my soundcard working I'll be a happy camper, so please help me out to do that.

I really don't mind if there's no internet on the machine.

Thanks

Sangram

---

### Post by realvz on 2007-10-22
Try this

Installing and configuring alsa-source

Next you should install all the infrastructure necessary for compiling alsa-source (note that you need to have enabled the Universe repository, because module-assistant is in Universe):

sudo apt-get install linux-headers-$(uname -r) build-essential gcc-3.4 module-assistant

Now install the downloaded package:

sudo dpkg -i alsa-source_1.0.10+1.0.11rc2-2_all.deb #or whatever package you downloaded

You may find that dpkg throws an error saying that you don't have the debconf package installed, in which case you'll need to install it:

sudo apt-get -f install

Now, you must reconfigure the package in order to select the proper driver:

sudo dpkg-reconfigure alsa-source

I have selected PnP and no debugging, but it shouldn't be a problem to choose the other options. If you know the module you should use -ca0106 for Sound Blaster Audigy SE model SB0570-, press Ok. Otherwise, you might look into the long list shown, searching for a module compatible with your sound card, or just skip to the next screen. Here, you must find and select your module and unselect any other mark, or just select All if you don't know which module to use. Press Ok once you have selected the appropriate driver.
Installing the alsa drivers

The next step is to compile alsa-source. Close any application which is making use of the sound card and run:

sudo module-assistant auto-install alsa-source

and that should be it. Check volumes with alsamixer, starting with Front volume if you have two speakers and try to make something play a sound. If it doesn't seem to work, check amixer output for strange things, and try to correct them. Still having no sound or loud static? Repeat the steps with different selections or check other tutorials. 

[https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy](https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy)

---

### Post by sangram on 2007-10-22
Thanks for the quick reply.

I managed to get the first line going, but it didn't find the RT kernel when it was looking for dependencies.

Also, I can't sem to get the ALSA folder off my desktop (downloaded on another machine and transferred vs. USB stick) on to any of the other directories - the system cannot find the specified archives.

These are all 'tar files downloaded off the ALSA site, there isn't a .deb for it yet. Since I can't connect to the 'net (therefore no repositories) I'm downloading these files off a PC running XP and moving them on to the Linux 'box using a USB stick.

Edit: As you can probably tell, I am a total noob at Linux. If this is beyond me I'll simply give up and go back to Windows. I wouldn't mind finding something to read that gave me more of the basics - everything seems to require an internet connection, which my box doesn't have (I wouldn't mind figuring out how to get it going though).

---

### Post by realvz on 2007-10-22
lets get ur internet working 1st then

what kind of wireless card do you have...or are you using a wired connection...

dont worry...this happens...i was a total noob when i tried ubuntu too....

just give it some time...and believe me..it wont be long...

---

### Post by sangram on 2007-10-22
Thanks for your encouraging words.

I'm using a wired ethernet, onboard the nforce board. The card is correctly detected and reported with ifconfig, but is not connecting. It is a fixed IP connection and the DNS and IP parameters are all correctly verified and entered manually.

When I use 'Ping' from network tools, it simply does nothing. Not a single request outgoing, forget about response. It should work the same way as it does in windows - but not a peep from the machine. I've tried everything I could. 

Whenever I boot the first card to show up in network tools  is the Loopback adapter, and I have to manually switch the adapter to \eth0. But still nothing.

---

### Post by realvz on 2007-10-22
try this from a terminal window:

sudo ifdown eth1
sudo ifdown eth0
sudo ifup eth0


If that fails, provide output from
sudo lspci
sudo lspci -class network
sudo lsmod

---

### Post by sangram on 2007-10-22
Here are the outputs, and no, none of them worked.

music@HTPC:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
music@HTPC:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
music@HTPC:~$ sudo ifup eth0
SIOCADDRT: No such process
Failed to bring up eth0.
music@HTPC:~$ sudo lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 01)
02:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:0c.0 Mass storage controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
music@HTPC:~$ sudo lspci -class network
lspci: invalid option -- c
Usage: lspci [<switches>]

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging
music@HTPC:~$ sudo lsmod
Module                  Size  Used by
nls_iso8859_1           6656  1 
nls_cp437               8320  1 
vfat                   16640  1 
fat                    60848  1 vfat
usb_storage            83264  1 
libusual               23208  1 usb_storage
ppdev                  11528  0 
powernow_k8            16864  0 
cpufreq_powersave       3200  0 
cpufreq_stats           8704  0 
cpufreq_conservative     9864  0 
cpufreq_userspace       6304  0 
cpufreq_ondemand       11024  1 
freq_table              6592  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
button                 10656  0 
sbs                    21904  0 
ac                      7560  0 
video                  21268  0 
container               6656  0 
dock                   13248  0 
battery                12680  0 
sbp2                   27784  0 
parport_pc             42792  0 
lp                     16264  0 
parport                45196  3 ppdev,parport_pc,lp
loop                   22660  0 
snd_emu10k1_synth       9344  0 
snd_emux_synth         40448  1 snd_emu10k1_synth
snd_seq_virmidi         9984  1 snd_emux_synth
snd_seq_midi_emul       9216  1 snd_emux_synth
snd_emu10k1           153760  1 snd_emu10k1_synth
snd_ac97_codec        122840  1 snd_emu10k1
ac97_bus                4608  1 snd_ac97_codec
snd_pcm_oss            50560  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                95624  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         12688  2 snd_emu10k1,snd_pcm
snd_util_mem            6784  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12552  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5508  0 
snd_seq_oss            37632  0 
snd_seq_midi           11136  0 
snd_rawmidi            30336  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     10240  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                63776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              28040  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10516  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70696  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11040  1 snd
psmouse                46108  0 
serio_raw               9348  0 
k8temp                  7936  0 
shpchp                 38684  0 
pcspkr                  4992  0 
i2c_nforce2             8192  0 
pci_hotplug            37876  1 shpchp
i2c_core               31488  1 i2c_nforce2
evdev                  13184  3 
ext3                  147216  2 
jbd                    68592  1 ext3
mbcache                11784  1 ext3
sg                     42024  0 
ide_cd                 35872  0 
cdrom                  42152  1 ide_cd
sd_mod                 33408  5 
usbhid                 33600  0 
hid                    33664  1 usbhid
sata_nv                24452  2 
amd74xx                17712  0 [permanent]
ide_core              146320  3 usb_storage,ide_cd,amd74xx
ohci1394               39752  0 
ieee1394              112856  2 sbp2,ohci1394
sata_sil               14984  0 
ata_generic            10372  0 
floppy                 74600  0 
libata                139312  3 sata_nv,sata_sil,ata_generic
ehci_hcd               40460  0 
ohci_hcd               25476  0 
scsi_mod              174776  5 usb_storage,sbp2,sg,sd_mod,libata
forcedeth              55048  0 
usbcore               163760  6 usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd
dm_mirror              26496  0 
dm_snapshot            20216  0 
dm_mod                 69872  7 dm_mirror,dm_snapshot
thermal                16784  0 
processor              36232  2 powernow_k8,thermal
fan                     7176  0 
fuse                   53808  1 
apparmor               48288  0 
commoncap               9600  1 apparmor
music@HTPC:~$

---

### Post by realvz on 2007-10-22
hmmm....can you Also post the /etc/network/interfaces file.

you might also wanna post your problem in 
Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > Networking & Wireless

there are more experts there about your specific problem.

:) Hey this is the Absolute Beginner section....LOL

---

### Post by sangram on 2007-10-22
Quick note: My crad is wrongly identified as an audigy, it is actually a 1212m. I guess we'll cross that bridge when we come to it. I probably need to flash a new firmware on it.

---

### Post by tony.morse on 2007-10-22
Hi I also had sound card problems, and the stuff I used to do in Feisty didn't fix it in Gusty.  Anyway this is how I did fix it eventually...
[http://ubuntuforums.org/showthread.php?t=153823](http://ubuntuforums.org/showthread.php?t=153823)

(I know, this is old and some line don't work, just plow on as if they did, and yes I realize you don't have an audigy, this could still work)

---

### Post by sangram on 2007-10-22
Here's the interfaces file

auto lo
iface lo inet loopback

iface eth0 inet static
address 203.109.118.254
netmask 255.255.255.224
gateway 209.109.118.225

auto eth0

---

### Post by sangram on 2007-10-22
Hey thanks Tony, I bookmarked your post. I don't yet have a way to connect to the outside world from that box though, I assume that without that I'm not going to get anywhere for some time!

---

### Post by realvz on 2007-10-22
just one more thing....how do you connect to internet...like do you have a router or a switch or anything or do u directly plug the computer in to the modem?

---

### Post by sangram on 2007-10-22
It's directly connected to the cable modem in my case.

The only network config I need to do (in Wondows) is my Ip and subnet mask, plus the DNS server addresses. I did the same for the connection in  this machine.

---

### Post by realvz on 2007-10-22
now did this machine of yours...the ubuntu one...did it ever work with this modem...i mean were you running windows on it earlier and was it running fine...

---

### Post by sangram on 2007-10-22
Oh yeah, absolutely. The network card runs fine with Windows. As a matter of fact, the working Windows install is still on a separate disk which is disconnected, and it's a five-minute job to switch between the installs. 

I haven't used the internet on that machine for a very long time though - it's a standalone machine.

But yes, it works just fine. I use it to check cddb info for my audio CDs, but not much else.

---

