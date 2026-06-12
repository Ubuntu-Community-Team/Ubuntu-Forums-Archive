---
title: "Possible hardware problem but not sure ubuntu 12.04.3 (zentyal 3.2)"
date: 2013-11-27
forum: Any Other OS
---

### Post by hotsummer55 on 2013-11-27
I know this is zentyal but it is mainly ubuntu 12.04.3 64bit
i have update atp-get upgrade to latest
I setup a new server with zentyal 3.2 on old hardware.
 The Hardware had been running windows with no problems.
 
I got a kernel BUG error .Is this possibly hardware or more likely a system / software problem.
This system crashed with below error BUG
>  Nov 22 15:17:04 zentyal kernel: [ 8030.080452] BUG: unable to handle kernel paging request at 000000000000ff18
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] IP: [<ffffffff811597b9>] vma_interval_tree_subtree_search+0x19/0x80
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] PGD 68473067 PUD 68474067 PMD 0 
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] Oops: 0000 [#1] SMP 
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] Modules linked in: xt_REDIRECT(F) xt_tcpudp(F) xt_state(F) iptable_nat(F) nf_nat_ipv4(F) iptable_filter(F) nf_nat_sip(F) nf_conntrack_sip(F) nf_nat_pptp(F) nf_nat_proto_gre(F) nf_conntrack_pptp(F) nf_conntrack_proto_gre(F) nf_nat_h323(F) nf_conntrack_h323(F) nf_conntrack_tftp(F) nf_nat_ftp(F) nf_nat(F) nf_conntrack_ftp(F) xt_mac(F) xt_mark(F) nf_conntrack_ipv4(F) nf_defrag_ipv4(F) xt_connmark(F) nf_conntrack(F) iptable_mangle(F) ip_tables(F) x_tables(F) quota_v2(F) quota_tree(F) snd_hda_codec_realtek(F) snd_hda_intel(F) i915(F) snd_hda_codec(F) coretemp(F) snd_hwdep(F) snd_pcm(F) drm_kms_helper(F) snd_timer(F) drm(F) snd(F) hid_generic(F) soundcore(F) snd_page_alloc(F) psmouse(F) usbhid(F) i2c_algo_bit(F) microcode(F) serio_raw(F) lpc_ich(F) hid(F) video(F) mac_hid(F) parport_pc(F) ppdev(F) lp(F) parport(F) usb_storage(F) e100(F)
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] CPU 0 
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] Pid: 31, comm: kswapd0 Tainted: GF            3.8.0-33-generic #48~precise1-Ubuntu Hewlett-Packard HP Compaq dx2300 Microtower/0A90
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] RIP: 0010:[<ffffffff811597b9>]  [<ffffffff811597b9>] vma_interval_tree_subtree_search+0x19/0x80
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] RSP: 0018:ffff880078ac5a98  EFLAGS: 00010206
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] RAX: ffff880079b16da8 RBX: ffff880068416b80 RCX: 000000000000ff00
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] RDX: 0000000000000022 RSI: 0000000000000022 RDI: ffff880079b16da8
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] RBP: ffff880078ac5a98 R08: ffff880079b16e00 R09: 0000000000000000
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] R10: 57ffe3bf4f902c80 R11: 0000000000000000 R12: ffffea00004b8c00
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] R13: 0000000000000000 R14: 0000000000000022 R15: 0000000000000000
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] FS:  0000000000000000(0000) GS:ffff88007f400000(0000) knlGS:0000000000000000
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] CR2: 000000000000ff18 CR3: 0000000068472000 CR4: 00000000000007f0
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] Process kswapd0 (pid: 31, threadinfo ffff880078ac4000, task ffff88007ba52e80)
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] Stack:
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  ffff880078ac5aa8 ffffffff81159c89 ffff880078ac5b28 ffffffff81169e4c
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  ffff880078ac5ad8 ffff88007b0e5400 ffff880078ac5be0 0000000000000000
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  00007f7c41ad8000 0000000000000022 ffff88007be2a138 0000000100000001
Nov 22 15:17:04 zentyal kernel: [ 8030.084009] Call Trace:
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff81159c89>] vma_interval_tree_iter_next+0x69/0x70
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff81169e4c>] page_referenced_file+0xfc/0x150
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff8116b915>] page_referenced+0x65/0xf0
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff81148dbd>] shrink_active_list+0x1dd/0x3a0
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff81149046>] shrink_list+0xc6/0x100
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff81149137>] shrink_lruvec+0xb7/0x1c0
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff811492b5>] shrink_zone+0x75/0xa0
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff8114a4af>] balance_pgdat+0x4ff/0x6c0
Nov 22 15:17:04 zentyal kernel: [ 8030.084009]  [<ffffffff8114a793>] kswapd+0x123/0x240
Nov 22 15:17:04 zentyal kernel: [ 8030.176099]  [<ffffffff8114a670>] ? balance_pgdat+0x6c0/0x6c0
Nov 22 15:17:04 zentyal kernel: [ 8030.176099]  [<ffffffff8107f210>] kthread+0xc0/0xd0
Nov 22 15:17:04 zentyal kernel: [ 8030.176099]  [<ffffffff8107f150>] ? flush_kthread_worker+0xb0/0xb0
Nov 22 15:17:04 zentyal kernel: [ 8030.176099]  [<ffffffff816fd0ac>] ret_from_fork+0x7c/0xb0
Nov 22 15:17:04 zentyal kernel: [ 8030.176099]  [<ffffffff8107f150>] ? flush_kthread_worker+0xb0/0xb0
Nov 22 15:17:04 zentyal kernel: [ 8030.176099] Code: 48 89 47 18 5d c3 66 66 66 2e 0f 1f 84 00 00 00 00 00 66 66 66 66 90 55 48 89 f8 48 89 e5 0f 1f 40 00 48 8b 48 68 48 85 c9 74 17 <48> 39 71 18 72 11 48 8d 41 a8 48 8b 48 68 48 85 c9 75 ed 0f 1f 
Nov 22 15:17:04 zentyal kernel: [ 8030.176099] RIP  [<ffffffff811597b9>] vma_interval_tree_subtree_search+0x19/0x80
Nov 22 15:17:04 zentyal kernel: [ 8030.176099]  RSP <ffff880078ac5a98>
Nov 22 15:17:04 zentyal kernel: [ 8030.176099] CR2: 000000000000ff18
Nov 22 15:17:04 zentyal kernel: [ 8030.228524] ---[ end trace 16c4980a7b862c1b ]---


I have run memory test and run mprime for a long time with no problems on knoppix
Is there anyone that can read this kernel log please

---

### Post by oldos2er on 2013-11-27
Moved to Other OS/Distro Support.

---

### Post by bashiergui on 2013-11-27
You could use gparted from a live CD to test it for hardware issues.

---

### Post by hotsummer55 on 2013-11-28
I have booted into knoppix
ran test on cpu with mprime
booted into ram test ran for 24 hours ok
checked fix disk smart data look good
i have looked at this log and im no expert but i think its the kswapd demond .anyone can confim this
If its not a bug in os then i thinks its the disk poss ? but no experiance of this error
but disk shows  no problems ? not sure

---

### Post by hotsummer55 on 2013-12-02
I am fairly sure this is a hardware problem so looking into it now.

---

