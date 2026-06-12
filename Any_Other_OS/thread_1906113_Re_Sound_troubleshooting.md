---
title: "Re: Sound troubleshooting"
date: 2012-01-08
forum: Any Other OS
---

### Post by Osmodivs on 2012-01-08
Hello.
I have_ LinuxMint 11 64bits_. My Intel Classic series Motherboard (**EG35EC**) onboard sound is not working.

I have tried this thread:
[URL="http://ubuntuforums.org/showthread.php?t=205449"]http://ubuntuforums.org/showthread.php?t=205449
[/URL]
And after all the steps, I got this:

```
sudo modprobe snd-hda-intel 
FATAL: Error inserting snd (/lib/modules/2.6.38-13-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.38-13-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.38-13-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.38-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```And now they say those instructions are obsolete.
But the wird part is, after un installing and re installing header modules and ALSA stuff, I still can't open alsamixer:
 alsamixer
```
cannot open mixer: No such file or directory
```Can't detect my onboard sound:
```
aplay -l
aplay: device_list:240: no soundcards found...
```But:
```
lspci -v | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```And:
```
aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
```I do not have a /proc/asound file.
```
cat /proc/asound/car*/co* |  grep Codec
cat: /proc/asound/car*/co*: No such file or directory
```I even added this line:
```
options snd-hda-intel model=-snd-hda-intel
```to /etc/modprobe.d/alsa-base.conf as you can see here: [http://pastebin.com/LidUkLWW](http://pastebin.com/LidUkLWW)
 And still nothing!

How can I fix this issue?
I need onboard sound.
Thank you.

---

### Post by howefield on 2012-01-08
Post spliced off to a new thread, placed in the "Other OS/Distro Talk" forum and prefixed appropriately.

---

