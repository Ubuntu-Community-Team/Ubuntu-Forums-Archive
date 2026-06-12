---
title: "Macbook 2,1 - Completely Lost Sound"
date: 2009-10-02
forum: Apple Hardware Users
---

### Post by tablebreaker on 2009-10-02
Hey all,
I'm on Jaunty, and was having the static in the left speaker problem that other people have described. I tried following a few solutions found in the forums, but I ended up losing my sound altogether! My sound driver is supposed to be snd-hda-intel, but it's not seeing it.

I've tried to reinstall alsa as per the Ultimate Sound Problems Thread (or whatever it was called!) but archive.ubuntu.com seems to be down for synaptic.

I'm not a total newbie, so I should be able to fix this, but I just need some help! 

Thanks!

Edit: Here is the output of ```
sudo modprobe snd-hda-intel
``` after reinstalling alsa:

```
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
FATAL: Error inserting snd (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_pcm (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.28-11-generic/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.28-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

and demsg:
```
[   83.266376] snd: Unknown symbol sound_class
[   83.267329] snd_timer: Unknown symbol snd_info_register
[   83.267561] snd_timer: Unknown symbol snd_info_create_module_entry
[   83.267785] snd_timer: Unknown symbol snd_info_free_entry
[   83.267966] snd_timer: Unknown symbol __snd_printk
[   83.268070] snd_timer: Unknown symbol snd_iprintf
[   83.268180] snd_timer: Unknown symbol snd_ecards_limit
[   83.268289] snd_timer: Unknown symbol snd_unregister_device
[   83.268376] snd_timer: Unknown symbol snd_device_new
[   83.268538] snd_timer: Unknown symbol snd_register_device_for_dev

```

---

