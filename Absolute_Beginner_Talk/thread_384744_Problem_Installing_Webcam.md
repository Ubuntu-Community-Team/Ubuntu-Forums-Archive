---
title: "Problem Installing Webcam"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-03-14
A few days ago I received a **Logitech Quickcam Chat** Webcam - [Info Here]("http://www.logitech.com/index.cfm/ptdy insroducts/details/US/EN,CRID=2204,CONTENTID=11635")

Here is the lsusb info: 
> Bus 001 Device 004: ID 046d:092e Logitech, Inc.
I've already installed the spca5xx driver via getautomatix but neither kopete nor amsn are registering the webcam.

DId I do somethng wrong? Anything else that I need to do? Please help...or my girlfriend will make me switch back to windows :p (she bought me the webcam)
Thanks!

---

### Post by Jonam on 2007-03-14
Can you see that the module has loaded through the lsmod command? This is the output I get with my Quickcam Messenger using ```
lsmod | grep -i quick
``` to  search for all related modules. Output is:

```
quickcam              105672  0
videodev                9856  2 quickcam,bttv
usbcore               130820  11 quickcam,snd_usb_audio,snd_usb_lib,usblp,aiptek,usb_storage,usbhid,ehci_hcd,uhci_hcd,ohci_hcd

```

You should get something similar by replacing "quick" with "spca" in the lsmod example above.

Jonam

---

### Post by silhouette on 2007-03-14
Not to be a downer but I have not had good results with the Quickcam Chat under Linux. Some programs won't recognize the camera, others will recognize it but the image is discolored; there are few programs where it manageably works.

Still, I would try the following things:

- checking that the module is loaded as Jonam said
- compiling the driver yourself
- using the gspcav1 driver instead of spca5xx

Source code for spca5xx [here](http://mxhaard.free.fr/spca50x/Download/spca5xx-20060501.tar.gz)
Source code for gspcav1 [here](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz)

Also try spcaview, a framegrabber program that was made specifically for this driver. You can get the source [here](http://mxhaard.free.fr/spca50x/Download/spcaview-20061208.tar.gz).

---

### Post by lazyrussian on 2007-03-14
When I put in lsmod this is what it outputs....nothing about quickcam, videodev, or usbcore though.

> 
Module                  Size  Used by
battery                10756  0
ac                      5892  0
thermal                14600  0
processor              26028  1 thermal
fan                     5124  0
button                  7056  0
8139too                27136  0
ath_pci                98208  0
ndiswrapper           201744  0
snd_rtctimer            3468  0
usbhid                 42464  0
rfcomm                 38936  0
l2cap                  23300  5 rfcomm
bluetooth              48996  4 rfcomm,l2cap
ipv6                  257632  10
fglrx                 405164  0
cpufreq_userspace       4372  0
cpufreq_stats           5892  0
freq_table              4996  1 cpufreq_stats
cpufreq_powersave       2048  0
cpufreq_ondemand        6944  0
cpufreq_conservative     7200  0
video                  16644  0
tc1100_wmi              7428  0
sbs                    15776  0
sony_acpi               5516  0
pcc_acpi               13184  0
i2c_ec                  5376  1 sbs
i2c_core               22288  1 i2c_ec
hotkey                 10660  0
dev_acpi               11140  0
container               4736  0
asus_acpi              16792  0
sbp2                   23304  0
parport_pc             36132  0
lp                     11972  0
parport                37320  2 parport_pc,lp
af_packet              21768  4
wlan_scan_sta          14080  1
ath_rate_sample        13440  1
snd_hda_intel          18580  1
snd_hda_codec         163712  1 snd_hda_intel
snd_pcm_oss            46080  0
snd_pcm                80520  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          18560  1 snd_pcm_oss
snd_seq_dummy           4100  0
snd_seq_oss            34304  0
pcmcia                 38972  0
snd_seq_midi            9088  0
snd_rawmidi            25600  1 snd_seq_midi
joydev                 10304  0
tsdev                   8256  0
wlan                  212932  4 ath_pci,wlan_scan_sta,ath_rate_sample
ath_hal               191952  3 ath_pci,ath_rate_sample
sg                     35356  0
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m
idi_event
snd_timer              23172  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          8972  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi
di,snd_seq
8139cp                 22528  0
psmouse                40072  0
shpchp                 40856  0
pci_hotplug            31284  1 shpchp
snd                    55428  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm
,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9952  1 snd
snd_page_alloc         10504  2 snd_hda_intel,snd_pcm
evdev                  10496  1
ati_agp                 9612  0
agpgart                33456  2 fglrx,ati_agp
serio_raw               7300  0
pcspkr                  3072  0
rtc                    12596  1 snd_rtctimer
mii                     6016  2 8139too,8139cp
yenta_socket           27916  1
rsrc_nonstatic         14336  1 yenta_socket
pcmcia_core            42128  3 pcmcia,yenta_socket,rsrc_nonstatic
ext3                  138888  1
jbd                    55700  1 ext3
ohci1394               35248  0
ieee1394              302904  2 sbp2,ohci1394
ehci_hcd               32520  0
ohci_hcd               20740  0
usbcore               130304  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
ide_generic             1536  0
ide_cd                 32416  0
cdrom                  37792  1 ide_cd
atiixp                  6544  1
sd_mod                 21648  3
generic                 5252  0
sata_sil               10120  2
libata                 73228  1 sata_sil
scsi_mod              141320  4 sbp2,sg,sd_mod,libata
fbcon                  40480  0
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0
capability              5000  0
commoncap               7808  1 capability


---

### Post by Jonam on 2007-03-15
I see a usbcore in your printout. It is likely that the spca5xx driver that you have is not the correct one for your camera hence it is not loading. I had similar issues with my webcam as I initially had the wrong module which wouldn't load. On compiling and loading the correct module, everything worked fine.

For your type of camera, there is a solution outlined here:

[http://ubuntuforums.org/showthread.php?t=205782](http://ubuntuforums.org/showthread.php?t=205782)

See if this works for you. You might also want to look at this site:

[http://www.wifi.com.ar/english/ipcamera/WorkingDevices.html](http://www.wifi.com.ar/english/ipcamera/WorkingDevices.html)

which says that the gspca driver is more appropriate.

Jonam

---

### Post by lazyrussian on 2007-03-15
Jonam,

Thank you very much!

I used the gspca driver, unzipped it, ran ./gspca_build and it started working in Kopete!

Thanks alot!

---

### Post by cruyff888 on 2007-03-18
Hello all. I'm new to Ubuntu so any help would be appreciated. I'm also having issues with my webcam. I have a Logitech QuickCam Pro 4000. My dmesg show the following:

[17179587.556000] Linux video capture interface: v1.00
[17179587.564000] pwc Philips webcam module version 9.0.2-unofficial loaded.
[17179587.564000] pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[17179587.564000] pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[17179587.564000] pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[17179587.564000] pwc Logitech QuickCam 4000 Pro USB webcam detected.
[17179587.564000] pwc Registered as /dev/video0.
[17179587.564000] usbcore: registered new driver Philips webcam

All I get when is a gray screen with Ekiga and GYachE. 

Thanks in advance.

---

### Post by lazyrussian on 2007-03-19
It seems that your webcam is not supported by SPCA5xx or GSPCA. 

Check this site out though - the driver download is at the top - [http://www.smcc.demon.nl/webcam/](http://www.smcc.demon.nl/webcam/)

---

### Post by cruyff888 on 2007-03-23
I'll give that a shot. Much appreciated. 



thanks

---

### Post by cruyff888 on 2007-03-26
Got it working.... just downloaded the latest version of the pwc driver and installed it... very easy. Thanks again for all the help....


Ubuntu is great!!!!!!!

---

### Post by lazyrussian on 2007-03-26
> **cruyff888 said:**
> Got it working.... just downloaded the latest version of the pwc driver and installed it... very easy. Thanks again for all the help....


Ubuntu is great!!!!!!!

Hey, no problem! Glad to hear it worked out!

---

