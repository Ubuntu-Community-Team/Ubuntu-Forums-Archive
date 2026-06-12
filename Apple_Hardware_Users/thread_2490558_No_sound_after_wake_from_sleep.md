---
title: "No sound after wake from sleep"
date: 2023-09-07
forum: Apple Hardware Users
---

### Post by DigiAngel on 2023-09-07
Hey all.  Topic really...iMac 2019 21.5 4K.  Had to compile a kernel mod to get sound to work, but after the system wakes from sleep I have no sound at all.  I've tried restarting pulse audio, but to no avail.  Anyone have any idea on what to try next?  Thank you.

---

### Post by DigiAngel on 2023-09-07
After wake from sleep everything looks normal...can play a wav file with aplay and the card shows up in settings, but there's just no sound.  I've tried unloading all the mods, but when I reload them all, all I see is Dummy Output in sound settings.

---

### Post by DigiAngel on 2023-09-07
Here's the mods on boot:

```
snd_seq_midi           20480  0
snd_sof_pci_intel_cnl    16384  0
ac97_bus               16384  1 snd_soc_core
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_compress           28672  1 snd_soc_core
snd_hda_codec_cs8409   172032  1
snd_hda_codec_generic   118784  1 snd_hda_codec_cs8409
snd_hda_codec_hdmi     94208  1
snd_hwdep              20480  1 snd_hda_codec
snd_pcm_dmaengine      20480  1 snd_soc_core
snd_rawmidi            53248  1 snd_seq_midi
snd_seq_midi_event     16384  1 snd_seq_midi
snd_soc_hdac_hda       24576  1 snd_sof_intel_hda_common
snd_sof_intel_hda      24576  1 snd_sof_intel_hda_common
snd_sof_intel_hda_common   188416  1 snd_sof_pci_intel_cnl
snd_sof_utils          20480  1 snd_sof
snd_sof_xtensa_dsp     16384  1 snd_sof_intel_hda_common
soundcore              16384  1 snd
soundwire_cadence      40960  1 soundwire_intel
soundwire_generic_allocation    16384  1 soundwire_intel
soundwire_intel        57344  1 snd_sof_intel_hda_common
snd_intel_sdw_acpi     20480  2 snd_sof_intel_hda_common,snd_intel_dspcfg
snd_seq                94208  2 snd_seq_midi,snd_seq_midi_event
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_sof_intel_hda_common
snd_soc_acpi_intel_match    77824  2 snd_sof_intel_hda_common,snd_sof_pci_intel_cnl
snd_sof_pci            24576  2 snd_sof_intel_hda_common,snd_sof_pci_intel_cnl
snd_timer              49152  2 snd_seq,snd_pcm
snd_hda_ext_core       36864  3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_intel_dspcfg       36864  3 snd_hda_intel,snd_sof,snd_sof_intel_hda_common
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_sof               311296  3 snd_sof_pci,snd_sof_intel_hda_common,snd_sof_intel_hda
soundwire_bus         110592  3 soundwire_intel,soundwire_generic_allocation,soundwire_cadence
snd_hda_intel          61440  4
snd_soc_core          417792  4 soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda
snd_hda_codec         204800  6 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_codec_cs8409,snd_hda_intel,snd_soc_hdac_hda,snd_sof_intel_hda
snd_hda_core          135168  9 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_codec_cs8409,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_pcm               192512  11 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_sof_utils,snd_hda_core,snd_pcm_dmaengine
snd                   135168  22 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_codec_cs8409,snd_hda_intel,snd_hda_codec,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
```

Here's the mods after reloading them:

```
snd_hda_codec_cs8409   172032  0
snd_seq_midi           20480  0
snd_sof_pci_intel_cnl    16384  0
ac97_bus               16384  1 snd_soc_core
ledtrig_audio          16384  1 snd_hda_codec_generic
snd_compress           28672  1 snd_soc_core
snd_hda_codec_hdmi     94208  1
snd_hda_intel          61440  1
snd_hwdep              20480  1 snd_hda_codec
snd_pcm_dmaengine      20480  1 snd_soc_core
snd_rawmidi            53248  1 snd_seq_midi
snd_seq_midi_event     16384  1 snd_seq_midi
snd_soc_hdac_hda       24576  1 snd_sof_intel_hda_common
snd_sof_intel_hda      24576  1 snd_sof_intel_hda_common
snd_sof_intel_hda_common   188416  1 snd_sof_pci_intel_cnl
snd_sof_utils          20480  1 snd_sof
snd_sof_xtensa_dsp     16384  1 snd_sof_intel_hda_common
soundcore              16384  1 snd
soundwire_cadence      40960  1 soundwire_intel
soundwire_generic_allocation    16384  1 soundwire_intel
soundwire_intel        57344  1 snd_sof_intel_hda_common
snd_hda_codec_generic   118784  2 snd_hda_codec_cs8409
snd_intel_sdw_acpi     20480  2 snd_sof_intel_hda_common,snd_intel_dspcfg
snd_seq                94208  2 snd_seq_midi,snd_seq_midi_event
snd_soc_acpi           16384  2 snd_soc_acpi_intel_match,snd_sof_intel_hda_common
snd_soc_acpi_intel_match    77824  2 snd_sof_intel_hda_common,snd_sof_pci_intel_cnl
snd_sof_pci            24576  2 snd_sof_intel_hda_common,snd_sof_pci_intel_cnl
snd_timer              49152  2 snd_seq,snd_pcm
snd_hda_ext_core       36864  3 snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_intel_dspcfg       36864  3 snd_hda_intel,snd_sof,snd_sof_intel_hda_common
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_sof               311296  3 snd_sof_pci,snd_sof_intel_hda_common,snd_sof_intel_hda
soundwire_bus         110592  3 soundwire_intel,soundwire_generic_allocation,soundwire_cadence
snd_soc_core          417792  4 soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_soc_hdac_hda
snd_hda_codec         204800  6 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_codec_cs8409,snd_hda_intel,snd_soc_hdac_hda,snd_sof_intel_hda
snd_hda_core          135168  9 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_codec_cs8409,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_sof_intel_hda
snd_pcm               192512  11 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_sof_utils,snd_hda_core,snd_pcm_dmaengine
snd                   135168  16 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_codec_cs8409,snd_hda_intel,snd_hda_codec,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi
```

It's obvious something is funky, but I cannot seem to find out why the mod that I need, snd_hda_codec_cs8409, after unloading/reloading isn't in use.  Aplay -l before and after:


```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CS8409/CS42L83 Analog [CS8409/CS42L83 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


**** List of PLAYBACK Hardware Devices ****
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

