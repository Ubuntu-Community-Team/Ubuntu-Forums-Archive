---
title: "Karmic running smoothly on imac 7,1 aluminum 20&quot; sound wifi wlan video working fully"
date: 2010-02-08
forum: Apple Hardware Users
---

### Post by magic-neophyte on 2010-02-08
I have Karmic Koala 9.10 working (near) perfectly on my iMac7,1, as identified by 

```
sudo dmidecode -s system-product-name
```

NOTE: See below for Lucid 10.04 update to these instructions

IMPORTANT: You need to complete the installation procedure while connected to internet via the WIRED network. Then you can enable the wireless by installing the restricted drivers, after the install is complete. Also the fglrx ATI Video driver is effortlessly installed via Menu > System > Administration > Hardware Drivers 

The sound card gave me some trouble, as it is an Intel HDA Model, reported as 'Codec: Realtek ALC889A' by 

```
cat /proc/asound/card0/codec#0 | grep Codec
```


It shows up in lspci as:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

It sounded rather tinny at first, when I tried mbp3 and other model names. Then I added the following line to /etc/modprobe.d/alsa-base.conf :

```
options snd-hda-intel model=mb31 power_save=10 power_save_controller=N
```

After reboot, my sound is full and can be put much louder than before. Jack detection works. Some people might have to leave out the power saving options. See below. 

dmesg reports: 

```

[   12.060481] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   12.060508] HDA Intel 0000:00:1b.0: setting latency timer to 64

```

Sources consulted are mostly the kernel documentation ( Enter into the terminal: sudo apt-get install linux-doc 

The relevant info can be found in HD-Audio-Models.txt.gz and HD-Audio.txt.gz in /usr/share/doc/linux-doc/sound/alsa )

---

### Post by magic-neophyte on 2010-06-30
Update: On Ubuntu Lucid 10.04, the imac 7,1 does not produce sound out of the box either.

I set the model to mb31 as above, but it did not work after reboot.

Then I enabled imac24 as model, rebooted and fiddled with the sound levels. The sound was tinny. 

Switching back to mb31 gave me full and rich sound. Recording has not been tested yet. The movie sound can be set to above 100% for a nice theater sound from the aluminum frame of the mac.

I also left out the powersaving options, resulting in the line 

options snd-hda-intel model=mb31

as the last line of /etc/modprobe.d/alsa-base.conf

---

