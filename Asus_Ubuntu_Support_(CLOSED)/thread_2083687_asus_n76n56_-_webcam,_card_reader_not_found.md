---
title: "asus n76/n56 - webcam, card reader not found"
date: 2012-11-13
forum: Asus Ubuntu Support (CLOSED)
---

### Post by broken plastic on 2012-11-13
Hey all,

Like hte title says, my webcam and card reader do not seem to exist.  i thought the webcam had worked in the summer, while using 12.04 ubuntu studio with unity, but it wasnt until after i had upgraded to 12.10 and tried to use skype that I found an issue.  Cheese, guvcview, skype, vlc, doesnt matter - the camera doesnt show up.

> $ gstreamer-properties

(gstreamer-properties:7408): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:7408): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]
  
> $ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory

> $ ls /dev/v4l 
ls: cannot access /dev/v4l: No such file or directory

> $ lsusb
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

here is a previous lsusb report
> lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3362 IMC Networks 

Can any of you with the same series laptop post results of lsusb, etc? I cant even confirm what oem devices should have been installed.

Is it a function key issue to even turn the webcam on?  There is nothing in the bios regarding such a device.  Would the card reader not showing up (i unfortunately dont have any media to test it with)

Since upgrading, suspend and hibernate do not work, but I will assume that is a separate issue.

cuda and bumblebee work.  internal mic also works.

any ideas?

oh, i should also add that I have tried fresh installs on other partitions with 12.10 ubuntu and ubuntu studio - same results. Kernels 3.5.18, 3.5.17 (generic and low latency), 3.6 generic

---

### Post by broken plastic on 2012-11-13
Just saw this thread, [http://ubuntuforums.org/showthread.php?t=2069298](http://ubuntuforums.org/showthread.php?t=2069298), and tried my chances installing the realtek deb.

lsusb now outputs
> $ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:3362 IMC Networks 


---

### Post by broken plastic on 2012-11-13
lsmod results
> $ lsmod
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               287145  3 vboxpci,vboxnetadp,vboxnetflt
bbswitch               13396  0 
parport_pc             32688  0 
ppdev                  17073  0 
rfcomm                 42523  12 
bnep                   18140  2 
binfmt_misc            17500  1 
nls_iso8859_1          12713  1 
snd_hda_codec_realtek    77876  1 
joydev                 17457  0 
snd_hda_intel          33491  3 
snd_hda_codec         134212  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
mxm_wmi                12979  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
asus_nb_wmi            12710  0 
coretemp               13400  0 
asus_wmi               24088  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
kvm_intel             136907  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
kvm                   418206  1 kvm_intel
ghash_clmulni_intel    13180  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  520724  3 
aesni_intel            51078  0 
cryptd                 20402  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
ath9k                 131308  0 
snd                    74638  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath3k                  12918  0 
wmi                    19070  2 mxm_wmi,asus_wmi
btusb                  18334  0 
bluetooth             209256  23 rfcomm,bnep,ath3k,btusb
drm_kms_helper         46784  1 i915
mac_hid                13205  0 
mac80211              544104  1 ath9k
microcode              22803  0 
ath9k_common           14055  1 ath9k
psmouse                95552  0 
ath9k_hw              395218  2 ath9k,ath9k_common
soundcore              15047  1 snd
lpc_ich                17061  0 
mei                    40690  0 
serio_raw              13215  0 
drm                   275528  4 i915,drm_kms_helper
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
cfg80211              202470  3 ath9k,mac80211,ath
i2c_algo_bit           13413  1 i915
lp                     17759  0 
video                  19335  1 i915
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid


---

### Post by broken plastic on 2012-11-13
lspci
> $ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 650M] (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 08)


---

### Post by fabian.g on 2013-02-24
Hi!

Did you find a solution to the card reader webcam problem? I'm thinking about buying an asus n76 within the next days.

Thanks,
Fabian

---

