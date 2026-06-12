---
title: "No Wireless connections - Joli OS"
date: 2012-04-11
forum: Any Other OS
---

### Post by giorgioscia on 2012-04-11
Hi, first ever post!!

Im having a little trouble with my wireless on my Joli OS, and really need help as I miss using my little netbook! :(

I have decent experience with Linux but I think my lack of experience with this Ubuntu variation is my weakness haha but after checking everything the [Joli help site]("http://help.jolicloud.com/entries/199163-my-wifi-doesn-t-work") told me to do, I took its advice and posted here for help!

When I right click the network connections button in the notification area on my toolbar, both the 'Enable Networking' and 'Enable Wireless' buttons are ticked, however when left clicking, underneath Wireless Networks, where all the available networks used to be listed, it just says "disconnected" :(

I know the Ethernet works as that's how I'm typing this post at the moment but that's not a great solution on a netbook that I want to use in my bedroom.

anyway here are the details:

Joli OS v1.2
Toshiba NB100
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

Is this simply a driver problem?

Thankyou :)

---

### Post by praseodym on 2012-04-11
Hi,

please show the outputs of:
```
uname -a
lsmod
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep ath
```

---

### Post by Elfy on 2012-04-11
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by giorgioscia on 2012-04-14
Hiya sorry been away for a couple of days!

Ignore 'usb0' thats my android phone, tethered

Here you are...

```
££££@££££-jolicloud:~$ uname -a
Linux giorgio-jolicloud 2.6.35.10-1-jolicloud-atom #64 SMP Fri Mar 4 04:39:01 MST 2011 i686 GNU/Linux


££££@££££-jolicloud:~$ lsmod
Module                  Size  Used by
rndis_host              8616  0 
cdc_ether               7934  1 rndis_host
usbnet                 23639  2 rndis_host,cdc_ether
ppdev                   6745  0 
joydev                  7469  0 
snd_hda_codec_realtek   197416  1 
snd_hda_intel          18859  2 
snd_hda_codec          71028  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               4496  1 snd_hda_codec
snd_pcm_oss            28725  0 
snd_mixer_oss          10783  1 snd_pcm_oss
snd_pcm                58904  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
uvcvideo               46443  0 
psmouse                52052  0 
ath5k                 113912  0 
snd_timer              15323  1 snd_pcm
snd_page_alloc          6328  2 snd_hda_intel,snd_pcm
lp                      6452  0 
parport                27135  2 ppdev,lp
fbcon                  29091  72 
tileblit                1687  1 fbcon
font                    7461  1 fbcon
bitblit                 3527  1 fbcon
softcursor              1001  1 bitblit
i915                  241970  3 
drm_kms_helper         24176  1 i915
drm                   146763  3 i915,drm_kms_helper
ata_piix               18770  0 
ide_pci_generic         2306  0 
usb_storage            36226  1 
intel_agp              21761  2 i915
piix                    3936  0 
r8169                  30906  0 
i2c_algo_bit            4214  1 i915
video                  18579  1 i915
agpgart                27601  2 drm,intel_agp
output                  1671  1 video


££££@££££-jolicloud:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
usb0      no wireless extensions.


££££@££££-jolicloud:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


££££@££££-jolicloud:~$ sudo iwlist scan
[sudo] password for ££££: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

usb0      Interface doesn't support scanning.


££££@££££-jolicloud:~$ dmesg | grep ath
[    2.469754] device-mapper: multipath: version 1.1.1 loaded
[    2.469763] device-mapper: multipath round-robin: version 1.0.0 loaded
[   16.664166] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.664194] ath5k 0000:02:00.0: setting latency timer to 64
[   16.664290] ath5k 0000:02:00.0: registered as 'phy0'
[   17.234420] ath: EEPROM regdomain: 0x65
[   17.234429] ath: EEPROM indicates we should expect a direct regpair map
[   17.234441] ath: Country alpha2 being used: 00
[   17.234447] ath: Regpair used: 0x65
[   17.350011] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[88996.548736] ath5k 0000:02:00.0: preparing suspend
[88996.548740] ath5k 0000:02:00.0: __pm_runtime_resume()!
[88996.548744] ath5k 0000:02:00.0: __pm_runtime_resume() returns -11!
[88996.611360] ath5k 0000:02:00.0: suspend
[88997.100637] ath5k 0000:02:00.0: LATE suspend
[88997.558686] ath5k 0000:02:00.0: EARLY resume
[88997.558718] ath5k 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x107)
[88997.558750] ath5k 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x52100004)
[88997.558761] ath5k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[88997.558773] ath5k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[88997.563534] ath5k 0000:02:00.0: resume
[88998.376567] ath5k 0000:02:00.0: completing resume

```

---

### Post by praseodym on 2012-04-15
Deactivate the hardware encryption:

> echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
and reboot

---

### Post by giorgioscia on 2012-04-15
The only thing that I can see has changed.....


```
££££@££££-jolicloud:~$ dmesg | grep ath
[    2.470709] device-mapper: multipath: version 1.1.1 loaded
[    2.470717] device-mapper: multipath round-robin: version 1.0.0 loaded
[   16.572184] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.572211] ath5k 0000:02:00.0: setting latency timer to 64
[   16.572299] ath5k 0000:02:00.0: registered as 'phy0'
[   17.829867] ath: EEPROM regdomain: 0x65
[   17.829875] ath: EEPROM indicates we should expect a direct regpair map
[   17.829886] ath: Country alpha2 being used: 00
[   17.829892] ath: Regpair used: 0x65
[   17.843847] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
```

---

