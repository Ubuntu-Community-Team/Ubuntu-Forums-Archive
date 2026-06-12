---
title: "No Sound in Linux Mint14"
date: 2013-01-13
forum: Any Other OS
---

### Post by johnfarrow on 2013-01-13
Cinnamon or KDE.  None at all.  Have a hp Laptop g7-1150.  Currently on Cinnamon.  I have posted everything I can find on the Mint forums in the terminal, but nada.

Any Ideas...

---

### Post by tgalati4 on 2013-01-13
aplay -l

---

### Post by johnfarrow on 2013-01-13
aplay -l
ohn@john-HP-Pavilion-g7-Notebook-PC ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jo

---

### Post by tgalati4 on 2013-01-13
Well, that wasn't helpful.  Do you know what type of sound chip you have in your machine?  It's probably in the Intel family, but something more specific?

tgalati4@Dell600m-mint14 ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

What modules are currently loading?

```
lsmod
```

Found this after some googling:

Pros: - Runs Windows 7 Ultimate x64 and UBUNTU 11.04 x64 beautifully. I updated some drivers Directly from Intel and Realtek. The drivers for the wireless Ralink RT5390 are available for UBUNTU, just Google it and you will find guides to make them work.

Once we find the specific sound chip, then we can search for the appropriate linux module to load.

---

### Post by johnfarrow on 2013-01-13
john@john-HP-Pavilion-g7-Notebook-PC ~ $ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  39842  1 
nls_iso8859_1          12713  1 
coretemp               13400  0 
kvm                   414070  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  0 
microcode              22803  0 
bluetooth             209199  10 bnep,rfcomm
snd_hda_intel          33491  2 
snd_hda_codec         134212  1 snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  2 snd_hda_intel,snd_hda_codec
uvcvideo               76749  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
joydev                 17457  0 
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
intel_ips              18049  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
psmouse                95552  0 
serio_raw              13215  0 
lpc_ich                17061  0 
rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              29425  2 snd_pcm,snd_seq
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             433804  1 
cfg80211              206566  2 rt2x00lib,mac80211
i915                  520519  8 
eeprom_93cx6           13302  1 rt2800pci
drm_kms_helper         46784  1 i915
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
drm                   275528  4 i915,drm_kms_helper
wmi                    19070  1 hp_wmi
i2c_algo_bit           13413  1 i915
video                  19335  1 i915
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
hid_logitech_dj        18604  0 
usbhid                 46947  1 hid_logitech_dj
hid                   100366  3 hid_generic,hid_logitech_dj,usbhid
r8169                  61650  0 
john@john-HP-Pavilion-g7-Notebook-PC ~ $

---

### Post by tgalati4 on 2013-01-13
Start reading:

[https://www.google.com/search?q=snd_hda_intel+module+options](https://www.google.com/search?q=snd_hda_intel+module+options)

---

### Post by xenopeek on 2013-01-14
Perhaps the output of inxi will give more details on the audio chip used:
```
inxi -Ax
```

---

### Post by johnfarrow on 2013-01-19
john@john-HP-Pavilion-g7-Notebook-PC ~ $ 
inxi -Ax Output.....

Audio:     Card: Intel 5 Series/3400 Series Chipset High Definition Audio driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture ver: 1.0.25
john@john-HP-Pavilion-g7-Notebook-PC ~ $

---

### Post by Lightning Dragon on 2013-01-21
Hello,

Make sure you performed a software update and nothing fails. Please see the following threads;

[http://forums.linuxmint.com/viewtopic.php?f=48&t=121099](http://forums.linuxmint.com/viewtopic.php?f=48&t=121099) (marked as solved!)

[http://www.techsupportalert.com/content/tips-and-tricks-mint-after-installation-mint-13-cinnamon-edition.htm#Set-Sound-Output](http://www.techsupportalert.com/content/tips-and-tricks-mint-after-installation-mint-13-cinnamon-edition.htm#Set-Sound-Output)

[http://forums.linuxmint.com/viewtopic.php?f=48&t=120172](http://forums.linuxmint.com/viewtopic.php?f=48&t=120172)

Sadly a lot of users have had this problem in Nadia, and when everything else failed, reinstalling was the only fix (though if you do, just go with Maya 13 LTS).

---

### Post by Gurtej22 on 2013-03-27
my linux mint give sound on starting but when i play any song or video it does not give  sound 
please help me.............

---

### Post by catchpramod on 2013-05-22
I had a similar issue, this did the job for me. 

```
sudo apt-get install libasound2-plugins:i386

```

---

