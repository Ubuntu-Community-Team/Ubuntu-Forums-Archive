---
title: "What should I do with a bug report?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by rgeddes on 2007-02-27
Today, firefox froze on me and  I got the following entry in my syslog file:


Feb 27 13:02:49 rg-desktop kernel: [ 9098.187892] ------------[ cut here ]------------
Feb 27 13:02:49 rg-desktop kernel: [ 9098.187918] kernel BUG at mm/mmap.c:1971!
Feb 27 13:02:49 rg-desktop kernel: [ 9098.187928] invalid opcode: 0000 [#1]
Feb 27 13:02:49 rg-desktop kernel: [ 9098.187935] SMP 
Feb 27 13:02:49 rg-desktop kernel: [ 9098.187944] Modules linked in: nls_cp437 vfat fat binfmt_misc rfcomm l2cap bluetooth apm radeon drm cpufreq_powersave c
pufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table nls_utf8 ntfs ext2 ipv6 lp af_packet sg sd_mod tsdev serio_raw floppy parport
_pc parport evdev pcspkr psmouse snd_ice1712 snd_ice17xx_ak4xxx snd_ak4xxx_adda snd_cs8427 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd_pag
e_alloc snd_ac97_bus snd_i2c snd_mpu401_uart snd_rawmidi snd_seq_device snd soundcore i2c_piix4 i2c_core tulip shpchp pci_hotplug intel_agp agpgart usbhid us
b_storage scsi_mod libusual reiserfs ehci_hcd ohci_hcd uhci_hcd usbcore ide_generic ide_cd cdrom ide_disk piix generic processor fbcon tileblit font bitblit 
softcursor vesafb capability commoncap
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188118] CPU:    0
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188122] EIP:    0060:[exit_mmap+234/256]    Not tainted VLI
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188128] EFLAGS: 00010202   (2.6.17-11-generic #2) 
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188170] EIP is at exit_mmap+0xea/0x100
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188182] eax: 00000000   ebx: 00000001   ecx: c3bb5d40   edx: cfd20ac4
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188195] esi: 00000000   edi: d5a5ce40   ebp: 00000000   esp: d6733e40
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188206] ds: 007b   es: 007b   ss: 0068
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188218] Process firefox-bin (pid: 7987, threadinfo=d6732000 task=d5a0e580)
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188227] Stack: 00000000 d6733e4c 00000000 00009200 c14049e0 d5a5ce40 d5a5ce88 0000000b 
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188254]        c0120013 d6732000 d5a0e580 c01255d2 08097000 d6733eb0 d44c9ac0 c044e0e4 
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188283]        d5a0e9ec 00000009 d6732000 0000000b 00000008 d6733f14 00000009 c02da075 
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188308] Call Trace:
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188352]  <c0120013> mmput+0x33/0xa0  <c01255d2> do_exit+0xe2/0x840
Feb 27 13:02:49 rg-desktop kernel: [ 9098.188450]  <c02da075> schedule_timeout+0x75/0xc0  <c0125d67> do_group_exit+0x37/0x80
Feb 27 13:02:50 rg-desktop kernel: [ 9098.188520]  <c012e751> get_signal_to_deliver+0x281/0x3f0  <c010266b> do_notify_resume+0x8b/0x6c0
Feb 27 13:02:50 rg-desktop kernel: [ 9098.188632]  <c013a738> sys_futex+0x88/0x100  <c011bde0> default_wake_function+0x0/0x10
Feb 27 13:02:50 rg-desktop kernel: [ 9098.188772]  <c013a738> sys_futex+0x88/0x100  <c01030be> work_notifysig+0x13/0x25
Feb 27 13:02:50 rg-desktop kernel: [ 9098.188897] Code: 5b 5e 5f c3 8b 03 c7 43 08 00 00 00 00 e8 2f 7c fb ff 8b 53 04 83 fa ff 74 d8 8d 43 10 e8 9f 4d 00 00
 c7 43 04 00 00 00 00 eb c7 <0f> 0b b3 07 e5 5e 2f c0 eb c8 8d b6 00 00 00 00 8d bf 00 00 00 
Feb 27 13:02:50 rg-desktop kernel: [ 9098.189011] EIP: [exit_mmap+234/256] exit_mmap+0xea/0x100 SS:ESP 0068:d6733e40
Feb 27 13:02:50 rg-desktop kernel: [ 9098.189033]  <1>Fixing recursive fault but reboot is needed!

What should I know about this message and what should I do about it?
(Of course, I rebooted)

Thnx 
Rich

---

### Post by aysiu on 2007-02-27
You can file bug reports here:
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

I think Edgy Eft and Feisty Fawn automate bug reporting.

---

### Post by actuary286 on 2007-02-27
Ubuntu manages its bugs in a system called [Launchpad]("http://launchpad.net/ubuntu").

You can report your bug here, but first you will need to register for a Launchpad account. I'd also recommend reading the [ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs") page in the Ubuntu wiki. The [article]("http://www.chiark.greenend.org.uk/~sgtatham/bugs.html") on filing bugs referenced there is also quite good.

---

