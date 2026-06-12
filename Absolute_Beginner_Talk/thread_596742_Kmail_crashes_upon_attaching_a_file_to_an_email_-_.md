---
title: "Kmail crashes upon attaching a file to an email - a problem with my hard drive?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-10-29
Dear all,

today the first problem with ubuntu arose since I started using it... months ago.
I have kubuntu feisty installed from server installl
The symptoms are the following:

Acrobat crashes when I was trying to open pdf files
Kontact crashes when I press the clip button to attach files to new emails
Both processes must be killed even though kontact leaves a "disk sleep" process after kill which can't be killed.
Both problems arose togethertoday out of the blue.
The problem with adobe have been solved by installing the latest adobe acrobat
The problem with kontact persists even after having reinstallled kontact

What do you guys think? a problem with my file system? I run kontact in terminal but nothing happens there when the program crashes.

What do you think???

Cheers

Cippa Lippa

----
(message in italian)

Ciao raga

oggi e' successo il primo guasto a ubuntu da quando ho cominciato ad usarlo... mesi fa. 
Ho kubuntu feisty installato da installazione server.
I sintomi sono i seguenti:
Acrobat mi crasha quando cerca di aprire i file pdf
Kontact crasha quando cerco di allegare un file (premendo il pulsante a forma di clip)
Entrambi i processi devono essere killati e kontact spesso anche dopo il kill mi lascia un processo "disk sleep" che non si puo' uccidere
Entrambi i problemi sono sorti oggi dal nulla senza che abbia fatto cose strane

Il problema con adobe si e' risolto installando il nuovo acrobat reader
il problema con kontact persiste anche dopo avere reinstallato kontact

Che ne dite? un bel puzzle eh?

Please help!!!!

Cippa Lippa

---

### Post by Can+~ on 2007-10-29
Did kontact left any logs? Or when executing it from the terminal?

> ls -R /var/log | grep -i kontact
(This commands makes a recursive list of the var/log files, and searches for "kontact" insensitive).

Also, it would be nice to know your specs:
> lspci

---

### Post by Cippa Lippa on 2007-10-30
hey thanks, just learnt where to look for logs :-)
I just found this link which describes exactly the problem I am having. I am using fsdriver to read ext3 filesystemsfrom my windows partition... and it seems that windows is screwing up my filesystem, as I thought.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109177)

there seems to be a solution (patch for it) at [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=3d82abae9523c33d4a16fdfdfd2bdde316d7b56a](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=3d82abae9523c33d4a16fdfdfd2bdde316d7b56a)
but I don't know how to implement it! HELP ME!!!


Anyway this is the message from my logs

this is from syslog:
Oct 30 07:18:13 localhost kernel: [  166.514257] ------------[ cut here ]------------
Oct 30 07:18:13 localhost kernel: [  166.514260] kernel BUG at fs/ext3/namei.c:384!
Oct 30 07:18:13 localhost kernel: [  166.514263] invalid opcode: 0000 [#1]
Oct 30 07:18:13 localhost kernel: [  166.514264] SMP 
Oct 30 07:18:13 localhost kernel: [  166.514268] Modules linked in: radeon drm sony_acpi dev_acpi tc1100_wmi pcc_acpi ibm_acpi sbs i2c_ec dock button container ac asus_acpi battery video backlight ppp_generic slhc ext2 af_packet fuse sbp2 lp wlan_scan_sta snd_intel8x0 ath_rate_sample snd_ac97_codec ath_pci wlan ac97_bus joydev ath_hal(P) snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss pcmcia snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw parport_pc psmouse pcspkr parport snd soundcore yenta_socket rsrc_nonstatic pcmcia_core snd_page_alloc sis_agp shpchp pci_hotplug agpgart i2c_sis96x i2c_core tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic pata_sis libata scsi_mod generic ohci1394 ieee1394 sis900 mii ehci_hcd ohci_hcd usbcore sis5513 thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Oct 30 07:18:13 localhost kernel: [  166.514344] CPU:    0
Oct 30 07:18:13 localhost kernel: [  166.514345] EIP:    0060:[<f89d3b51>]    Tainted: P      VLI
Oct 30 07:18:13 localhost kernel: [  166.514347] EFLAGS: 00210282   (2.6.20-16-generic #2)
Oct 30 07:18:13 localhost kernel: [  166.514364] EIP is at dx_probe+0x1e1/0x320 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514367] eax: 00000090   ebx: ea7d5000   ecx: 00200082   edx: 00000000
Oct 30 07:18:13 localhost kernel: [  166.514371] esi: ea7d5018   edi: ea9d6b70   ebp: ea7baa48   esp: f24dfce0
Oct 30 07:18:13 localhost kernel: [  166.514374] ds: 007b   es: 007b   ss: 0068
Oct 30 07:18:13 localhost kernel: [  166.514377] Process kontact (pid: 4721, ti=f24de000 task=c1b83560 task.ti=f24de000)
Oct 30 07:18:13 localhost kernel: [  166.514379] Stack: f89dff28 f89df26b f89e1d6d 00000180 f89e0078 f24dfdcc 00000000 ea9d6b38 
Oct 30 07:18:13 localhost kernel: [  166.514388]        d93adc84 dfb2c800 f24dfddc f24dfdb4 f24dfe70 f89d474b f24dfdb4 f24dfddc 
Oct 30 07:18:13 localhost kernel: [  166.514397]        f24dfd2c c02ed622 f24dfd54 00000000 f24dfd5c c02ed9c9 c0197d10 ea9d6b38 
Oct 30 07:18:13 localhost kernel: [  166.514405] Call Trace:
Oct 30 07:18:13 localhost kernel: [  166.514443]  [<f89d474b>] ext3_find_entry+0x28b/0x640 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514463]  [io_schedule+34/48] io_schedule+0x22/0x30
Oct 30 07:18:13 localhost kernel: [  166.514480]  [__wait_on_bit+89/112] __wait_on_bit+0x59/0x70
Oct 30 07:18:13 localhost kernel: [  166.514484]  [sync_buffer+0/64] sync_buffer+0x0/0x40
Oct 30 07:18:13 localhost kernel: [  166.514502]  [out_of_line_wait_on_bit+123/144] out_of_line_wait_on_bit+0x7b/0x90
Oct 30 07:18:13 localhost kernel: [  166.514519]  [wake_bit_function+0/96] wake_bit_function+0x0/0x60
Oct 30 07:18:13 localhost kernel: [  166.514539]  [__wait_on_buffer+36/48] __wait_on_buffer+0x24/0x30
Oct 30 07:18:13 localhost kernel: [  166.514550]  [<f89cf044>] __ext3_get_inode_loc+0x254/0x340 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514630]  [<f89d620c>] ext3_lookup+0x3c/0x100 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514644]  [d_alloc+263/400] d_alloc+0x107/0x190
Oct 30 07:18:13 localhost kernel: [  166.514666]  [do_lookup+328/400] do_lookup+0x148/0x190
Oct 30 07:18:13 localhost kernel: [  166.514692]  [__link_path_walk+2151/3696] __link_path_walk+0x867/0xe70
Oct 30 07:18:13 localhost kernel: [  166.514751]  [link_path_walk+69/192] link_path_walk+0x45/0xc0
Oct 30 07:18:13 localhost kernel: [  166.514789]  [do_page_fault+839/1536] do_page_fault+0x347/0x600
Oct 30 07:18:13 localhost kernel: [  166.514823]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0
Oct 30 07:18:13 localhost kernel: [  166.514833]  [getname+167/208] getname+0xa7/0xd0
Oct 30 07:18:13 localhost kernel: [  166.514848]  [__user_walk_fd+59/96] __user_walk_fd+0x3b/0x60
Oct 30 07:18:13 localhost kernel: [  166.514865]  [sys_faccessat+155/336] sys_faccessat+0x9b/0x150
Oct 30 07:18:13 localhost kernel: [  166.514910]  [do_page_fault+839/1536] do_page_fault+0x347/0x600
Oct 30 07:18:13 localhost kernel: [  166.514943]  [sys_access+31/48] sys_access+0x1f/0x30
Oct 30 07:18:13 localhost kernel: [  166.514956]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Oct 30 07:18:13 localhost kernel: [  166.514984]  [xfrm_state_find+803/1392] xfrm_state_find+0x323/0x570
Oct 30 07:18:13 localhost kernel: [  166.515010]  =======================
Oct 30 07:18:13 localhost kernel: [  166.515012] Code: 44 24 10 78 00 9e f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 1d 9e f8 c7 44 24 04 6b f2 9d f8 c7 04 24 28 ff 9d f8 e8 bf 30 75 c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 00 9e f8 c7 44 24 04 6b 
Oct 30 07:18:13 localhost kernel: [  166.515056] EIP: [<f89d3b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:f24dfce0

this is from "messages":
Oct 30 07:18:13 localhost kernel: [  166.514268] Modules linked in: radeon drm sony_acpi dev_acpi tc1100_wmi pcc_acpi ibm_acpi sbs i2c_ec dock button container ac asus_acpi battery video backlight ppp_generic slhc ext2 af_packet fuse sbp2 lp wlan_scan_sta snd_intel8x0 ath_rate_sample snd_ac97_codec ath_pci wlan ac97_bus joydev ath_hal(P) snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss pcmcia snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw parport_pc psmouse pcspkr parport snd soundcore yenta_socket rsrc_nonstatic pcmcia_core snd_page_alloc sis_agp shpchp pci_hotplug agpgart i2c_sis96x i2c_core tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic pata_sis libata scsi_mod generic ohci1394 ieee1394 sis900 mii ehci_hcd ohci_hcd usbcore sis5513 thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap

this is from kern.log:
Oct 30 07:18:13 localhost kernel: [  166.514257] ------------[ cut here ]------------
Oct 30 07:18:13 localhost kernel: [  166.514260] kernel BUG at fs/ext3/namei.c:384!
Oct 30 07:18:13 localhost kernel: [  166.514263] invalid opcode: 0000 [#1]
Oct 30 07:18:13 localhost kernel: [  166.514264] SMP 
Oct 30 07:18:13 localhost kernel: [  166.514268] Modules linked in: radeon drm sony_acpi dev_acpi tc1100_wmi pcc_acpi ibm_acpi sbs i2c_ec dock button container ac asus_acpi battery video backlight ppp_generic slhc ext2 af_packet fuse sbp2 lp wlan_scan_sta snd_intel8x0 ath_rate_sample snd_ac97_codec ath_pci wlan ac97_bus joydev ath_hal(P) snd_pcm_oss snd_pcm snd_mixer_oss snd_seq_dummy snd_seq_oss pcmcia snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device serio_raw parport_pc psmouse pcspkr parport snd soundcore yenta_socket rsrc_nonstatic pcmcia_core snd_page_alloc sis_agp shpchp pci_hotplug agpgart i2c_sis96x i2c_core tsdev evdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic pata_sis libata scsi_mod generic ohci1394 ieee1394 sis900 mii ehci_hcd ohci_hcd usbcore sis5513 thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
Oct 30 07:18:13 localhost kernel: [  166.514344] CPU:    0
Oct 30 07:18:13 localhost kernel: [  166.514345] EIP:    0060:[<f89d3b51>]    Tainted: P      VLI
Oct 30 07:18:13 localhost kernel: [  166.514347] EFLAGS: 00210282   (2.6.20-16-generic #2)
Oct 30 07:18:13 localhost kernel: [  166.514364] EIP is at dx_probe+0x1e1/0x320 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514367] eax: 00000090   ebx: ea7d5000   ecx: 00200082   edx: 00000000
Oct 30 07:18:13 localhost kernel: [  166.514371] esi: ea7d5018   edi: ea9d6b70   ebp: ea7baa48   esp: f24dfce0
Oct 30 07:18:13 localhost kernel: [  166.514374] ds: 007b   es: 007b   ss: 0068
Oct 30 07:18:13 localhost kernel: [  166.514377] Process kontact (pid: 4721, ti=f24de000 task=c1b83560 task.ti=f24de000)
Oct 30 07:18:13 localhost kernel: [  166.514379] Stack: f89dff28 f89df26b f89e1d6d 00000180 f89e0078 f24dfdcc 00000000 ea9d6b38 
Oct 30 07:18:13 localhost kernel: [  166.514388]        d93adc84 dfb2c800 f24dfddc f24dfdb4 f24dfe70 f89d474b f24dfdb4 f24dfddc 
Oct 30 07:18:13 localhost kernel: [  166.514397]        f24dfd2c c02ed622 f24dfd54 00000000 f24dfd5c c02ed9c9 c0197d10 ea9d6b38 
Oct 30 07:18:13 localhost kernel: [  166.514405] Call Trace:
Oct 30 07:18:13 localhost kernel: [  166.514443]  [<f89d474b>] ext3_find_entry+0x28b/0x640 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514463]  [io_schedule+34/48] io_schedule+0x22/0x30
Oct 30 07:18:13 localhost kernel: [  166.514480]  [__wait_on_bit+89/112] __wait_on_bit+0x59/0x70
Oct 30 07:18:13 localhost kernel: [  166.514484]  [sync_buffer+0/64] sync_buffer+0x0/0x40
Oct 30 07:18:13 localhost kernel: [  166.514502]  [out_of_line_wait_on_bit+123/144] out_of_line_wait_on_bit+0x7b/0x90
Oct 30 07:18:13 localhost kernel: [  166.514519]  [wake_bit_function+0/96] wake_bit_function+0x0/0x60
Oct 30 07:18:13 localhost kernel: [  166.514539]  [__wait_on_buffer+36/48] __wait_on_buffer+0x24/0x30
Oct 30 07:18:13 localhost kernel: [  166.514550]  [<f89cf044>] __ext3_get_inode_loc+0x254/0x340 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514630]  [<f89d620c>] ext3_lookup+0x3c/0x100 [ext3]
Oct 30 07:18:13 localhost kernel: [  166.514644]  [d_alloc+263/400] d_alloc+0x107/0x190
Oct 30 07:18:13 localhost kernel: [  166.514666]  [do_lookup+328/400] do_lookup+0x148/0x190
Oct 30 07:18:13 localhost kernel: [  166.514692]  [__link_path_walk+2151/3696] __link_path_walk+0x867/0xe70
Oct 30 07:18:13 localhost kernel: [  166.514751]  [link_path_walk+69/192] link_path_walk+0x45/0xc0
Oct 30 07:18:13 localhost kernel: [  166.514789]  [do_page_fault+839/1536] do_page_fault+0x347/0x600
Oct 30 07:18:13 localhost kernel: [  166.514823]  [do_path_lookup+131/448] do_path_lookup+0x83/0x1c0
Oct 30 07:18:13 localhost kernel: [  166.514833]  [getname+167/208] getname+0xa7/0xd0
Oct 30 07:18:13 localhost kernel: [  166.514848]  [__user_walk_fd+59/96] __user_walk_fd+0x3b/0x60
Oct 30 07:18:13 localhost kernel: [  166.514865]  [sys_faccessat+155/336] sys_faccessat+0x9b/0x150
Oct 30 07:18:13 localhost kernel: [  166.514910]  [do_page_fault+839/1536] do_page_fault+0x347/0x600
Oct 30 07:18:13 localhost kernel: [  166.514943]  [sys_access+31/48] sys_access+0x1f/0x30
Oct 30 07:18:13 localhost kernel: [  166.514956]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Oct 30 07:18:13 localhost kernel: [  166.514984]  [xfrm_state_find+803/1392] xfrm_state_find+0x323/0x570
Oct 30 07:18:13 localhost kernel: [  166.515010]  =======================
Oct 30 07:18:13 localhost kernel: [  166.515012] Code: 44 24 10 78 00 9e f8 c7 44 24 0c 80 01 00 00 c7 44 24 08 6d 1d 9e f8 c7 44 24 04 6b f2 9d f8 c7 04 24 28 ff 9d f8 e8 bf 30 75 c7 <0f> 0b eb fe 89 44 24 0c c7 44 24 08 50 00 9e f8 c7 44 24 04 6b 
Oct 30 07:18:13 localhost kernel: [  166.515056] EIP: [<f89d3b51>] dx_probe+0x1e1/0x320 [ext3] SS:ESP 0068:f24dfce0


I really hope this help..

---

### Post by Cippa Lippa on 2007-10-30
I solved the problem by foollowing a suggestion found on this forum by Hymn to Life, TEMPORARILY by booting from livecd and then running e2fsck -fy /dev/hda1 as sudo, where /dev/hda1 is whatever drive is incriminated

The problem is though NOT solved and it does require the patch mentioned in my previous message. Get we get it a go??

Cheers  

Cippa

---

