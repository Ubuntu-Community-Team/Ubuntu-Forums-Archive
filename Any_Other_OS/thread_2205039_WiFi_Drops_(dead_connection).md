---
title: "WiFi Drops (dead connection)"
date: 2014-02-11
forum: Any Other OS
---

### Post by marc16 on 2014-02-11
Hi, new to Ubuntu (12.04 LTS 64bit), trying to move away from windows and doing ok so far with it on most things but I am getting a weird issue with my wifi dongle. It randomly disconnects, doesn't seem to be any pattern as to why, and by disconnect I mean I lose all data and yet the connection shows as up. I can't connect to other PC's on my network, can't get to the internet yet shows as connected. A disconnect and reconnect gets everything back up and running but obviously that is annoying. Looked through some previous threads and seems to be a common problem but some of the fixes I tried didn't work so just going to start from scratch and ask for help.

Here are some outputs asked for in other threads, let me know if you need anything else. I have the disc for the dongle which says it supports linux yet don't see any sort of .sh file? Branded as pluscom (cheap thing) but drvers are realtek, was working fine on windows 7 before I wiped it. ini file shows the driver name as REALTEK RTL8187 which judging by the output below doesn't seem to be the version picked up yet going to the website to download it for linux it fails but can get into that if that is the agreed upon path.

```
marc@MUTHER:~$ lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8169
marc@MUTHER:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 003: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 002 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
marc@MUTHER:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40302  1 
dm_crypt               23111  1 
arc4                   12573  2 
snd_hda_codec_hdmi     41736  1 
rtl8192cu              72806  0 
snd_hda_codec_realtek    56448  1 
rtl8192c_common        53827  1 rtl8192cu
rtl_usb                18713  1 rtl8192cu
rtlwifi                64035  2 rtl8192cu,rtl_usb
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              619465  3 rtl8192cu,rtl_usb,rtlwifi
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rfcomm                 74718  0 
bnep                   24107  2 
snd_seq_midi           13324  0 
eeepc_wmi              13151  0 
snd_rawmidi            30416  1 snd_seq_midi
cfg80211              499466  2 rtlwifi,mac80211
asus_wmi               24794  1 eeepc_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             391726  10 rfcomm,bnep
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13890  1 asus_wmi
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse               104093  0 
snd                    73753  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13413  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
parport_pc             32866  0 
ppdev                  17711  0 
lpc_ich                21163  0 
mei_me                 18418  0 
mei                    78537  1 mei_me
mac_hid                13253  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
nls_iso8859_1          12713  1 
hid_generic            12548  0 
usbhid                 53329  0 
hid                   106315  2 hid_generic,usbhid
i915                  688281  3 
drm_kms_helper         53237  1 i915
drm                   306660  4 i915,drm_kms_helper
wmi                    19256  1 asus_wmi
i2c_algo_bit           13564  1 i915
video                  19574  2 asus_wmi,i915
r8169                  73299  0 
mii                    13981  1 r8169
marc@MUTHER:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"*******"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 84:9C:A6:51:2F:B7   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

marc@MUTHER:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
marc@MUTHER:~$ sudo iwlist scan

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 84:9C:A6:51:2F:B7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"*******"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 116ms ago
                    IE: Unknown: 00074665636B4F4646
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

marc@MUTHER:~$ 


```

Any help appreciated, cheers.

---

### Post by varunendra on 2014-02-13
Welcome to Ubuntu Forums marc16 !

A few quick suggestions based on your outputs -
> **marc16 said:**
> ```

wlan0     Scan completed :
          Cell 01 - Address: 84:9C:A6:51:2F:B7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ....
                    *<snip>*
                    ....
                    IE: IEEE 802.11i/**[COLOR="#006400"]WPA2[/COLOR]** Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F02C0000
                    IE: [B][COLOR="#FF0000"]WPA[/COLOR] Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR][/B]

```
First of all, please log into your router/access-point and change its encryption to pure WPA2-AES(CCMP). Currently it is set to WPA/WPA2 mixed mode with TKIP - which should be avoided at all costs. Save the change and reboot the router.

After that, try connecting again and IF required, try this in Ubuntu (in a terminal) -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=1
```
This would be a temporary change that will be lost at next boot, so try the connection without rebooting after above. If it helps, we can make it permanent.

If these two changes don't help, also try disabling the N-channel in your router (set it to b/g only mode, currently it seems to be in b/g/n mode). Again, save the changes > reboot it > try the connection in Ubuntu.

Any improvement? If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by marc16 on 2014-02-14
Thanks Varun, unfortunately I ended up getting more and weirder issues. Like I rebooted and it wouldn't see my wifi dongle at all, then tried to reinstall and got some gnome crash. I have ended up installing Zorin instead for the time being so it looks a bit more familiar. 

I got the same wi-fi dead connection however so made the router change but no joy so tried the commands you suggested and have been ok for the moment. It seems very random but am doing a continuous ping and downloading a bunch so should see in the next few hours hopefully if the commands worked. Although this is no longer as relevant to ubuntu I guess. What do they do btw?

---

### Post by varunendra on 2014-02-14
> **marc16 said:**
> What do they do btw?
The first command (modeprobe -r..) removes (due to the "-r" option) the driver so that we can load it with parameters we want.
The second command reloads it with the parameter "swenc=1".

This parameter shifts the load of packet encryption from the hardware (the wireless chip) to the software (driver + OS). This helps when the hardware encryption can't keep up with the packet speed (due to too much speed, or inefficient encryption used) resulting in corrupt packets.

If the problem persists, you may try newer (backported) drivers, although I don't know if the steps to install them in Zorin are same/similar or different.

---

### Post by Bucky Ball on 2014-02-15
*Thread moved to **Other OS/Distro Support**.*
[QUOTE=marc16]
 Although this is no longer as relevant to ubuntu I guess. [/QUOTE]

Zorin is not supported in the main support areas of this forum. See here:

[http://zorin-os.webs.com/apps/forums/](http://zorin-os.webs.com/apps/forums/)

---

### Post by varunendra on 2014-02-15
@ Mark,

In reply to your PM to me -
> ....the fix you provided works ([http://ubuntuforums.org/showthread.php?t=2205039](http://ubuntuforums.org/showthread.php?t=2205039)) but as mentioned is only temporary. How do you make this permanent?....
To make the parameter swenc=1 permanent, create a .conf file in /etc/modprobe.d directory containing the following line -
```
options rtl8192cu swenc=1
```
The name of the file doesn't matter, but its extension name *should* contain .conf (as the files without this extension will be ignored in future releases) and its contents MUST be same as above. To do that quickly via terminal, you can use the following command -
```
echo "options rtl8192cu swenc=1" | sudo tee /etc/modprobe.d/rtl8192cu.conf
```
This will put the above code in a file "**rtl8192cu.conf**" in the **/etc/modprobe.d** directory. This file will make the parameter be loaded automatically since next boot.

If this makes your connection good and stable, please mark the thread as [SOLVED] to help others looking for help on similar problem. Use the "Thread Tools" link above the top post to mark it as such. Thanks !

---

