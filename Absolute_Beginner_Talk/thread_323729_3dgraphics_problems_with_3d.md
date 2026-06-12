---
title: "3dgraphics problems with 3d"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by fnordportland on 2006-12-22
im trying to get 3d aceleration to work with my card lspcia says its a: 1:00.0 VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01)


not sure what to do form here but i thought this mght help:

$ lsmod | grep via
snd_via82xx_modem      16648  1
snd_via82xx            30360  1
gameport               17160  1 snd_via82xx
snd_ac97_codec         97696  2 snd_via82xx_modem,snd_via82xx
snd_pcm                84612  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_mpu401_uart        10240  1 snd_via82xx
via_agp                11264  1
agpgart                34888  1 via_agp
i2c_viapro              9876  0
i2c_core               23424  2 i2c_ec,i2c_viapro
snd                    58372  16 snd_via82xx_modem,snd_seq_oss,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_mpu401_uart,snd_timer,snd_rawmidi,snd_seq_device
snd_page_alloc         11400  3 snd_via82xx_modem,snd_via82xx,snd_pcm
via_rhine              26116  0
mii                     6912  1 via_rhine
via82cxxx              10500  0 [permanent]

---

### Post by zgornel on 2006-12-22
Try setting in /etc/X11/xorg.conf, under Section "Device" instead of Driver "vesa", Driver "unichrome". If you don't have direct rendering after a X restart, try: dpkg-reconfigure xserver-xorg

---

### Post by fnordportland on 2007-01-12
tryed that i tried ,unichrome,vesa,and a few others no luck xorg just chrashed

---

### Post by DaneDog on 2007-01-19
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

