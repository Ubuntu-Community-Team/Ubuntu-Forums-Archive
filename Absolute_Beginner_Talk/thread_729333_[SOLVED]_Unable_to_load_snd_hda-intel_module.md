---
title: "[SOLVED] Unable to load snd_hda-intel module"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by bsharp on 2008-03-19
I'm trying to get my compaq presario f700's sound working correctly with the headphone jack, and I'm following this guide:
[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda_intel%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda_intel%29)

and have compiled and installed the latest version (1.0.16) of alsa-drivers, alsa-lib, and alsa-utils, but my card's driver isn't working, because snd_hda-intel isn't loading.  When I try to manually load it, I get this error:
```
brandon@brandon-laptop:~$ sudo modprobe snd_hda-intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

this is the ouput of dmesg:
```
[  123.732000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  123.732000] snd_hda_intel: Unknown symbol snd_ctl_add
[  123.732000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  123.732000] snd_hda_intel: Unknown symbol snd_pcm_new
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_card_register
[  123.736000] snd_hda_intel: Unknown symbol snd_card_register
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_card_free
[  123.736000] snd_hda_intel: Unknown symbol snd_card_free
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  123.736000] snd_hda_intel: Unknown symbol snd_card_proc_new
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  123.736000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  123.736000] snd_hda_intel: Unknown symbol snd_ctl_new1
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_component_add
[  123.736000] snd_hda_intel: Unknown symbol snd_component_add
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_card_new
[  123.736000] snd_hda_intel: Unknown symbol snd_card_new
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  123.736000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[  123.736000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_device_new
[  123.736000] snd_hda_intel: Unknown symbol snd_device_new
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  123.736000] snd_hda_intel: Unknown symbol snd_card_disconnect
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  123.736000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  123.736000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

```

from what I can get from this, it is because of conflicting versions among alsa.  If someone knows how to correct this, please let me know.

---

### Post by (((X))) on 2008-03-19
Not just sudo, use sudo -s

---

### Post by Arthur Archnix on 2008-03-19
Mine's called snd_hda_intel  not snd_hda-intel

---

### Post by igknighted on 2008-03-19
In almost all cases, recompiling ALSA is unnecessary and counterproductive... Gusty has the newer modules backported with the 'linux-backports-modules-generic' package.  Installing this, along with entering anything specific to your sound card in the /etc/modprobe.d/alsa-base file should fix it.

---

### Post by Arthur Archnix on 2008-03-19
Second igknighted.

---

### Post by bsharp on 2008-03-19
Installing the backports did it. Thanks!

---

