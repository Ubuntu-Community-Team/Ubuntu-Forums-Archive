---
title: "Webcam"
date: 2010-09-10
forum: Catalan Team
---

### Post by Josep Maria on 2010-09-10
Bona nit:
Em podeu aconsellar una Webcam que funcioni bé amb la 10.04 Lucid Lynx?

---

### Post by wgarcia on 2010-09-11
En aquesta pàgina:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

tens enllaços a informes sobre compatibilitat de les webcam ordenats per marques.

---

### Post by Josep Maria on 2010-09-11
Gràcies.
Tinc una Webcam Philips spc230nc que no hi ha manera de fer anar, i només per això haig de tenir una partició de Xp al meu ordinador.
Per això vull canviar la càmera.

---

### Post by wgarcia on 2010-09-13
D'acord amb la pàgina que t'he passat aquesta càmera que menciones està suportada i funciona bé. Tenint la càmera endollada, pots adjuntar en un fitxer de text el resultat d'entrar en una terminal les comandes següents:

lsusb

lsmod

Una altra pregunta: quines proves has fet per veure si et funciona la càmera?

---

### Post by Josep Maria on 2010-09-15
Gràcies wgarcia.
Em surt això: 

duipkibi@duipkibi-desktop:~$ lsusb 
Bus 005 Device 003: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter 
Bus 005 Device 002: ID 093a:262c Pixart Imaging, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 04b8:012d Seiko Epson Corp. Perfection V10/V100 (GT-S600/F650) 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
duipkibi@duipkibi-desktop:~$ 
duipkibi@duipkibi-desktop:~$ 
duipkibi@duipkibi-desktop:~$ lsmod 
Module                  Size  Used by 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203374  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel 
snd_pcm_oss            35308  0 
snd_usb_audio          75765  3 
snd_mixer_oss          13746  1 snd_pcm_oss 
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
snd_usb_lib            15801  1 snd_usb_audio 
snd_hwdep               5412  2 snd_hda_codec,snd_usb_audio 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              19098  2 snd_pcm,snd_seq 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    54148  23 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_usb_audio,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
usbhid                 36110  0 
parport_pc             25962  1 
nvidia               7087672  34 
intel_agp              24119  0 
hid                    67032  1 usbhid 
gspca_pac7311           8986  0 
soundcore               6620  1 snd 
lp                      7060  0 
gspca_main             21199  1 gspca_pac7311 
videodev               34361  1 gspca_main 
v4l1_compat            13251  1 videodev 
psmouse                63245  0 
serio_raw               3978  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb 
agpgart                31724  2 nvidia,intel_agp 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
parport                32635  3 ppdev,parport_pc,lp 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394 
e100                   28211  0 
mii                     4381  1 e100 
floppy                 53016  0 
duipkibi@duipkibi-desktop:~$

---

