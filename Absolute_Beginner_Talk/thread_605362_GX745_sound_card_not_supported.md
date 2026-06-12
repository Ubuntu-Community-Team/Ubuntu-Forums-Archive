---
title: "GX745 sound card not supported?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Masateru KUWATA on 2007-11-06
Dear

I have recntly installed Ubuntu7.10 on DELL Optiplex GX745. Everything worked fine except sound card.

My DELL desktop has a SoundMAX Integrated Digital HD Audio (working with WindowsXP). However, when  PC was booted from ubuntu7.10 DesktopCD, it did not make a sound. After the installation on Hard Disk, the sound was still unavailable.

I have looked at sound manager -- it seems like that the sound card was recognized and HDA Intel (Alsa mixer) was chosen as a driver. The mute was deselected and the volume level was highest -- but still no sound.

How can I go ahead to more detailed analysis?

Any suggestions and advice would be appreciated.
Thanks in advance!:(

---

### Post by Masateru KUWATA on 2007-11-07
Additional Information:

I have checked with Alsamixer from the terminal window. It showed "headphone"  volume was 90%, but I cannot find "Master" volume.

In the past experience with other PC (e.g. GX520), "Master" was always displayed in sound manager. Therefore the problem seems like that Ubuntu7.10 could not detect "Master" in GX745 sound card (built-in).

Does anyone have same or similar problem?

Best regards


> **Masateru KUWATA said:**
> Dear

I have recntly installed Ubuntu7.10 on DELL Optiplex GX745. Everything worked fine except sound card.

My DELL desktop has a SoundMAX Integrated Digital HD Audio (working with WindowsXP). However, when  PC was booted from ubuntu7.10 DesktopCD, it did not make a sound. After the installation on Hard Disk, the sound was still unavailable.

I have looked at sound manager -- it seems like that the sound card was recognized and HDA Intel (Alsa mixer) was chosen as a driver. The mute was deselected and the volume level was highest -- but still no sound.

How can I go ahead to more detailed analysis?

Any suggestions and advice would be appreciated.
Thanks in advance!:(

---

### Post by Masateru KUWATA on 2007-11-07
I confirmed that Headphone works!

The only problem is why "Master" is not detected by Ubuntu7.10.

It was detected as Analog Devices AD1983 by alsamixer -- WindowsXP xomes with SoundMAX Integrated Digital HD Audio Driver and works just fine.

Is there any new driver that I need to install?:confused:

regards:

> **Masateru KUWATA said:**
> Additional Information:

I have checked with Alsamixer from the terminal window. It showed "headphone"  volume was 90%, but I cannot find "Master" volume.

In the past experience with other PC (e.g. GX520), "Master" was always displayed in sound manager. Therefore the problem seems like that Ubuntu7.10 could not detect "Master" in GX745 sound card (built-in).

Does anyone have same or similar problem?

Best regards

---

