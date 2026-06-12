---
title: "wicd connects to wifi and stays that way for about 10mins then disconnect"
date: 2011-09-20
forum: Any Other OS
---

### Post by 7cardcha on 2011-09-20
I have linux mint. I used to have Network-Manager and it would disconnect in about 2 minutes. When I switched to wicd this problem was reduced but not by that much. The connection is great while it works. When it loses connection it stop recognizing my wireless and a reboot is required. Please help. FYI Linux mint is based off of ubuntu

---

### Post by wildmanne39 on 2011-09-20
Hi, please open a terminal by hitting ctrl+alt+t then paste these commands into it, then post the results here from each command:
```
cat /etc/lsb-release; uname -a
sudo lshw -C network
lspci -nn | grep -e 0280 -e 0200
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by 7cardcha on 2011-09-20
Cat command:
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=11
DISTRIB_CODENAME=katya
DISTRIB_DESCRIPTION="Linux Mint 11 Katya"
Linux Charles-Laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

Lshw command:
PCI (sysfs) 

Lscpi command:
01:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

lsusb command:
Bus 005 Device 002: ID 0cf3:3005 Atheros Communications, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b262 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1410:a014 Novatel Wireless 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Iwconfig command:

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"some essid i dont want you to know :D"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: **:**:**:**:**:**  (Bleeped out) 
          Bit Rate=54 Mb/s   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:240   Missed beacon:0

Rfkill command:
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


lsmod command:
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
rfcomm                 38125  8 
arc4                   12473  2 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
ath9k                 103633  0 
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
sco                    17779  2 
bnep                   17785  2 
snd_seq_midi           13132  0 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
mac80211              257001  1 ath9k
btusb                  18160  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb
uvcvideo               66851  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
videodev               75143  1 uvcvideo
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
psmouse                73312  0 
ath                    19141  2 ath9k,ath9k_hw
tpm_tis                13993  0 
serio_raw              12990  0 
cfg80211              156212  3 ath9k,mac80211,ath
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm                    21251  1 tpm_tis
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tpm_bios               13460  1 tpm
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
usb_storage            43946  0 
uas                    17676  0 
i915                  450944  3 
drm_kms_helper         40745  1 i915
ahci                   21591  2 
drm                   180037  4 i915,drm_kms_helper
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915








Thanks a lot for even caring.

---

### Post by 7cardcha on 2011-09-20
Oh yeah and I supported you on your membership thing.

---

### Post by wildmanne39 on 2011-09-20
Hi, your welcome! and thank you for supporting me. I am looking up that card right now, that whole family of cards have issues but most of theme can be resolved.

---

### Post by 7cardcha on 2011-09-20
Oh yeah I spent 3 hours of googling wicd/network-manager stuff so don't think I didn't try. Anyways thanks for helping.

---

### Post by wildmanne39 on 2011-09-20
Hi, Is your network set to WPA and WPA2 mixed mode? That often causes problems. If you can, try WPA2 only. You might also try:
```
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
```

You can make it permanent 
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thank you

---

### Post by 7cardcha on 2011-09-20
Well I don't have a "Just WPA2" option [http://imgur.com/NbVao](http://imgur.com/NbVao) I did the sudo gedit thing(I am not a linux noob I know abou command line and stuff) it might have worked might not I will know in 15-30mins(It should disconnect by then if it didn't help) Thanks for helping I will let you know when 15-30mins has gone by.

---

### Post by wildmanne39 on 2011-09-20
Hi, ok let me know, I am about to go to bed for tonight, I have been on for fourteen hours.

The wpa2 only would be in your router settings, you can get to them by typing 192.168.0.1 into your web browser while you are hard wired to the router,sometimes it is a little different numbers it just depends on your router.

The setting well be under wireless in your router configuration file.
Thank you

---

### Post by 7cardcha on 2011-09-20
Go to bed :D. I am about to to.

---

### Post by Perfect Storm on 2011-09-20
Moved to Other OS/Distro Talk.

---

### Post by 7cardcha on 2011-09-20
It works PERFECTLY thank you very much.

---

### Post by wildmanne39 on 2011-09-20
Hi, your welcome! that is great, I am glad to hear it.

---

