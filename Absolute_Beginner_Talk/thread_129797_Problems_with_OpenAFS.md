---
title: "Problems with OpenAFS"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by dakebusi on 2006-02-14
Hello,

I've tried to install OpenAFS on my Ubunty 5.10. It has worked fine when I've installed with the 2.6.12-10 kernel. 

However, when I try to install it with my recompiled kernel, I get some errors. I've followed the instructions on /usr/share/doc/openafs-modules-source/README.modules and I've recompiled the kernel and the module at the same time.

When I boot Ubuntu with the recompiled kernel, I get the following error (got from 'dmesg'):

```

[4294737.304000] openafs: no version for "struct_module" found: kernel tainted.
[4294737.305000] openafs: module license 'http://www.openafs.org/dl/license10.ht ml' taints kernel.
[4294737.326000] Found system call table at 0xc02aa900 (pattern scan)
[4294737.326000] kmem_cache_create: duplicate cache afs_inode_cache
[4294737.326000] ------------[ cut here ]------------
[4294737.326000] kernel BUG at <bad filename>:28043!
[4294737.326000] invalid operand: 0000 [#1]
[4294737.326000] Modules linked in: openafs rfcomm l2cap bluetooth speedstep_cen trino cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondem and cpufreq_conservative pcmcia radeon drm video tc1100_wmi sony_acpi pcc_acpi h otkey dev_acpi i2c_acpi_ec i2c_core button battery container ac ipv6 af_packet r tc ohci1394 yenta_socket rsrc_nonstatic pcmcia_core ipw2100 firmware_class ieee8 0211 ieee80211_crypt snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_p cm snd_timer snd soundcore snd_page_alloc tpm_atmel tpm_nsc tpm hw_random shpchp  pci_hotplug intel_agp agpgart nls_iso8859_1 vfat fat nls_cp437 ntfs dm_mod joyd ev tsdev evdev sr_mod sbp2 ieee1394 psmouse mousedev parport_pc lp sd_mod parpor t md ext3 jbd thermal processor fan usb_storage scsi_mod usbhid tg3 ehci_hcd uhc i_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix vga16fb vgast ate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4294737.326000] CPU:    0
[4294737.326000] EIP:    0060:[<c01333f0>]    Tainted: PF     VLI
[4294737.326000] EFLAGS: 00010202   (2.6.12-afs)
[4294737.326000] EIP is at kmem_cache_create+0x3c8/0x42a
[4294737.326000] eax: c027c4e8   ebx: f624ec00   ecx: f7611f3c   edx: f8e5d74b
[4294737.326000] esi: c028057b   edi: f8e5d75b   ebp: dfb56cf0   esp: f7611f40
[4294737.326000] ds: 007b   es: 007b   ss: 0068
[4294737.326000] Process modprobe (pid: 7860, threadinfo=f7610000 task=f6fadaa0)
[4294737.326000] Stack: 00003fff f8e47e80 c0000000 c02b793c 00000000 c02a7940 00 004001 002aa900
[4294737.326000]        f8e6d8a0 c0000000 f7610000 c0114856 f8e5d419 00000000 f8 e6e180 f7610000
[4294737.326000]        c0000000 f7610000 f8e489a6 f8e5d74b 0000020c 00000000 00 022000 f8e48979
[4294737.326000] Call Trace:
[4294737.326000]  [<f8e47e80>] try_harder+0x1e/0x5d [openafs]
[4294737.326000]  [<c0114856>] printk+0xe/0x11
[4294737.326000]  [<f8e489a6>] afs_init_inodecache+0x1d/0x2e [openafs]
[4294737.326000]  [<f8e48979>] init_once+0x0/0x10 [openafs]
[4294737.326000]  [<f8ccc01e>] init_module+0x1e/0x3a [openafs]
[4294737.326000]  [<c0128478>] sys_init_module+0xb5/0x172
[4294737.326000]  [<c01029bf>] sysenter_past_esp+0x54/0x75
[4294737.326000] Code: c0 75 f8 31 c0 eb 04 19 c0 0c 01 85 c0 75 1e ff 74 24 4c 68 e8 c4 27 c0 e8 66 14 fe ff 58 5a ff 05 ac 25 38 c0 0f 8e 23 0f 00 00 <0f> 0b 8b 6d 00 eb 97 8b 54 24 08 b8 00 e0 ff ff 21 e0 89 50 18

```

Any help will be really appreciated.

Thanks!

---

