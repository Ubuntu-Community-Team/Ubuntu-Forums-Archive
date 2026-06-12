---
title: "No sound after start up in mint 14"
date: 2013-05-22
forum: Any Other OS
---

### Post by Kranium31 on 2013-05-22
My new laptop is an MSI GE60 0NC-498US and i recently installed Mint 14 Nadia Mate 64bit on my new SSD.  After the first reboot after install there is no sound after the system sounds at startup.

btw im fairly new to linux so go easy on me :)

this thread:
[http://ubuntuforums.org/showthread.php?t=2104539](http://ubuntuforums.org/showthread.php?t=2104539)

pointed me to the snd_hda_intel options database here:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568). 

 None of the commands work in mint though it keeps giving me this error message:

jay@msi ~ $ sudo gedit /etc/modprobe.d/alsa-base
[sudo] password for jay: 
sudo: gedit: command not found

Then i use sudo apt-get install instead and it says modprobe cant be found :confused:


Any help is greatly appreciated :)



here are a few outputs:

**_aplay -l:_**

jay@msi ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


[B][U]lsmod:

[/U][/B]jay@msi ~ $ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
joydev                 17457  0 
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
ghash_clmulni_intel    13180  0 
aesni_intel            51037  2 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
aes_x86_64             17208  1 aesni_intel
arc4                   12529  2 
mxm_wmi                12979  0 
rfcomm                 46619  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
parport_pc             32688  0 
ppdev                  17073  0 
binfmt_misc            17500  1 
microcode              22803  0 
psmouse                95552  0 
serio_raw              13215  0 
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlwifi               386826  0 
mac80211              539908  1 iwlwifi
snd_seq_midi           13324  0 
lpc_ich                17061  0 
cfg80211              206566  2 iwlwifi,mac80211
snd_rawmidi            30512  1 snd_seq_midi
rts_pstor             433804  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19070  1 mxm_wmi
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i915                  520519  2 
mei                    40690  0 
mac_hid                13205  0 
drm_kms_helper         46784  1 i915
drm                   275528  3 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
video                  19335  1 i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci




_** inxi -Ax**_

jay@msi ~ $ inxi -Ax
Audio:     Card: Intel 7 Series/C210 Series Chipset Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture ver: 1.0.25

---

### Post by smellyman on 2013-05-23
haven't used Mint or Ubuntu in a while but....

just type alsamixer in the terminal and make sure nothing is muted or turned down.

[B]jay@msi ~ $ sudo gedit /etc/modprobe.d/alsa-base
[sudo] password for jay: 
sudo: gedit: command not found[/B]

try gksu instead of sudo or sudo nano or just browse to alsa-base and open it.  :)  sometimes things are made more difficult than they acutally are.

---

### Post by Kranium31 on 2013-05-25
Getting into a file in terminal is still very hard for me. I can change directories but past that i get lost...

---

### Post by Kranium31 on 2013-05-26
I edited the conf file and still nothing. I'm not sure what command to use for my sound card though.  Can anyone give me the right command to use from my sound card info?

---

### Post by Rebelli0us on 2013-05-27
On Mint new installations the default sound scheme is "no sound". You just have to select one of the available schemes to enable sound. But if still no sound, install MInt 13 ... 14 has occasional bugs.

---

