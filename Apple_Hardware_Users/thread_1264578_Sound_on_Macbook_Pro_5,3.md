---
title: "Sound on Macbook Pro 5,3"
date: 2009-09-12
forum: Apple Hardware Users
---

### Post by viktara on 2009-09-12
Hi,

I have recently installed Ubuntu Jaunty on my Macbook Pro.

Issuing:

dmidecode -s system-product-name

tells me it's a:

MacBookPro5,3

Most things are working fine - but I have no sound.

When I originally installed Jaunty, going to the volume applet and selecting volume control did show me ALSA and OSS devices (NVIDIA).

But I had no sound.

So I followed the instructions for 5,5 here:
[http://ubuntuforums.org/showthread.php?p=7627817#post7627817](http://ubuntuforums.org/showthread.php?p=7627817#post7627817)

Which has left me in what seems to be a worse position.

Now, volume control does not list the device at all, I can just see:
Null Ouput (PulseAudio Mixer).

Some other info:

```
aplay -l

gives me:

aplay: device_list:217: no soundcards found...
```

```
lspci -v

tells me I have a:

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 15
	Memory at e7480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel
```

```
modprobe snd-hda-intel

give me:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-page-alloc.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-15-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-15-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

```

dmesg

gives me:

[  629.772945] snd: Unknown symbol unregister_sound_special
[  629.773179] snd: Unknown symbol register_sound_special_device
[  629.773746] snd: Unknown symbol sound_class
```

Jaunty looks amazing on the macbook - I just need to get the sound up and running.

It seems like I have the same sound card as the 5,5 so using the latest snapshot from alsa as per the instructions should work I guess, but it appears not.

Any help greatly appreciated!


Vik

---

### Post by viktara on 2009-09-14
After a bit of digging I realised that the 2.6.28-13 kernel had not been installed and hence the drivers would not insert.

The instructions I followed on the other thread advise:
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic

But if you have never installed 2.6.28-13 then you need to use apt-get install rather than reinstall.

So my sound is almost working now - I get sound from th headphone socket, but not the speakers.

---

### Post by amd-64 on 2009-09-14
Please note these instructions were written when 2.6.28-13 was the latest kernel. It is no longer the latest. I would just use the most up to date kernel in 

```
sudo aptitude reinstall linux-headers-2.6.28-13-generic linux-image-2.6.28-13-generic linux-restricted-modules-2.6.28-13-generic 
```

Today this happens to be 2.6.28-15, so you may want to use 15 in place of 13 in the code above.

---

### Post by viktara on 2009-09-15
> Today this happens to be 2.6.28-15, so you may want to use 15 in place of 13 in the code above.

I tried it with 2.6.28-15 first - but it would not insert the module and I was left with no alsa device.

---

### Post by amd-64 on 2009-09-15
I am not sure why it would not insert the module. These kernels are not that different anyways. I used the method here [http://ubuntuforums.org/showpost.php?p=7834207&postcount=39 ]("http://ubuntuforums.org/showpost.php?p=7834207&postcount=39")
on a Macbookpro 5,3 and it works perfectly. The difference is this is the stable alsa driver.

If you are getting sound on the headphones and not the speakers. Make sure pavucontrol is installed and check that none of the outputs are muted.  Also check for muted channels in alsamixer.

---

### Post by viktara on 2009-09-15
> I am not sure why it would not insert the module. These kernels are not that different anyways. I used the method here [http://ubuntuforums.org/showpost.php?p=7834207&postcount=39 ]("http://ubuntuforums.org/showpost.php?p=7834207&postcount=39")
on a Macbookpro 5,3 and it works perfectly. The difference is this is the stable alsa driver.

I tried it again from the top - I was already using the stable snapshot. 

For 2.6.28-15 the module doesn't load as per my post, and I'm left without any alsa device.

For 2.6.28-13 everything loads fine, but I still only have sound from the headphone socket.

> If you are getting sound on the headphones and not the speakers. Make sure pavucontrol is installed and check that none of the outputs are muted.  Also check for muted channels in alsamixer.

In my previous attempts I had not installed pavucontrol.

I've installed it, but none of the outputs are muted.

For 'device' under default mixer tracks, mine says:
"Playback: HDA NVidia - Cirrus Analog (Pulse Audio..."

In alsamixer the only muted channel was surround which I unmuted.

In the volume control applet, front speaker was muted - I unmuted that.

But still only sound from the headphone socket and not the speakers.

Thanks a lot for your help so far, any further ideas?

BTW here are my modules for the running kernel:

```
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-ca0110.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-si3054.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-cirrus.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-conexant.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-intelhdmi.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-cmedia.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-via.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-idt.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-analog.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-atihdmi.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-nvhdmi.ko
/lib/modules/2.6.28-13-generic/kernel/sound/pci/hda/snd-hda-codec-realtek.ko
/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-timer.ko
/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-hwdep.ko
/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-page-alloc.ko
/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd-pcm.ko
/lib/modules/2.6.28-13-generic/kernel/sound/acore/snd.ko
/lib/modules/2.6.28-13-generic/kernel/sound/acore/seq/snd-seq-device.ko
```

---

### Post by amd-64 on 2009-09-15
Ok. I think you are almost there. 

Here are my sound preferences. I don't know if this could be the cause

Sound events
           Sound Playback: autodetect

Music and movies
           Sound Playback: autodetect

Audio conferencing
           Sound Playback: HDA NVidia - Cirrus Analog (ALSA)
           Sound Capture: PulseAudio Sound Server

Default Mixer Tracks:
           Device:  Playback: HDA NVidia (PulseAudio Mixer)


Another question. What do you get when you run speaker-test.

---

### Post by viktara on 2009-09-16
OK - I have sent my sound preferences to the same:
Sound events
Sound Playback: autodetect

Music and movies
Sound Playback: autodetect

Audio conferencing
Sound Playback: HDA NVidia - Cirrus Analog (ALSA)
Sound Capture: PulseAudio Sound Server

Default Mixer Tracks:
Device: Playback: HDA NVidia - Cirrus Analog (PulseAudio Mixer)

Still no noise from the speakers.

speaker-test gives me:

speaker-test 1.0.18

```
Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 2048 to 8192
Period size range from 1024 to 1024
Using max buffer size 8192
Periods = 4
was set period_size = 1024
was set buffer_size = 8192
 0 - Front Left
Time per period = 2.836565
 0 - Front Left
Time per period = 2.986548
 0 - Front Left
Time per period = 2.986600
 0 - Front Left
Time per period = 2.986576
 0 - Front Left
```

It continues like that until I ctrl c


Thanks for all your help on this :)


Vik

---

### Post by viktara on 2009-09-22
Is anyone else facing this issue - ie only sound from the headphone socket?

Regards


Vik

---

