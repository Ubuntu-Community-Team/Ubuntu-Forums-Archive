---
title: "Daily Crashes: Netatalk, Time Machine &amp; HFS+ HD's"
date: 2012-01-26
forum: Apple Hardware Users
---

### Post by orisdorch on 2012-01-26
Greetings and Salutations!

First and foremost, I'm fairly new to Linux so please bare with me! Been a bit of an Apple power user for years, but Linux gets a heck of a lot more complicated - though I love the amount of control and flexibility it gives!

Here's (are) my Issues: Daily crashes and kernel panics.. some logs below.. Computer doesn't like to shut down after the kernel panics -- hangs on 'Xubuntu' shut-down screen.. Beyond the panics, the full crashes involve fans spinning, lights being on, but monitor will not turn on,  caps lock light won't turn on, and SSH is unavailable.. Have to do a hard reset (hold power button). Have to fsck_hfsplus on my HFS hard drives after every kernel panic / crash, as I can never properly unmount before rebooting (kernel panic prevents normal shut-down).. Same issue was cropping up with just 1 HFS HD.. Have tried minor variations in Netatalk config and mounting options to no avail.. 

Hardware: IBM Think Centre A50: P4 3.8ghz, 512MB Ram, 40GB HD.
Additional HW: Internal 400GB HFS+ HD (Journaling disabled), Enternal 2TB HFS+ HD (Journaling disabled), Tenda wireless USB dongle (ralink based)
Additional SW: Netatalk, HFS utils,  HFS Tools, Avahi, Open SSH, X11VNC, .

Added entries to fstab with these options: hfsplus rw,exec,auto,nosuid,nodev,user 0 0
Example of a manual mount command:
```
sudo mount -t hfsplus -o rw,nosuid,nodev /dev/sdb2 /[mountpoint]
```
Netatalk options used: cnidscheme:dbd options:usedots,tm

I installed Ubuntu 11.10 then installed Xubuntu Desktop, which I generally use. So far this computer serves as a NAS server for other Apple computers in the house.. Not much else on this machine at this point. Tried an erase and reinstall from scratch to resolve, no dice..

Due to crashes and other issues, I've had to force power-off the computer on several occations, and perform umount -l on the 400gb HFS drive, causing corrupt catalogue and incorrect file counts (corrected with fsck_hfsplus).. Have worked through a long list of minor issues to get this up and running so far, though sadly it's still not stable..

ANY help would be appreciated!!!

Log details below:

**System Log details leading up to a crash** (computer unresponsive, had to hard reset, even Caps Lock button didn't light up, though CD tray would eject.):
```
24/01/12 04:28:48 PM	IBM	wpa_supplicant[1119]	WPA: Group rekeying completed with 00:1f:f3:f9:c6:51 [GTK=CCMP]
24/01/12 04:29:35 PM	IBM	afpd[24908]	AFP3.3 Login by zryan
24/01/12 04:29:35 PM	IBM	afpd[24908]	volume "Timemachine" does not support Extended Attributes, using ea:ad instead
24/01/12 04:29:35 PM	IBM	afpd[24908]	volume "BackupHD" does not support Extended Attributes, using ea:ad instead
24/01/12 04:29:37 PM	IBM	kernel	[19270.865307] hfs: keylen 4024 too large
24/01/12 04:29:37 PM	IBM	kernel	[19270.865541] hfs: keylen 4024 too large
24/01/12 04:59:34 PM	IBM	afpd[24908]	select: Invalid argument
24/01/12 04:59:34 PM	IBM	afpd[24908]	dsi_stream_read: len:-1, Invalid argument
24/01/12 04:59:35 PM	IBM	afpd[24908]	===============================================================
24/01/12 04:59:35 PM	IBM	afpd[24908]	INTERNAL ERROR: Signal 11 in pid 24908 (2.2-beta4)
24/01/12 04:59:35 PM	IBM	afpd[24908]	===============================================================
24/01/12 04:59:35 PM	IBM	afpd[24908]	BACKTRACE: 10 stack frames:
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #0 /usr/sbin/afpd(netatalk_panic+0x29) [0x4b4019]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #1 /usr/sbin/afpd(+0x50161) [0x4b4161]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #2 [0x956400]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #3 /lib/i386-linux-gnu/libc.so.6(+0x77b1f) [0xc4fb1f]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #4 /usr/sbin/afpd(dsi_writeinit+0x60) [0x4b1e90]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #5 /usr/sbin/afpd(afp_over_dsi+0x5c7) [0x473597]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #6 /usr/sbin/afpd(+0xe0b5) [0x4720b5]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #7 /usr/sbin/afpd(main+0x560) [0x46f390]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #8 /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3) [0xbf1113]
24/01/12 04:59:35 PM	IBM	afpd[24908]	 #9 /usr/sbin/afpd(+0xb865) [0x46f865]
24/01/12 04:59:36 PM	IBM	afpd[24950]	AFP3.3 Login by zryan
24/01/12 04:59:36 PM	IBM	afpd[24950]	afp_disconnect: trying primary reconnect
24/01/12 04:59:36 PM	IBM	afpd[1036]	Reconnect: no child[24908]
24/01/12 04:59:41 PM	IBM	afpd[24950]	afp_disconnect: primary reconnect failed
24/01/12 04:59:42 PM	IBM	afpd[24950]	dsi_stream_read: len:0, unexpected EOF
24/01/12 04:59:43 PM	IBM	afpd[24956]	AFP3.3 Login by zryan
24/01/12 04:59:43 PM	IBM	afpd[24956]	afp_disconnect: trying primary reconnect
24/01/12 04:59:43 PM	IBM	afpd[1036]	Reconnect: no child[24908]
24/01/12 04:59:48 PM	IBM	afpd[24956]	afp_disconnect: primary reconnect failed
24/01/12 04:59:50 PM	IBM	afpd[24956]	dsi_stream_read: len:0, unexpected EOF
24/01/12 04:59:50 PM	IBM	afpd[24960]	AFP3.3 Login by zryan
24/01/12 04:59:50 PM	IBM	afpd[24960]	afp_disconnect: trying primary reconnect
24/01/12 04:59:50 PM	IBM	afpd[1036]	Reconnect: no child[24908]
24/01/12 04:59:55 PM	IBM	afpd[24960]	afp_disconnect: primary reconnect failed
24/01/12 05:00:00 PM	IBM	afpd[24960]	dsi_stream_read: len:0, unexpected EOF
24/01/12 05:00:00 PM	IBM	afpd[24964]	AFP3.3 Login by zryan
24/01/12 05:00:00 PM	IBM	afpd[24964]	afp_disconnect: trying primary reconnect
24/01/12 05:00:00 PM	IBM	afpd[1036]	Reconnect: no child[24908]
24/01/12 05:00:05 PM	IBM	afpd[24964]	afp_disconnect: primary reconnect failed
24/01/12 05:00:05 PM	IBM	afpd[24964]	dsi_stream_read: len:0, unexpected EOF
24/01/12 05:03:37 PM	IBM	afpd[24564]	afp_zzz: entering extended sleep
24/01/12 05:03:38 PM	IBM	wpa_supplicant[1119]	WPA: Group rekeying completed with 00:1f:f3:f9:c6:51 [GTK=CCMP]
24/01/12 05:07:54 PM	IBM	afpd[24977]	AFP3.3 Login by zryan
24/01/12 05:07:54 PM	IBM	afpd[24977]	afp_disconnect: trying primary reconnect
24/01/12 05:07:54 PM	IBM	afpd[1036]	Reconnect: transfering session to child[24564]
24/01/12 05:07:54 PM	IBM	afpd[1036]	Reconnect: killing new session child[24977] after transfer
24/01/12 05:07:54 PM	IBM	afpd[24564]	afp_dsi_transfer_session: succesfull primary reconnect
24/01/12 05:07:54 PM	IBM	afpd[24983]	AFP3.3 Login by zryan
24/01/12 05:07:55 PM	IBM	afpd[24983]	volume "Timemachine" does not support Extended Attributes, using ea:ad instead
24/01/12 05:07:55 PM	IBM	afpd[24983]	volume "BackupHD" does not support Extended Attributes, using ea:ad instead
24/01/12 05:07:56 PM	IBM	kernel	[21569.965542] hfs: keylen 4024 too large
24/01/12 05:07:56 PM	IBM	kernel	[21569.965979] hfs: keylen 4024 too large
24/01/12 05:08:01 PM	IBM	afpd[24977]	afp_disconnect: primary reconnect succeeded
24/01/12 05:17:01 PM	IBM	CRON[25005]	(root) CMD (   cd / && run-parts --report /etc/cron.hourly)
24/01/12 05:20:36 PM	IBM	wpa_supplicant[1119]	WPA: Group rekeying completed with 00:1f:f3:f9:c6:51 [GTK=CCMP]
24/01/12 05:39:48 PM	IBM	afpd[24983]	AFP logout by zryan
24/01/12 05:39:48 PM	IBM	afpd[24983]	AFP statistics: 91086.27 KB read, 76767.53 KB written
24/01/12 05:39:48 PM	IBM	afpd[24983]	done
24/01/12 05:48:59 PM	IBM	avahi-daemon[893]	Received response from host 10.0.1.7 with invalid source port 50535 on interface 'wlan0.0'
24/01/12 05:48:59 PM	IBM	afpd[25062]	AFP3.3 Login by zryan
24/01/12 05:48:59 PM	IBM	afpd[25062]	volume "Timemachine" does not support Extended Attributes, using ea:ad instead
24/01/12 05:48:59 PM	IBM	afpd[25062]	volume "BackupHD" does not support Extended Attributes, using ea:ad instead
24/01/12 05:49:00 PM	IBM	kernel	[24034.233200] hfs: keylen 861 too large
24/01/12 05:49:00 PM	IBM	kernel	[24034.233487] hfs: keylen 861 too large
24/01/12 06:04:46 PM	IBM	afpd[25062]	AFP logout by zryan
24/01/12 06:04:46 PM	IBM	afpd[25062]	AFP statistics: 83998.85 KB read, 70836.49 KB written
24/01/12 06:04:46 PM	IBM	afpd[25062]	done
24/01/12 06:17:01 PM	IBM	CRON[25136]	(root) CMD (   cd / && run-parts --report /etc/cron.hourly)
24/01/12 06:37:23 PM	IBM	afpd[25185]	AFP statistics: 0.51 KB read, 0.38 KB written
24/01/12 07:17:01 PM	IBM	CRON[25264]	(root) CMD (   cd / && run-parts --report /etc/cron.hourly)
24/01/12 07:31:49 PM	IBM	afpd[25291]	AFP3.3 Login by zryan
24/01/12 07:31:49 PM	IBM	afpd[25291]	volume "Timemachine" does not support Extended Attributes, using ea:ad instead
24/01/12 07:31:49 PM	IBM	afpd[25291]	volume "BackupHD" does not support Extended Attributes, using ea:ad instead
24/01/12 07:37:31 PM	IBM	afpd[25310]	AFP3.3 Login by zryan
24/01/12 07:37:31 PM	IBM	afpd[25310]	volume "Timemachine" does not support Extended Attributes, using ea:ad instead
24/01/12 07:37:31 PM	IBM	afpd[25310]	volume "BackupHD" does not support Extended Attributes, using ea:ad instead
24/01/12 07:37:34 PM	IBM	kernel	[30548.082183] hfs: keylen 861 too large
24/01/12 07:37:34 PM	IBM	kernel	[30548.082426] hfs: keylen 861 too large
```
*** Log picks up at the next boot, which is after a hard reset.



**Dmesg details of a recent kernel panic **(screen went black with white text, was able to exit with ctrl-alt-F7).. The trace details have become very familiar, and also show in log files preceeding crashes.. Actual panic occurred with the second kernel error (bottom):
```
[ 7055.769178] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
[ 7055.769178]   cache: kmalloc-8192, object size: 8192, buffer size: 8192, default order: 3, min order: 1
[ 7055.769178]   node 0: slabs: 72, objs: 285, free: 0
[ 7055.769591] kworker/u:0: page allocation failure: order:1, mode:0x4020
[ 7055.769600] Pid: 3861, comm: kworker/u:0 Not tainted 3.0.0-15-generic #26-Ubuntu
[ 7055.769605] Call Trace:
[ 7055.769622]  [<c151a7a2>] ? printk+0x2d/0x2f
[ 7055.769635]  [<c10e3c3f>] warn_alloc_failed+0xbf/0xf0
[ 7055.769644]  [<c10e69a3>] __alloc_pages_nodemask+0x513/0x6e0
[ 7055.769655]  [<c1077f21>] ? tick_program_event+0x21/0x30
[ 7055.769666]  [<c1117c9b>] allocate_slab+0xbb/0xd0
[ 7055.769674]  [<c1117cd7>] new_slab+0x27/0x110
[ 7055.769682]  [<c151e06b>] __slab_alloc.constprop.65+0xbf/0x191
[ 7055.769692]  [<c1430531>] ? dev_alloc_skb+0x21/0x40
[ 7055.769703]  [<c111ac78>] __kmalloc_track_caller+0x1c8/0x1d0
[ 7055.769713]  [<c13ce8f8>] ? ehci_urb_enqueue+0x58/0xf0
[ 7055.769722]  [<c142fe1e>] ? __alloc_skb+0x2e/0x1f0
[ 7055.769729]  [<c1430531>] ? dev_alloc_skb+0x21/0x40
[ 7055.769737]  [<c142fe48>] __alloc_skb+0x58/0x1f0
[ 7055.769744]  [<c1430531>] dev_alloc_skb+0x21/0x40
[ 7055.769765]  [<e0b0360a>] rt2x00queue_alloc_rxskb+0x4a/0x140 [rt2x00lib]
[ 7055.769777]  [<e0b009b1>] rt2x00lib_rxdone+0x81/0x1f0 [rt2x00lib]
[ 7055.769786]  [<c1001c24>] ? __switch_to+0x94/0x1a0
[ 7055.769797]  [<c152e0bd>] ? _raw_spin_lock_irqsave+0x2d/0x40
[ 7055.769809]  [<e0b02dbe>] ? rt2x00queue_get_entry+0x3e/0x90 [rt2x00lib]
[ 7055.769818]  [<c152bea1>] ? __schedule+0x2f1/0x620
[ 7055.769829]  [<e02b114c>] rt2x00usb_work_rxdone+0x4c/0x80 [rt2x00usb]
[ 7055.769839]  [<c10602c2>] ? cwq_dec_nr_in_flight+0x52/0x90
[ 7055.769846]  [<c10616e1>] process_one_work+0x101/0x3a0
[ 7055.769855]  [<c1535530>] ? common_interrupt+0x30/0x38
[ 7055.769865]  [<e02b1100>] ? rt2x00usb_disconnect+0x70/0x70 [rt2x00usb]
[ 7055.769875]  [<c1062244>] worker_thread+0x124/0x2d0
[ 7055.769883]  [<c1062120>] ? manage_workers.isra.28+0x110/0x110
[ 7055.769891]  [<c1065d5d>] kthread+0x6d/0x80
[ 7055.769898]  [<c1065cf0>] ? flush_kthread_worker+0x80/0x80
[ 7055.769906]  [<c153553e>] kernel_thread_helper+0x6/0x10
[ 7055.769910] Mem-Info:
[ 7055.769913] DMA per-cpu:
[ 7055.769918] CPU    0: hi:    0, btch:   1 usd:   0
[ 7055.769923] CPU    1: hi:    0, btch:   1 usd:   0
[ 7055.769927] Normal per-cpu:
[ 7055.769931] CPU    0: hi:  186, btch:  31 usd:  46
[ 7055.769935] CPU    1: hi:  186, btch:  31 usd: 120
[ 7055.769944] active_anon:39657 inactive_anon:33731 isolated_anon:0
[ 7055.769946]  active_file:9508 inactive_file:29594 isolated_file:0
[ 7055.769948]  unevictable:0 dirty:724 writeback:0 unstable:0
[ 7055.769950]  free:1291 slab_reclaimable:2344 slab_unreclaimable:3833
[ 7055.769952]  mapped:9670 shmem:24328 pagetables:1646 bounce:0
[ 7055.769965] DMA free:1968kB min:88kB low:108kB high:132kB active_anon:916kB inactive_anon:4772kB active_file:744kB inactive_file:4984kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:876kB writeback:0kB mapped:176kB shmem:2432kB slab_reclaimable:360kB slab_unreclaimable:1752kB kernel_stack:176kB pagetables:160kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[ 7055.769975] lowmem_reserve[]: 0 483 483 483
[ 7055.769992] Normal free:3196kB min:2764kB low:3452kB high:4144kB active_anon:157712kB inactive_anon:130152kB active_file:37288kB inactive_file:113392kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:495236kB mlocked:0kB dirty:2020kB writeback:0kB mapped:38504kB shmem:94880kB slab_reclaimable:9016kB slab_unreclaimable:13580kB kernel_stack:2216kB pagetables:6424kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:977 all_unreclaimable? no
[ 7055.770003] lowmem_reserve[]: 0 0 0 0
[ 7055.770013] DMA: 14*4kB 13*8kB 25*16kB 8*32kB 4*64kB 3*128kB 2*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1968kB
[ 7055.770033] Normal: 799*4kB 0*8kB 0*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 3196kB
[ 7055.770054] 74704 total pagecache pages
[ 7055.770058] 11240 pages in swap cache
[ 7055.770062] Swap cache stats: add 455959, delete 444719, find 172649/226342
[ 7055.770067] Free swap  = 365984kB
[ 7055.770070] Total swap = 508924kB
[ 7055.773358] 128864 pages RAM
[ 7055.773366] 0 pages HighMem
[ 7055.773369] 3955 pages reserved
[ 7055.773372] 78615 pages shared
[ 7055.773375] 63322 pages non-shared
[ 7055.773383] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
[ 7055.773389]   cache: kmalloc-8192, object size: 8192, buffer size: 8192, default order: 3, min order: 1
[ 7055.773396]   node 0: slabs: 72, objs: 285, free: 0
[ 7691.260503] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7691.269267] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7691.674896] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.120479] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.131088] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.137086] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.153966] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.161204] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.172582] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.183964] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.192447] hfs: inconsistency in B*Tree (2,0,1,0,421)
[ 7695.370691] BUG: unable to handle kernel NULL pointer dereference at   (null)
[ 7695.370776] IP: [<c102bac0>] kmap+0x10/0x60
[ 7695.370818] *pde = 1c5f2067 *pte = 00000000 
[ 7695.370853] Oops: 0000 [#1] SMP 
[ 7695.370885] Modules linked in: appletalk bnep rfcomm bluetooth dm_crypt arc4 rt2800usb rt2800lib binfmt_misc crc_ccitt rt2x00usb rt2x00lib mac80211 nls_utf8 hfsplus cfg80211 snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ppdev snd_timer snd_seq_device psmouse serio_raw snd shpchp soundcore snd_page_alloc parport_pc lp parport usbhid hid usb_storage uas e1000 i915 floppy drm_kms_helper drm i2c_al
[ 7695.371371] Pid: 6654, comm: afpd Not tainted 3.0.0-15-generic #26-Ubuntu IBM 8183WR4/IBM
[ 7695.371431] EIP: 0060:[<c102bac0>] EFLAGS: 00010246 CPU: 1
[ 7695.371470] EIP is at kmap+0x10/0x60
[ 7695.371499] EAX: 00000000 EBX: 00000000 ECX: de34b0c0 EDX: dc670000
[ 7695.371543] ESI: 00000004 EDI: 000000c0 EBP: dc671a00 ESP: dc6719fc
[ 7695.371586]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[ 7695.371625] Process afpd (pid: 6654, ti=dc670000 task=c0515940 task.ti=dc670000)
[ 7695.371675] Stack:
[ 7695.371690]  da8f8e00 dc671a1c e0aeffd0 fffde357 dc671a4c da8f8e00 00000002 dc671ca0
[ 7695.371766]  dc671a5c e0af216f 00000004 de34a200 ffffffff dc671ab8 c152bea1 00000000
[ 7695.371841]  dc671ae0 db428800 00000000 000001a5 c186dec0 dc671ca0 dc4f975c dc671a84
[ 7695.371916] Call Trace:
[ 7695.371945]  [<e0aeffd0>] hfsplus_bnode_read+0x40/0xb0 [hfsplus]
[ 7695.371992]  [<e0af216f>] hfsplus_brec_find+0x6f/0x140 [hfsplus]
[ 7695.372043]  [<c152bea1>] ? __schedule+0x2f1/0x620
[ 7695.372083]  [<e0af2260>] hfsplus_brec_read+0x20/0x60 [hfsplus]
[ 7695.372129]  [<e0aedf9f>] hfsplus_find_cat+0x3f/0xd0 [hfsplus]
[ 7695.372179]  [<c1069c30>] ? __remove_hrtimer+0x40/0xa0
[ 7695.372216]  [<c106a4e2>] ? hrtimer_try_to_cancel+0x42/0xb0
[ 7695.372254]  [<c106a569>] ? hrtimer_cancel+0x19/0x30
[ 7695.372290]  [<c152d29f>] ? schedule_hrtimeout_range_clock+0xcf/0x170
[ 7695.372335]  [<c1069dd0>] ? update_rmtp+0x80/0x80
[ 7695.372368]  [<c10263e8>] ? default_spin_lock_flags+0x8/0x10
[ 7695.372409]  [<c152e0bd>] ? _raw_spin_lock_irqsave+0x2d/0x40
[ 7695.372452]  [<c10664af>] ? remove_wait_queue+0x3f/0x50
[ 7695.372494]  [<c113996f>] ? poll_freewait+0x3f/0xc0
[ 7695.372529]  [<c113a3c8>] ? do_select+0x4e8/0x570
[ 7695.372564]  [<c11399f0>] ? poll_freewait+0xc0/0xc0
[ 7695.372599]  [<c1139ac0>] ? __pollwait+0xd0/0xd0
[ 7695.372635]  [<c146afcd>] ? ip_finish_output+0x12d/0x300
[ 7695.372673]  [<c146afcd>] ? ip_finish_output+0x12d/0x300
[ 7695.372710]  [<c146bb37>] ? ip_output+0xc7/0xe0
[ 7695.372743]  [<c11194b5>] ? __kmalloc+0x195/0x1e0
[ 7695.372778]  [<e0af1f59>] ? hfsplus_find_init+0x29/0x50 [hfsplus]
[ 7695.372820]  [<c152ccb8>] ? mutex_lock+0x18/0x40
[ 7695.372859]  [<e0af1f78>] ? hfsplus_find_init+0x48/0x50 [hfsplus]
[ 7695.372904]  [<e0aec4e3>] hfsplus_cat_write_inode+0x83/0x230 [hfsplus]
[ 7695.372955]  [<c1481397>] ? tcp_transmit_skb+0x2d7/0x4c0
[ 7695.372997]  [<c1481d73>] ? tcp_write_xmit+0x153/0x370
[ 7695.373034]  [<c152df86>] ? _raw_spin_unlock_bh+0x16/0x20
[ 7695.373072]  [<c142b27f>] ? release_sock+0x5f/0x70
[ 7695.373109]  [<c142ec60>] ? skb_release_data+0x80/0xb0
[ 7695.373146]  [<c1118c2a>] ? kmem_cache_free+0xea/0x100
[ 7695.373184]  [<c152df86>] ? _raw_spin_unlock_bh+0x16/0x20
[ 7695.373221]  [<c142b27f>] ? release_sock+0x5f/0x70
[ 7695.373258]  [<c142e94e>] ? kfree_skbmem+0x2e/0x80
[ 7695.373301]  [<c10df707>] ? find_get_pages_tag+0x37/0x110
[ 7695.373345]  [<c10e6e78>] ? tag_pages_for_writeback+0x68/0xb0
[ 7695.373388]  [<c10e89c7>] ? pagevec_lookup_tag+0x27/0x30
[ 7695.373429]  [<c10df707>] ? find_get_pages_tag+0x37/0x110
[ 7695.373469]  [<c115a580>] ? mpage_end_io+0x90/0x90
[ 7695.374618]  [<c10e89c7>] ? pagevec_lookup_tag+0x27/0x30
[ 7695.374618]  [<c10df2e5>] ? filemap_fdatawait_range+0x95/0x160
[ 7695.374618]  [<c10df707>] ? find_get_pages_tag+0x37/0x110
[ 7695.374618]  [<e0aed500>] ? hfsplus_file_extend+0x300/0x300 [hfsplus]
[ 7695.374618]  [<c115a42b>] ? mpage_writepages+0x7b/0xa0
[ 7695.391137]  [<c152ccb8>] ? mutex_lock+0x18/0x40
[ 7695.391137]  [<e0aea1ef>] hfsplus_write_inode+0x2f/0x40 [hfsplus]
[ 7695.391137]  [<c114b83e>] writeback_single_inode+0x1be/0x210
[ 7695.391137]  [<c114b8c5>] sync_inode+0x35/0x60
[ 7695.391137]  [<c114b923>] sync_inode_metadata+0x33/0x40
[ 7695.391137]  [<e0aeb731>] hfsplus_file_fsync+0x31/0xd0 [hfsplus]
[ 7695.391137]  [<c114f597>] vfs_fsync_range+0x57/0x80
[ 7695.391137]  [<c114f677>] vfs_fsync+0x27/0x30
[ 7695.391137]  [<c114f906>] sys_fsync+0x26/0x50
[ 7695.391137]  [<c152e2a4>] syscall_call+0x7/0xb
[ 7695.391137]  [<c1520000>] ? ext3_orphan_cleanup.isra.15+0x19f/0x271
[ 7695.391137] Code: 74 26 00 8b 15 c8 25 88 c1 e8 ed fe ff ff 5d c3 8d 74 26 00 8d bc 27 00 00 00 00 55 89 e5 53 3e 8d 74 26 00 89 c3 e8 60 07 50 00 <8b> 03 c1 e8 1e 69 c0 40 03 00 00 05 00 54 7b c1 2b 80 0c 03 00 
[ 7695.391137] EIP: [<c102bac0>] kmap+0x10/0x60 SS:ESP 0068:dc6719fc
[ 7695.391137] CR2: 0000000000000000
[ 7695.453695] ---[ end trace e3accf255a3ea019 ]---
```
*** I'm able to return to my GUI after this using Ctrl-Alt-F7, though reboot & shut-down get hung-up..

---

### Post by Khayyam on 2012-01-27
orisdorch ..

Its late here and so I probably won't have too much to energy solve the problem in one swoop, however, I've some experience with Netatalk and so can hopefully give you some pointers.

First off, the problem doesn't seem to be with Netatalk, but a hfs engenderd kernel oops, somewhat akin to the oops reported [here]("http://lkml.indiana.edu/hypermail/linux/kernel/1109.2/00309.html") on the kernel mailing list (Sep 16 2011).

The exact reasons for this I can't be sure, but from the dmesg output the oops seems to be triggerd by an inconsistency in the B*Tree (the filesystems catalogue file). I can only speculate that something is not right with the B*Tree on these disks. Whether this is caused by afpd "using ea:ad instead" on detecting the filesystems lack of support extended attributes (at 04:29:35), or the disk itself, its difficult to tell. It's not a problem I've encountered.

That said, I've never served HFS+ formated disks over AFP, there is no need to. The filesystem is mostly transparent to AFP, metadata is handled by the cnid_meta daemon (see bellow), and in my experience the client shouldn't notice any difference. The idea of Netatalk is to serve *nix filesystems over AFP, it doesn't require HFS+. Unless you must have the disks formated as HFS+ I would suggest you don't.

Another possible issue is that Ubuntu's Netatalk package is 2.2-beta2, the current stable release is 2.2.2 (see the [Netatalk website]("http://netatalk.sourceforge.net/")). It may be a bug in the beta that is triggering this (though given the bug reported above, the problem lies with the kernels hfsplus support). I would try 2.2.2 and see if the problem persists.

In your 'options' your running 'cnidscheme:dbd' but is the cnid_meta daemon set to start in your config? If your network doesn't need to provide appletalk services for OS9 clients then your /etc/default/netatalk should look like the following:
```
ATALKD_RUN=no
 PAPD_RUN=no
CNID_METAD_RUN=yes
AFPD_RUN=yes
TIMELORD_RUN=no
A2BOOT_RUN=no
```I've never used cnidscheme:dbd but cnidscheme:cbd, not sure this will make a difference though. Also, I've never used the 'tm' (Time Machine) option, I'm not entirely sure it will behave with standard Appletalk disk usage, doesn't Time Machine create a sparsebundle on the volume? I don't know how this works exactly but I would try without this.

BTW, its best to post your full config /etc/netatalk/afpd.conf /etc/netatalk/AppleVolumes.default /etc/defaults/netatalk (in codeblocks) when reporting problems, otherwise its alot of guesswork this end.

---

### Post by orisdorch on 2012-01-27
Hey Khayyam - thanks so much for your reply!!!


/etc/default/netatalk does look as you describe - the CNID_METAD_RUN is set to Yes..

I'm using HFS rather than a more unix-friendly configuration primarily as a failsafe, which might be more a fail than a safe.. The idea is this: If I have a major crash and need to restore from my Timemachine HD, I want to be able to plug it directly into my Mac to restore, just in case..

You're right about Timemachine creating a sparsebundle on the network volume - there are 2 computers backing up here, so 2 sparsebundles on there.. It's worth noting that I've had issues with HFS plus and write permissions, prompting me to create group 'hfs' with ID '99', which OSX sets as the owner of HFS volumes.. Chose this route over changing the owner / permissions in hopes that it would retain full compatibility for direct plug-in to an OSX machine in the future.

I'll try the following steps between crashes to see if I have any luck:
1. Unplug the 'BackupHD' HFS volume to isolate the issue
1. Change cnidscheme to cbd
2. Removing the 'tm' option from netatalk config for the Timemachine HD
3. Rebuilt the catalogue for the Timemachine HD using:
```
sudo fsck.hfsplus -r /dev/[drivelocation]
```
4. Update to Netatalk 2.2.2 


Posting the files you suggested, or at least the non-markup parts..  Not sure what's relevant on /etc/defaults/netatalk, so posted the whole thing. 

Thanks again for taking the time to respond!!

/etc/netatalk/AppleVolumes.default 
```
/home/zryan/Timemachine allow:zryan cnidscheme:dbd options:usedots,tm
/home/zryan/BackupHD allow:zryan cnidscheme:dbd options:usedots
/home/zryan allow:zryan cnidscheme:dbd options:usedots
```

/etc/defaults/netatalk
```
#########################################################################
# Global configuration
#########################################################################

#### machine's AFPserver/AppleTalk name.
#ATALK_NAME=machinename

#### server (unix) and legacy client (<= Mac OS 9) charsets
ATALK_UNIX_CHARSET='LOCALE'
ATALK_MAC_CHARSET='MAC_ROMAN'

#### Don't Edit. export the charsets, read form ENV by apps
export ATALK_UNIX_CHARSET
export ATALK_MAC_CHARSET

#########################################################################
# AFP specific configuration
#########################################################################

#### Set which daemons to run.
#### If you use AFP file server, run both cnid_metad and afpd.
ATALKD_RUN=no
PAPD_RUN=no
CNID_METAD_RUN=yes
AFPD_RUN=yes
TIMELORD_RUN=no
A2BOOT_RUN=no

#### maximum number of clients that can connect:
#AFPD_MAX_CLIENTS=20

#### UAMs (User Authentication Modules)
#### available options: uams_dhx.so, uams_dhx2.so, uams_guest.so,
####                    uams_clrtxt.so(legacy), uams_randnum.so(legacy)
#AFPD_UAMLIST="-U uams_dhx2.so,uams_clrtxt.so"

#### Set the id of the guest user when using uams_guest.so
#AFPD_GUEST=nobody

#### config for cnid_metad. Default log config:
#CNID_CONFIG="-l log_note"

#########################################################################
# AppleTalk specific configuration (legacy)
#########################################################################

#### Set which legacy daemons to run.
#### If you need AppleTalk, run atalkd.
#### papd, timelord and a2boot are dependent upon atalkd.
#ATALKD_RUN=no
#PAPD_RUN=no
#TIMELORD_RUN=no
#A2BOOT_RUN=no

#### Control whether the daemons are started in the background.
#### If it is dissatisfied that legacy atalkd starts slowly, set "yes".
#ATALK_BGROUND=no

#### Set the AppleTalk Zone name.
#### NOTE: if your zone has spaces in it, you're better off specifying
####       it in afpd.conf
#ATALK_ZONE=@zone
```


/etc/netatalk/afpd.conf  
```
- -transall -uamlist uams_randnum.so,uams_dhx2.so -nosavepassword -advertise_ssh

```

---

### Post by Khayyam on 2012-01-28
orisdorch .. no problem, hopefully we can figure out what the problem is.

I can understand your wanting to have some flexability WRT your use of Time Machine but isn't the whole purpose of a NAS to provide such services (backup & restore) without having to go in search of the hardisk on which the backup is stored? Given that Time Machine is designed with distributive storage in mind I'm not really getting why you would need that 'failsafe'. I've not used Time Machine and so I'm not entirely sure of what it is capable of, but surely a "major crash" would be the exact situation it was designed for. Does it not allow you to sync a backup onto a clean install over the network? I'm not asking this disingeniuosly, I'm genuinely unfamiliar with what its capable of, but my understanding was that it does just that. Anyhow, it may indeed be more fail than safe, and assuming that it would work as well from a NAS as a connected HD, I'm struggling to understand your reasoning.  

Still, its hardly your "failsafe" that is at fault here (though you might circumvernt these issues by simplifying your options), the hfsplus support in the kernel obviously has issues, and it seems afpd triggers it. I wonder (speculatively) if both the kernels hfsplus filesystem and afpd (or perhaps the cnid_meta daemon) aren't expecting to maintain the B*Tree and when doing so conflicting with each other. I say speculatively as I'm not sure what Netatalk does ITR, but I imagine (given the fact that Netatalk expects to export non-B*Tree'd filesystems) it probably is not expecting a B*Tree to be there (cnid_meta expects to take care of a metadata). If I'm right then this conflict may be whats causing the oops.

I wonder if on a HFS+ filesystem the cnid_meta demon is necessary. You might test with CNID_METAD_RUN=no and remove the 'cnidscheme' in /etc/netatalk/AppleVolumes.default. I'm not sure how, or if, aftp operates without CNID but it might be worth giving it a shot (it would perhaps shed some light on the above hypothesis).
      
Note: /etc/netatalk/AppleVolumes.defualt shows nested volumes (/home/zryan/Timemachine and /home/zryan/BackupHD nested in /home/zryan) this is a no-no for CNID (see the "Note" in [Chapter 3 of the Netatalk documentation]("http://netatalk.sourceforge.net/2.0/htmldocs/configuration.html"). This would lead to a situation where each entry is expecting its own aftp_root/.AppleDouble and aftp_root/.AppleDB but as they are nested there would be similar .AppleDouble or .AppleDB's in the root of the other (nested) directories. /home/zryan/Timemachine and /home/zryan/BackupHD should be OK, just don't nest them in /home/zryan.

Note that as you've cashed its possible the CNID data files (.AppleDouble and .AppleDB) have been corrupted (see the above linked Netatalk documentation for why this happens) so, it's probably a good idea to remove them (they will be regenerated). 

The /etc/netatalk/afpd.conf and the other configuration files look fine (sans the nesting mentioned above).

Your probably OK with cnidscheme:dbd, both dbd and cdb will probably trigger the same result (they are simply different storage methods for CNID).

If the drive(s) don't have anything on them, or its data that can be replaced. It might be worth disconnecting them, and running Disk Utilities on it/them, perhaps even a reformat. This is just incase fsck.hfplus isn't fixing the B*Tree correctly, also, we can rule out as yet the disks being faulty (a low level format would detect badblocks).

Thats about all I can suggest for the moment. I think one easy solution for you would be to switch filesystems on the drives, but given your wanting to maintain the failsafe, we should at least exhaust other options before I say "there is your solution" and leave you to make the choice.

BTW, I think I've read elsewhere of a Time Machine setup that didn't use the 'tm' option. Not sure exactly what it does, but its not a requirement.

HTH .. and again .. no problem.

---

### Post by Khayyam on 2012-01-28
very quick follow-up ...

I'm reading all kinds of conflicting information about Time Machine's filesystem requirements. A user of this form states [in this thread]("http://ubuntuforums.org/showpost.php?p=11631646&postcount=4") that Time Machines requires a journaled HFS+. A similar position is stated in [a post on the QNAP forum]("http://forum.qnap.com/viewtopic.php?p=193504"), this person also states that the filesystem needs to be case-sensitive! Of course I can find no definitive statement from Apple on this question.

---

### Post by orisdorch on 2012-01-29
Thanks again for taking the time to help Khayyam!

Trying to leave a paper train for others in my situation.. 

I performed the following steps
1. Unplug the 'BackupHD' HFS volume to isolate the issue
1. Change cnidscheme to cbd
2. Removing the 'tm' option from netatalk config for the Timemachine HD
3. Rebuilt the catalogue for the Timemachine HD using:
```
sudo fsck.hfsplus -r /dev/[drivelocation]
```
- It's worth noting that I got a bunch of errors on this.. I've run fsck.hfsplus a TON in the past month, and this was the worst by far, but the crashes started with a cleanly formatted drive, so I don't think it comes down to btree corruption here... 
4. Delete all .Apple files and directories from all Netatalk share root folders using:
```
ls -a
sudo rm -r [filename]
```

Tried continue use after this, and ran into another crash.

I did NOT update to Netatalk 2.2.2, as upon downloading the package I saw that I would need to compile it from scratch, and as a fairly new user with little documentation out there for compiling 2.2.2, I preferred to avoid this road.. Looking at high level release hi-lights, there's no mention of HFS.

SO, I gave up. backed up my sparsebundles, Wiped my Timemachine drive, reformatted to ex4, and reconfigured from there. Seems to be working fine for now for backups..

I know Apple only technically supports HFS+ Journaled.. Read about [one person]("http://bigdiver.wordpress.com/2009/11/24/restoring-time-machine-backups-on-a-different-computer/") who successfully restored from a setup like this, which is reassuring, but it does involve use of terminal commands which doesn't really follow Apple's credo of simplicity for the end user, thus I wouldn't be surprised it's unsupported simply because of the extra steps required and programming that would have been needed to support setups like this.

Anyhow, I am still troubleshooting for the sake of others, and have the 'BackupHD' which is also HFS, which I'll play with a bit more.. Even after fixing my Timemachine volume, I did get a crash when using BackupHD, so that means 2 drives are affected (both freshly formatted before using for this) - looks like software to me.

I do think you're on to something with conflicting efforts around HFS support.  It's only when I use an Apple (HFS) drive AND AppleShare (Netatalk) protocols; I don't get crashes when I simply have an HFS drive plugged in and in use on Ubuntu, and I don't get crashes when I share an Ext4 drive over Netatalk. I have no clue what the Timemachine (tm) option in netatalk does, as it does not seem to be necessary.

I'll try running without the CNID daemon, but I suspect it simply won't work.. I'll also move my shares around as you describe (moving shares out of my home folder).

For the sake of curiosity, I'm going to run an experiment of using the HFS volume over SMB (Samba) to see if I can reproduce.. Read that SMB is much slower for backups, but if it's more stable for HFS volumes, that might be a worthwhile trade off for some poor sucker who can't switch to Ext4 :p


ALSO - for the sake of anyone looking to follow my footsteps - here are a few notes on resources I used to get setup:
```

Setting up AppleTalk and Time Machine:
http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/

Per http://talklikeaduck.denhaven2.com/2010/07/19/ubuntu-timemachine-server-for-snow-leopard
"The article gives the following configuration line in /etc/netatalk/afpd.conf
  - - transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword -advertise_ssh
But with the current netatalk this needs to be changed to:
  - - transall -uamlist uams_randnum.so,uams_dhx2.so -nosavepassword -advertise_ssh"

NOTES: If using ssh to modify files, use nano instead of gedit.


HFS FILESYSTEM
I started with an actual TimeMachine backup hard drive that I wanted to move to NAS... I spent days trying to get that to work and eventually gave up.. Timemachine likes to use sparsebundles when backing up remotely, and my existing backups weren't setup as such.. Also ran into a slew of permission errors and caused kernel panics when trying CHOWN and CHMOD commands recursively. 

You'll probably need to DISABLE JOURNALING on an HFS Plus drive by plugging it into a mac, selecting the drive to Disk Utilities, holding Option and clicking File>Disable Journaling

Example- force mount RW WITH JOURNALING STILL ACTIVE (not recommended): 
sudo mount -t hfsplus -o force,rw,nosuid,nodev,uid=1000 /dev/sdb2 /home/zryan/Timemachine

Example - Mount WITHOUT JOURNALING: 
sudo mount -t hfsplus -o rw,nosuid,nodev,uid=1000 /dev/sdb2 /home/zryan/Timemachine
NOTE: uid=1000 did allow me to mount the drive with write access using my user ID (which, according to 'id -u [username]' was 1000.  I wasn't able to get this to work in fstab (auto-mount on boot), so I ended up having to do a user group tweak (Adding GID 99 and adding myself to the group).

I added this to /etc/fstab so that Hard Drive would mount on boot or by using 'sudo mount -a':
/dev/sdb2 /home/zryan/Timemachine hfsplus rw,exec,auto,nosuid,nodev,user 0 0

sudo groupadd -g 99 hfsplus
sudo usermod -a -G hfsplus zryan
* Can't remember if I also did a chmod 775 on the mountpoint...


mount -l
if this shows your HFS drive as ro despite the above, it may be due to the drive being improperly unmounted. Unmount it and run fsck.hfsplus -- see below.

You'll need hfsprogs (allows fsck.hfsplus - which you will NEED to run if your Mac HD is ever inproperly unmounted)
sudo apt-get install hfsprogs
sudo umount /[mountpoint]
sudo fsck.hfsplus /dev/[drive]
OR you can plug it into a mac and use disk utilities repair disk.

Setting up VNC
http://lifehacker.com/317125/set-up-vnc-on-ubuntu-in-four-steps
NOTE: My VNC is behind a router.. What this means is that the port that VNC uses is blocked at the router level.. this would otherwise be a big security concern.
x11vnc -forever -rfbport 5900 -rfbauth ~/.vnc/passwd -o ~/.vnc/x11vnc.log -auth ~/.vnc/:0 -noxdamage -display :0 -nossl

Setting up SSH
http://www.jonathanmoeller.com/screed/?p=1585
ssh -p 83 zryan@24.235.168.40 -L 5900/localhost:5900

Other things to consider.
Setting up Port Forwarding on a [wireless] router
Setting up mounting in FSTAB and adding mount folders
Setting up Samba for Windows machines


```

---

### Post by Khayyam on 2012-01-30
orisdorch .. OK, good to hear some headway is being made, and again np.

I should have mentioned that I'm not an Ubuntu user, I only created the account here so as to make a post re USB booting 11.10 iso's for install on Mactel. I'd created a USB boot disk for a friend (using grub2-efi) after they had failed getting it to work from instructions posted here. I'd got it to work and so was passing on the fix. In your case I figured I had some idea of what was going on, and might be able to help, but that help is limited specificly to the kernel oops and Netatalk, as far as how one might go about upgrading from 2.2beta4 to 2.2.2 on Ubuntu I'm best to defer to someone else. I can say there are essencially two methods, find a .deb package or compile from source, both methods will require you meet dependencies and/or have the requisite tools/libraries installed, and so will be specific to your install (distribution, release, etc). This is something you'll get a handle on over time, so I wouldn't worry about it, I only suggested upgrading to 2.2.2 as its standard practice to be running the latest stable release prior to troubleshooting, but as 2.2beta4 is Ubuntu's current stable package I would assume the package is working as expected for standard setups.

As I understand it Time Machine shouldn't care what filesystem it is on, the 'actual' filesystem is within the sparsebundle. If you create a hfsplus.img it is the client machine that mounts it, not the host machine. I can't see this being an issue and wonder why others suggest that the sparsebundle needs to be on a journaled HFS+. The only issue I could forsee is how Time Machine might set permissions on the sparsebundle. Incidentally, I see others are using the 'upriv' option for Time Machine shares (see: [this]("http://langit.wordpress.com/2011/09/14/share-folder-in-ubuntu-11-04-for-mac-osx-lion/") for example).

The 'tm' option seems to have come about to overcome some 10.7 issue (or change in protocol). I don't imagine it will effect your setup with or without it, and I'm assuming your client OS is prior to 10.7.

I'd suggest you do move the shares from $HOME as you can then inlcude /home/zryan as a seperate share .. /media/ or /mnt/ would be the obvious choices.

I think Samba has been discontinued for 10.7 so its not really an option for 10.7 clients.

I don't think there is any obvious solution we are missing here, at least in terms of Netatalk's setup, the problem may be, as I suggested, how hfsplus (kernel) and afpd/cnid_meta deal with the B*Tree, and this is not something that can currently be worked arround. With that in mind I'd say the solution is not to export hfsplus mounted disks, at least at this current moment in time. If your satisified with that then you might want to mark this thread [SOLVED].

---

### Post by orisdorch on 2012-02-15
I'll edit this final post with updates for anyone who happens upon this thread with similar issues.. Don't want to keep posting as the thread is basically dead and I don't want to keep bumping it.

I've had my Ubuntu machine crash-free for well over a week now! I started by mounting the HFS+ volume as Read-Only and tested that for a few days - worked great, but no write access.. Next step I took was to mount the drive as RW, but in /etc/netatalk/AppleVolumes.default  I used options:usedots,**ro**  - so I can write to the drive on Ubuntu, but not over Netatalk. I then installed Samba so that I could use the SMB protocol when I wanted to write to the drive over the network, and could use the Netatalk/AppleTalk protocol when I only needed to read data.. This has been working great so far.

I do plan to test Netatalk & RW on an HFS+ drive further, but will use a small older HD as I don't want to corrupt my 2TB backup! Will update this thread eventually when I do more testing.

---

### Post by Afinity on 2012-03-17
> **orisdorch said:**
>  I do plan to test Netatalk & RW on an HFS+ drive further, but will use a small older HD as I don't want to corrupt my 2TB backup! Will update this thread eventually when I do more testing.

Orisdorch, I highly recommend you go with a HFS+ (Journaled) filesystem if you are hell bent on using HFS. Many people say it's impossible to write to from ubuntu, but they are only partially correct.

_To mount a r/w HFS+ journaled file system:_
- install the packages "hfsprogs hfsplus hfsutils"
- quickly repair the volume FS if it suffered any power losses previously.
- then use a mounting command like "sudo mount -o force /dev/sdx /PATH/TO/DIRECTORY"

The key package here is *hfsprogs*. I use this as my mounting method for a journaled HFS+ external USB HDD anyways. Though my time machine backup for netatalk is on an EXT4 partition actually. 

~Cheers

---

