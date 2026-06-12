---
title: "Problemes de Só [II]"
date: 2007-05-16
forum: Catalan Team
---

### Post by prostata on 2007-05-16
Us faig un copy-paste de les sentencies de terminal i el seu resultat perquè tingueu una idea més clara del meu probleme....gràcies


josep@josep-desktop:~$ lspci |grep audio
00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
josep@josep-desktop:~$ asoundconf list
Names of available sound cards:
AudioPCI
UART
U0x46d0x8da
josep@josep-desktop:~$ cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xd800, irq 21
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5
 2 [U0x46d0x8da    ]: USB-Audio - USB Device 0x46d:0x8da
                      USB Device 0x46d:0x8da at usb-0000:00:03.0-3, full speed
josep@josep-desktop:~$ lsmod |grep snd
snd_usb_audio          79744  0 
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_ens1371            27552  1 
snd_ac97_codec         98336  1 snd_ens1371
ac97_bus                3200  1 snd_ac97_codec
snd_mpu401              9256  0 
snd_mpu401_uart         9472  1 snd_mpu401
snd_pcm_oss            44544  0 
snd_pcm                79876  4 snd_usb_audio,snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  4 snd_usb_lib,snd_ens1371,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
gameport               16520  2 snd_ens1371,analog
snd                    54020  16 snd_usb_audio,snd_hwdep,snd_ens1371,snd_ac97_codec,snd_mpu401,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  1 snd_pcm
usbcore               134280  8 snd_usb_audio,snd_usb_lib,xpad,usbhid,gspca,ehci_hcd,ohci_hcd
josep@josep-desktop:~$ alsamixer

josep@josep-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
josep@josep-desktop:~$

---

