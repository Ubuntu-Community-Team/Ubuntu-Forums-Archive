---
title: "Ubuntu+nVidia Riva TNT2"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by happyweb on 2006-08-12
i have a nVidia Riva Tnt2 32 MB graphic card on my machine
,will ubuntu automatically detect the driver or would i hvae to install the driver manually, i mean to say when i install ubuntu will get get installed sucessfully..

---

### Post by Perfect Storm on 2006-08-12
When you successfully installed Ubuntu it uses the Open Source Driver called nv, so yes.
But if you want good 3D acc. you need to install Nvidia's driver. You do it like this:

Go **applications** tab ---> **Accessories** ---> **terminal**
and you type in the terminal;

```
 sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-glx-legacy
sudo nvidia-glx-config enable
```

reboot.

nvidia-glx-legacy driver is for older cards.
nvidia-glx is for newer cards.

If it fails to start up when you reboot, you'll end in command line. Don't worry. It'll ask for your username and password. Then type:
```
sudo nano /etc/X11/xorg.conf
```
(remember that linux is case sensitive).

find the 
```
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]" (this my card name, your will be diffrent)
    Driver         "nv"
EndSection

```

and change "nv" to "nvidia"
save and exit (ctrl + o cttrl + x)
then
```
startx
```

---

### Post by happyweb on 2006-08-12
Thank a ton AI ,
for the prompt help
i will try the commands as described by you...

thanks again
cheers

---

### Post by jbtito03 on 2006-11-01
Hi guys..

just switched from fedora to ubuntu. Have to say its quite a piece of a distro.....

Well... everything works fine, just the 3d acc is not working at all. 

I am using the legacy drivers, xorg.conf has the "nvidia" driver string and at reboot i see the nvidia logo. But, for example, the screensavers don work at all... 

In one forum thread i read something about nvidifb... so i modprobed it.. and now my lsmod says: 

Module                  Size  Used by
nvidiafb               58012  0 
i2c_algo_bit            9480  1 nvidiafb
nls_utf8                2304  1 
nls_cp437               6016  1 
vfat                   13440  1 
fat                    54556  1 vfat
binfmt_misc            11784  1 
nfsd                  231844  13 
exportfs                6016  1 nfsd
lockd                  65800  2 nfsd
sunrpc                160188  8 nfsd,lockd
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
hotkey                 10660  0 
dev_acpi               11140  0 
button                  7056  0 
battery                10756  0 
container               4736  0 
ac                      5892  0 
asus_acpi              16792  0 
sg                     35356  0 
sd_mod                 21648  2 
ipv6                  257632  21 
dm_mod                 60088  4 
md_mod                 78740  0 
lp                     11972  0 
nvidia               3931148  8 
tsdev                   8256  0 
usb_storage            73408  1 
scsi_mod              141320  3 sg,sd_mod,usb_storage
af_packet              21768  2 
snd_via82xx            28696  1 
gameport               15368  1 snd_via82xx
snd_ac97_codec         96672  1 snd_via82xx
snd_ac97_bus            2432  1 snd_ac97_codec
snd_mpu401_uart         8704  1 snd_via82xx
snd_pcm_oss            46080  0 
snd_pcm                80520  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10504  2 snd_via82xx,snd_pcm
snd_mixer_oss          18560  1 snd_pcm_oss
snd_seq_dummy           4100  0 
snd_seq_oss            34304  0 
snd_seq_midi            9088  0 
snd_rawmidi            25600  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23172  2 snd_pcm,snd_seq
snd_seq_device          8972  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
libusual               15632  1 usb_storage
parport_pc             36132  1 
parport                37320  2 lp,parport_pc
i2c_viapro              8980  0 
snd                    55428  13 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                40072  0 
shpchp                 40856  0 
pci_hotplug            31284  1 shpchp
usbhid                 42464  0 
i2c_core               22288  4 nvidiafb,i2c_algo_bit,i2c_ec,i2c_viapro
via_agp                10368  1 
agpgart                33456  2 nvidia,via_agp
soundcore               9952  1 snd
rtc                    12596  0 
serio_raw               7300  0 
evdev                  10496  1 
pcspkr                  3072  0 
floppy                 60676  0 
via_rhine              23940  0 
mii                     6016  1 via_rhine
ext3                  138632  2 
jbd                    55700  1 ext3
ehci_hcd               32520  0 
uhci_hcd               23176  0 
usbcore               130304  6 usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd
ide_generic             1536  0 
ide_disk               17664  4 
ide_cd                 32416  1 
cdrom                  37792  1 ide_cd
via82cxxx               9604  0 [permanent]
generic                 4868  0 
thermal                14600  0 
processor              26028  1 thermal
fan                     5124  0 
fbcon                  40480  0 
tileblit                2944  1 fbcon
font                    8448  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2432  1 bitblit
vesafb                  8348  0 
capability              5000  0 
commoncap               7808  1 capability

but still... no 3d....

can someone help... pleaseee....

Distro... edgy elf 6.10

bye

---

### Post by happyweb on 2006-11-25
> **Artificial Intelligence said:**
> When you successfully installed Ubuntu it uses the Open Source Driver called nv, so yes.
But if you want good 3D acc. you need to install Nvidia's driver. You do it like this:

Go **applications** tab ---> **Accessories** ---> **terminal**
and you type in the terminal;

```
 sudo apt-get update && sudo apt-get upgrade
sudo apt-get install nvidia-glx-legacy
sudo nvidia-glx-config enable
```

reboot.

nvidia-glx-legacy driver is for older cards.
nvidia-glx is for newer cards.

If it fails to start up when you reboot, you'll end in command line. Don't worry. It'll ask for your username and password. Then type:
```
sudo nano /etc/X11/xorg.conf
```
(remember that linux is case sensitive).

find the 
```
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]" (this my card name, your will be diffrent)
    Driver         "nv"
EndSection

```

and change "nv" to "nvidia"
save and exit (ctrl + o cttrl + x)
then
```
startx
```

hi AI,
i did as described by you
 however after reboot i am getting a white and grey screen and nothing happens after that.
then is restarted ubuntu 6.10 in recovery mode and in my "xorg.conf"
i saw under Driver section it was written "nvidia",
now i changed this to "nv" and after this change i was able to get my login back
and was able to use ubuntu.

now after login i typed in the "terminal"

this command
"lspci -n | grep 0300"

and got this:
01:00.0 0300: 10de:002d (rev 15)

now please help
as i think that the nvidia drivers are still not installed correctly and it should have shown "3d" and it is showing only "2d"

My system configuration is:
intel 845 HVWN motherboard
with intel pentium IV , 1.7 Ghz
512 SD RAM
nvidia riva tnt2 32 mb model 64 / model 64 pro.
 

thanks in advance
looking forward to hearing from you soon

---

