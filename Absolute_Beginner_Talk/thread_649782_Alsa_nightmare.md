---
title: "Alsa nightmare"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by viniciuscarvalho on 2007-12-25
Hello there! I'm using the 7.10 distro, and recently I've updated to the new kernel version 2.6.22-14. Well, after that sound stop working again. I have a piece of crap acer travelmate which sound card does not work with ubuntu and alsa. It took me over 4 hours to get it working, and after all that lost time ( I've lost so many hours with this laptop and ubuntu), now after installing the new kernel, the problems persists. Do I need to reinstall the drivers?

Regards

---

### Post by TidusBlade on 2007-12-25
I just rid of my ALSA/OSS problem, so I my experience you might want to try installing them again :( If you cant do it with ALSA, maybe try out OSS? I hate it but it's better than no sound at all. Followed [this](http://tldp.org/HOWTO/Alsa-sound.html#toc4) guide for another computer and it worked flawlessly... Good luck ;)

---

### Post by viniciuscarvalho on 2007-12-26
Well I still got no success. I've downloaded the latest version of alsa 1.0.15, but this one I can't even configure:

```

configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."

```

So I tried 1.0.14rc4. I've configured it with --with-cards=hda-intel, then make ... make install. After that I've used modprobe snd_hda_intel well, still nothing. Tried to update the etc/modules with the entry: snd_hda_intel model=ACER still nothing.

here's an output of my lsmod (just getting the snd entries...)

```

snd_hda_intel         244760  1 
snd_pcm_oss            44800  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            35456  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54256  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
snd                    56580  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm


```

which I must admit I understand nothing on it :(

also, here's a few lines of my dmsg output regarding sound issues.

```

[   15.589015] PnPBIOS: Disabled by ACPI PNP
[   15.589106] PCI: Using ACPI for IRQ routing
[   15.589159] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.589235] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   15.589293] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   15.589351] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[   15.589409] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   15.589467] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   15.589525] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[   15.589583] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   15.589640] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   15.589698] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[   14.968000] ALSA /home/vinicius/alsa-driver-1.0.14rc4/pci/hda/../../alsa-kernel/pci/hda/patch_si3054.c:245: si3054: cannot initialize. EXT MID = 0000
[   16.076000] ALSA /home/vinicius/alsa-driver-1.0.14rc4/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...

```

now, what really makes me thing something is really wrong : (messages)
```

Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_ctl_add
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_card_register
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_card_register
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_card_free
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_card_free
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_card_proc_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_ctl_find_id
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_verbose_printk
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_ctl_new1
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_component_add
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_component_add
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_card_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_card_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_hwdep_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_hwdep_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_device_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_device_new
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_card_disconnect
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
Dec 25 16:50:48 cybertron kernel: [   15.772000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

```

Anyone could help me out?

Regards

---

