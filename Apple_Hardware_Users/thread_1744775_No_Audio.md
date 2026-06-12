---
title: "No Audio"
date: 2011-04-30
forum: Apple Hardware Users
---

### Post by Bray90820 on 2011-04-30
so here is my problem i have a macpro 5,1 the tower NOT the laptop people are always making that mistake and for the life of me i cant seem to get any audio through my external speakers i have tried everything i can think of

---

### Post by tstc on 2011-04-30
try"alsamixer" in terminal
raise every level that you see
might have to select the correct soundcard, my G5 used soundbylayout
exit "alsamixer" 
test your sound with sound applet on task bar
run "alsactl store" to save as SU

---

### Post by Bray90820 on 2011-04-30
i probably should have been more specific i already tried alsamixer and all the settings in the general sound settings i also tried a the usb creative x-fi with headphones and that worked f you need anymore information from me just ask

---

### Post by tstc on 2011-04-30
thats reall the only thing I can think of. some levels are muted by default in alsamixer. your probably gonna want to run lspci, lsmod, and look in /etc/modprobe.d to see what's/what's not configured. Good luck.

---

### Post by Bray90820 on 2011-04-30
hum i don't really know how to use slmod or slpci but thank anyways

---

### Post by tstc on 2011-04-30
just run those commands in a terminal AND look to see what's in the /etc/modprobe.d directory.

---

### Post by Bray90820 on 2011-04-30
well i ran the 2 commands and this is what it gave me 

for lspci i got ALL of this 

00:00.0 Host bridge: Intel Corporation 5520 I/O Hub to ESI Port (rev 22)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 22)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 22)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 22)
00:0d.0 Host bridge: Intel Corporation Device 343a (rev 22)
00:0d.1 Host bridge: Intel Corporation Device 343b (rev 22)
00:0d.2 Host bridge: Intel Corporation Device 343c (rev 22)
00:0d.3 Host bridge: Intel Corporation Device 343d (rev 22)
00:0d.4 Host bridge: Intel Corporation 5520/5500/X58 Physical Layer Port 0 (rev 22)
00:0d.5 Host bridge: Intel Corporation 5520/5500 Physical Layer Port 1 (rev 22)
00:0d.6 Host bridge: Intel Corporation Device 341a (rev 22)
00:0d.7 Host bridge: Intel Corporation Device 341b (rev 22)
00:0e.0 Host bridge: Intel Corporation Device 341c (rev 22)
00:0e.1 Host bridge: Intel Corporation Device 341d (rev 22)
00:0e.2 Host bridge: Intel Corporation Device 341e (rev 22)
00:0e.3 Host bridge: Intel Corporation Device 341f (rev 22)
00:0e.4 Host bridge: Intel Corporation Device 3439 (rev 22)
00:0f.0 Performance counters: Intel Corporation Device 3424 (rev 22)
00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 22)
00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 22)
00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 22)
00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 22)
00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 22)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 22)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 22)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 22)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 22)
00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 22)
00:16.0 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.1 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.2 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.3 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.4 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.5 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.6 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:16.7 System peripheral: Intel Corporation 5520/5500/X58 Chipset QuickData Technology Device (rev 22)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 PCI bridge: Integrated Device Technology, Inc. PES12T3G2 PCI Express Gen2 Switch (rev 01)
02:02.0 PCI bridge: Integrated Device Technology, Inc. PES12T3G2 PCI Express Gen2 Switch (rev 01)
02:04.0 PCI bridge: Integrated Device Technology, Inc. PES12T3G2 PCI Express Gen2 Switch (rev 01)
05:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
05:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
09:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
0a:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
0b:00.0 PCI bridge: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge (rev 01)
0c:00.0 FireWire (IEEE 1394): Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller (rev 01)
0d:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)


and when i ran lsmod i got this 

Module                  Size  Used by
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18131  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
snd_hda_codec_hdmi     28103  1 
fglrx                2739144  176 
snd_usb_audio         112426  0 
snd_hda_codec_realtek   336693  1 
uvcvideo               72195  0 
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_intel          33211  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
applesmc               19604  0 
input_polldev          14007  1 applesmc
hid_apple              13324  0 
snd_hwdep              13604  2 snd_usb_audio,snd_hda_codec
lib80211_crypt_tkip    17387  0 
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
videodev               82052  1 uvcvideo
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
v4l2_compat_ioctl32    17078  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
wl                   2568244  0 
i7core_edac            27903  0 
usb_storage            53538  0 
uas                    17996  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  12 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_codec_realtek,snd_hda_intel,snd_usbmidi_lib,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18600  2 
bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb
usbhid                 46956  0 
hid                    91020  2 hid_apple,usbhid
edac_core              53845  1 i7core_edac
shpchp                 37297  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ioatdma                43771  24 
lp                     17825  0 
dca                    15219  1 ioatdma
parport                46458  3 parport_pc,ppdev,lp
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
e1000e                159096  0 
crc_itu_t              12707  1 firewire_core


what it looks like is it is trying to you my video card with hdmi audio but i dont have an hdmi port on mu video card

---

### Post by tstc on 2011-04-30
I'll say... that your snd system is completely different than anything that I've seen on my old mac 450 AGP or my 1.8DP. It looks to be a usb related sound device of some sort. Maybe someone else will chime in but I would look at something simple first, it does take those channels  in alsamixer a second or two to respond from a keystroke in order to raise the level. Your hardware IS recognized. A good thing!

---

### Post by Bray90820 on 2011-04-30
the sound card i am trying to get working is not a usb although i did plug in a USB creative x-fi but the one im trying to get working is the one that came pre installed in the mac in this mac there are 2 audio cards one with a 3.5 mm jack which is the one im trying to get working and another one with spdif just for reference its an 8 core xeon tower macpro that i bought new in September and i am currently using the creative x-fi for audio but i would like to use the internal one because its much higher quality and so i can switch between OS X ubuntu and windows easily sorry of that was a bit hard to read

---

### Post by tstc on 2011-04-30
"soundcard" "controller" "chip" are all interchangeble . If your system has only been out for 6 months or so, there may not be support for it yet. I'd just use your Creative/usb when in Ubuntu for the time being. See ya

---

### Post by Hatsune Miku on 2011-05-01
Lets do this the simple way shall we. Every mac i get i need to unmute the device, so simply unmute it! How you say? Well with gnome-alsamixer... but the ubuntu dev team ALWAYS REMOVE IT!!! so do this!

```
sudo apt-get install gnome-alsamixer
```

Install the GRAPHICAL alsamixer. Then open termina type

```
gnome-alsamixer
```

and unmute the speakers. I hope this one works lol!

---

### Post by luismacb on 2011-05-01
Me too, no audio.

Macbook pro 13,3, nvidia mcp89 audio.
aplay -l list correctly the device, and in alsamixer I can see Master and PCM unmuted and 100% volume.

I've noticed that I can record without problems (and audio is recorded, checked with google translate), but I can0t hear anything at forntal speaker and headphones.

Sound was working in Ubuntu 10.10 (I followed the guide [https://help.ubuntu.com/community/MacBookPro7-1/Maverick](https://help.ubuntu.com/community/MacBookPro7-1/Maverick)), but broke afer upgrade to 11.04.

Someone with the same problem?

---

### Post by brodieman01 on 2011-05-01
I am experiencing the same issue! My audio worked in the previous version of Ubuntu, but now it is dead. I have gone through all of the ssh to see if Ubuntu "sees" my equipment, and it does. So, I am in the same predicament, how do I get the audio fixed????

---

### Post by luismacb on 2011-05-02
Any idea to get it working?
I'm running the propietary driver of Nvidia, maybe the driver is not ready?

---

### Post by luismacb on 2011-05-02
I can't believe it!!

I found the solution. It was all the Mactel PPA, this is a big mistake, this should be warned!! Those untrusted ppas.... ](*,)

So, simply uninstall snd-hda-dkms with Synaptics and reboot!

Via: [http://ubuntuforums.org/showpost.php?p=10747611&postcount=307](http://ubuntuforums.org/showpost.php?p=10747611&postcount=307)

---

### Post by brodieman01 on 2011-05-02
is the snd-hda-dkms only on the mac book? I am running an IMac and have no sound. I have looked in symantio, and many other places and nothing. I am still very new to Ubuntu and really do not know my way around so please help me!  Thank you every one!

---

