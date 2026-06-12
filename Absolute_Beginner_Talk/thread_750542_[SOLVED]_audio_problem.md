---
title: "[SOLVED] audio problem"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by azkehmm on 2008-04-09
Yes... another one of those.

I've tried following this guide [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), untill the point where I've installed the alsa-drivers, alsa-lib and alsa- utils. Rebooted and still no sound. 
 i've tried the dmesg and the snd_ strings look like this:
```

[   15.788000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   15.788000] snd_hda_intel: Unknown symbol snd_ctl_add
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_new
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   15.788000] snd_hda_intel: Unknown symbol snd_card_register
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   15.788000] snd_hda_intel: Unknown symbol snd_card_free
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   15.788000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   15.788000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   15.788000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   15.788000] snd_hda_intel: Unknown symbol snd_component_add
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   15.788000] snd_hda_intel: Unknown symbol snd_card_new
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   15.788000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   15.788000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   15.788000] snd_hda_intel: Unknown symbol snd_device_new
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   15.788000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   15.788000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   15.788000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step


```

I'm by no means an expert, but I'm pretty sure something is wrong, I just can't figure out what :)
Please help me, and thank you very much in advance.

---

### Post by Crafty Kisses on 2008-04-09
Can you post the following output:
```
lspci
```

---

### Post by jettjunker on 2008-04-10
The troubleshooting section at the bottom of that very page says what to do for those errors.  Have you tried copying those files?

---

### Post by azkehmm on 2008-04-19
> 
ubuntu default snd-hda-intel.ko location: /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko 

alsa 1.0.15's installation location: /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko 

so copy /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko to /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko . 

and put the modules/* in alsa's compile directory into /lib/modules/.../kernel/sound, you can use "find" to get their location. snd-hda-intel.ko snd-hwdep.ko snd.ko snd-mixer-oss.ko snd-page-alloc.ko snd-pcm.ko snd-pcm-oss.ko snd-rtctimer.ko snd-seq-device.ko snd-seq.ko snd-seq-midi-event.ko snd-seq-oss.ko snd-timer.ko 

then, depmod -a 

reboot, try again. 



Tried it right untill it want me to move files from alsa's compile directory, but I can't bloody find it :). Tried to use "find" on each of the files, but it comes up with, "no such file or directory found."
 Can you guys help me find it?:confused:

EDIT:
Turned out copying the first file, then compiling the alsa stuff again, was enough. Dunno why, but I have sound now :) Thanks for the help, guys :)

---

