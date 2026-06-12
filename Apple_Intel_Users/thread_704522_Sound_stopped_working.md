---
title: "Sound stopped working"
date: 2008-02-22
forum: Apple Intel Users
---

### Post by ward83 on 2008-02-22
After trying (unsuccessfully) to get XGL to work on my system, my sound card has stopped working. I'm not sure what I did to break it, but it was working fine before. The volume icon in the tray has a red X on it, and when I click it, I get "No volume control GStreamer plugins and/or devices found". The system is a 20" iMac Intel, the non-aluminum one, running 7.10.

My sound card does show up in lspci:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Sigmatel Unknown device 7680
        Flags: fast devsel, IRQ 21
        Memory at 88500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

However, I found this in dmesg:
```

[   17.080000] HDA Intel: probe of 0000:00:1b.0 failed with error -16

```

Output of 'alsamixer'
```

alsamixer: function snd_ctl_open failed for default: No such device

```

Output of 'modinfo snd_hda_intel':
```

filename:       /lib/modules/2.6.22-14-generic/updates/sound/pci/hda/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     7C05112D0C9214E90DF6E16
alias:          pci:v000010DEd00000777sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000776sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000775sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000774sv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FDsv*sd*bc*sc*i*
alias:          pci:v000010DEd000007FCsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Csv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd,snd-hwdep,snd
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           power_save:Automatic power-saving timeout (in second, 0 = disable). (int)
parm:           index:Index value for Intel HD audio interface. (int)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           model:Use the given board model. (charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           power_save_controller:Reset controller in power save mode. (bool)
parm:           enable:bool

```


Any help is greatly appreciated, I'm totally stuck on this one.

---

### Post by cyberdork33 on 2008-02-22
> **ward83 said:**
> After trying (unsuccessfully) to get XGL to work on my system, my sound card has stopped working. I'm not sure what I did to break it, but it was working fine before.
Just FYI, XGL isn't needed anymore with newer ATI drivers, use Envy to install them.

Your sound device is not being created for some reason, which might be a kernel module problem, though how you messed the sound system up by trying to install XGL I don't know... Were you following a guide or something? That might help figure out what may have happened.

Check 'lsmod' for the snd modules.

---

### Post by ward83 on 2008-02-22
I had originally tried using the restricted drivers manager, which totally broke my xorg.conf. After several hours of trying different things, and following different guides, I got it working again. To be honest, I tried so many things, and followed so many guides, I lost track of what all was changed.

this is the output of 'lsmod | grep snd'
```

snd_hda_intel         291488  0 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54788  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

```

---

### Post by cyberdork33 on 2008-02-22
Well, unfortunately it looks like modules are loading ok, but that line in dmesg is really your only clue. It is like your audio device isn't responding.

I would suggest checking that it works in OS X. and if that is the case, and you still cannot get it to work in Ubuntu, shut everything down and uplug the iMac for a couple of minutes, then start everything back up. That will reset the smc.

---

### Post by ward83 on 2008-02-22
I did boot to OSX, and sound is working fine there. I haven't tried shutting it down and unplugging it, but I did try a full power-off reboot. I will try turning it off and unplugging it and see if that works.

---

### Post by ward83 on 2008-02-22
Well, still no go. I shut it down, and left it uplugged for about 10 minutes. Any other ideas?

---

### Post by Arcadio on 2008-02-22
Hi,

sometimes ubuntu silences automagically some devices. Try going to the volume control (I don't know the exact name in English: right click over the speaker which is close to the clock in the task bar) and see if the different sound devices are muted.

Hope it helps.

---

### Post by ward83 on 2008-02-22
No, it's not muted. If I right click the icon, then preferences, nothing happens. If I right click it, and then 'Open Volume Control', I get 'No volume control GStreamer plugins and/or devices found'.

---

