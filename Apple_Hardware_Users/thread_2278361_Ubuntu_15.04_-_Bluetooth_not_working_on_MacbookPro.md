---
title: "Ubuntu 15.04 - Bluetooth not working on MacbookPro(12,1)"
date: 2015-05-16
forum: Apple Hardware Users
---

### Post by vishal733 on 2015-05-16
Any solutions to resolve bluetooth functionality on Macbook Pro (12,1) (early 2015 Macbook Pro 13).

Ubuntu works well other than bluetooth and touchpad functionality.

---

### Post by raywang2 on 2015-06-24
No one has the experience to this problem? I'm facing this one too

---

### Post by sundragon2 on 2015-07-21
No updates. I have continued to update my software on Ubuntu with no change in functionality. I looked online and no luck. I'm glad I didn't commit to this on my SSD and installed it on a SD card.

---

### Post by sicvolo on 2015-07-22
Looks like something in userland blocks the device from being recognized. What do you see with lsmod, lsusb and lspci in regards to bluetooth?

---

### Post by vishal733 on 2015-07-22
lsmod output:
> Module                  Size  Used by
usblp                  20480  0 
msr                    16384  0 
nls_utf8               16384  1 
hfsplus               106496  1 
binfmt_misc            20480  1 
nls_iso8859_1          16384  1 
joydev                 20480  0 
hid_apple              16384  0 
hid_generic            16384  0 
snd_hda_codec_hdmi     53248  1 
applesmc               20480  0 
input_polldev          16384  1 applesmc
snd_hda_codec_cirrus    20480  1 
snd_hda_codec_generic    69632  1 snd_hda_codec_cirrus
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
aesni_intel           172032  0 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
snd_hda_intel          32768  5 
gf128mul               16384  1 lrw
snd_hda_controller     32768  1 snd_hda_intel
snd_usb_audio         180224  0 
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_cirrus
snd_usbmidi_lib        32768  1 snd_usb_audio
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
bcm5974                20480  0 
snd_pcm               106496  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
btusb                  40960  0 
bluetooth             491520  1 btusb
uvcvideo               90112  0 
snd_rawmidi            32768  2 snd_usbmidi_lib,snd_seq_midi
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
usbhid                 53248  0 
videobuf2_core         49152  1 uvcvideo
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
v4l2_common            16384  1 videobuf2_core
hid                   114688  3 hid_generic,usbhid,hid_apple
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
i915                 1052672  9 
lpc_ich                24576  0 
brcmfmac              278528  0 
brcmutil               16384  1 brcmfmac
drm_kms_helper        122880  1 i915
cfg80211              540672  1 brcmfmac
drm                   344064  8 i915,drm_kms_helper
snd                    90112  23 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
bdc_pci                16384  0 
shpchp                 40960  0 
mei_me                 20480  0 
i2c_algo_bit           16384  1 i915
mei                    90112  1 mei_me
soundcore              16384  2 snd,snd_hda_codec
sbs                    16384  0 
sbshc                  16384  1 sbs
spi_pxa2xx_platform    24576  0 
apple_bl               16384  0 
video                  20480  1 i915
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
ahci                   36864  4 
uas                    24576  0 
libahci                32768  1 ahci
usb_storage            69632  1 uas


lsusb:
> Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 05ac:0273 Apple, Inc. 
Bus 001 Device 005: ID 05ac:8290 Apple, Inc. 
Bus 001 Device 007: ID 046d:c535 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lspci:
> 00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:15.0 DMA controller: Intel Corporation Wildcat Point-LP Serial IO DMA Controller (rev 03)
00:15.4 Serial bus controller [0c80]: Intel Corporation Wildcat Point-LP Serial IO GSPI Controller #1 (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1c.5 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Multimedia controller: Broadcom Corporation Device 1570
03:00.0 Network controller: Broadcom Corporation BCM43602 802.11ac Wireless LAN SoC (rev 01)
04:00.0 SATA controller: Samsung Electronics Co Ltd Device a801 (rev 01)
05:00.0 PCI bridge: Intel Corporation Device 156d
06:00.0 PCI bridge: Intel Corporation Device 156d
06:03.0 PCI bridge: Intel Corporation Device 156d
06:04.0 PCI bridge: Intel Corporation Device 156d
06:05.0 PCI bridge: Intel Corporation Device 156d
06:06.0 PCI bridge: Intel Corporation Device 156d
07:00.0 System peripheral: Intel Corporation Device 156c

---

### Post by imoody on 2015-08-26
I also have the problem of Bluetooth not working but have a macbook pro 13 with 12.2. and have added the following if it can help
my lsmod
sofie@SofieLinux:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          16384  1 
snd_hda_codec_hdmi     53248  1 
intel_rapl             20480  0 
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0 
intel_powerclamp       20480  0 
coretemp               16384  0 
kvm_intel             151552  0 
kvm                   483328  1 kvm_intel
crct10dif_pclmul       16384  0 
crc32_pclmul           16384  0 
ghash_clmulni_intel    16384  0 
applesmc               20480  0 
input_polldev          16384  1 applesmc
aesni_intel           172032  0 
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lpc_ich                24576  0 
brcmfmac              278528  0 
snd_hda_codec_cirrus    20480  1 
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_hda_codec_generic    69632  1 snd_hda_codec_cirrus
btusb                  40960  0 
brcmutil               16384  1 brcmfmac
snd_rawmidi            32768  1 snd_seq_midi
bluetooth             491520  1 btusb
cfg80211              540672  1 brcmfmac
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
bdc_pci                16384  0 
i915                 1060864  4 
snd_hda_intel          36864  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_cirrus
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
shpchp                 40960  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper        126976  1 i915
snd_timer              32768  2 snd_pcm,snd_seq
mei_me                 20480  0 
mei                    90112  1 mei_me
drm                   344064  5 i915,drm_kms_helper
snd                    90112  21 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_cirrus
soundcore              16384  2 snd,snd_hda_codec
i2c_algo_bit           16384  1 i915
sbs                    16384  0 
sbshc                  16384  1 sbs
video                  20480  1 i915
spi_pxa2xx_platform    24576  0 
apple_bl               16384  0 
mac_hid                16384  0 
parport_pc             32768  0 
ppdev                  20480  0 
lp                     20480  0 
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2 
hid_generic            16384  0 
uas                    24576  0 
ahci                   36864  3 
libahci                32768  1 ahci
usb_storage            69632  1 uas
usbhid                 53248  0 
hid                   110592  2 hid_generic,usbhid
sofie@SofieLinux:~$ 
 lsusb
Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05ac:0273 Apple, Inc. 
Bus 001 Device 003: ID 05ac:8290 Apple, Inc. 
Bus 001 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sofie@SofieLinux:~$ 

lspci
sofie@SofieLinux:~$ lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:15.0 DMA controller: Intel Corporation Wildcat Point-LP Serial IO DMA Controller (rev 03)
00:15.4 Serial bus controller [0c80]: Intel Corporation Wildcat Point-LP Serial IO GSPI Controller #1 (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.1 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #2 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1c.5 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Multimedia controller: Broadcom Corporation Device 1570
03:00.0 Network controller: Broadcom Corporation BCM43602 802.11ac Wireless LAN SoC (rev 01)
04:00.0 SATA controller: Samsung Electronics Co Ltd Device a801 (rev 01)
05:00.0 PCI bridge: Intel Corporation Device 156d
06:00.0 PCI bridge: Intel Corporation Device 156d
06:03.0 PCI bridge: Intel Corporation Device 156d
06:04.0 PCI bridge: Intel Corporation Device 156d
06:05.0 PCI bridge: Intel Corporation Device 156d
06:06.0 PCI bridge: Intel Corporation Device 156d
07:00.0 System peripheral: Intel Corporation Device 156c
sofie@SofieLinux:~$

---

### Post by mj0g on 2015-09-10
This thread is a dupe of [http://ubuntuforums.org/showthread.php?t=2282509](http://ubuntuforums.org/showthread.php?t=2282509) - there's more information there.

---

