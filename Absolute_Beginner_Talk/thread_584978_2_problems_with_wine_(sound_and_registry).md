---
title: "2 problems with wine (sound and registry)"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Dimas on 2007-10-21
I'm trying to configure wine with good performance but I founded two important errors. I have:
- WoW running with Wine 0.9.47.
- Ubuntu 7.10 and WIndows Vista in the other partition
- Mainboard ASUS P5K Deluxe with integrated sound card
- NVidia 8800 Gts

Errors:

**Registry configuration**
When I run "regedit" in terminal I have these errors and it doesn't start:

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls.Resources"
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls.Resources"
wine: Call from 0x7b843f50 to unimplemented function shell32.dll.PrintersGetCommand_RunDLLW, aborting
wine: Call from 0x70015eae to unimplemented function msvcrt.dll._except_handler4_common, aborting
(...)
err:seh:setup_exception stack overflow 684 bytes in thread 0009 eip b7d84743 esp 00240d54 stack 0x241000-0x340000

```

**Audio**
When I start winecfg I have these errors and I haven't sound on any games that use Wine:

```
dimas@hastpc:~$ sudo winecfg
[sudo] password for dimas:
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 1
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:1
ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:mixer:ALSA_MixerInit No master control found on Conexant CX8811, disabling mixer
```

I've tried ALSA and OSS with the same result.

Someone can help? I've googled but I haven't found any solution to that...

---

### Post by Peetke on 2007-10-21
I think you should not use "sudo winecfg" but run winecfg in your own user space.

---

### Post by Dimas on 2007-10-21
Yes, I tried it first without sudo with the same result :/

---

### Post by Dimas on 2007-10-22
Nobody can help? :-(

---

