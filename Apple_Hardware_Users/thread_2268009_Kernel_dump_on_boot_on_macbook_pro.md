---
title: "Kernel dump on boot on macbook pro"
date: 2015-03-05
forum: Apple Hardware Users
---

### Post by mattator on 2015-03-05
Hi,

On boot I have this error with kernel :
ommand line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-31-generic
 root=UUID=8cf1f180-1ef1-44a5-aca6-ca0a3f87736b ro usbhid.quirks=0x1B1C:0x1B13:0x20000000
```


5fff], which spans more than reserved [mem 0xfed10000-0xfed13fff]
Mar  5 14:17:00 teto-Mac kernel: [    2.508542] ------------[ cut here ]------------
Mar  5 14:17:00 teto-Mac kernel: [    2.508548] WARNING: CPU: 1 PID: 1 at /build/buildd/linux-3.16.0/arc
h/x86/mm/ioremap.c:183 __ioremap_caller+0x25a/0x2e0()
Mar  5 14:17:00 teto-Mac kernel: [    2.508550] Info: mapping multiple BARs. Your kernel is fine.
Mar  5 14:17:00 teto-Mac kernel: [    2.508552] Modules linked in:
Mar  5 14:17:00 teto-Mac kernel: [    2.508556] CPU: 1 PID: 1 Comm: swapper/0 Not tainted 3.16.0-31-gene
ric #41-Ubuntu
Mar  5 14:17:00 teto-Mac kernel: [    2.508558] Hardware name: Apple Inc. MacBookPro9,2/Mac-6F01561E16C7
5D06, BIOS MBP91.88Z.00D3.B08.1208081132 08/08/2012
Mar  5 14:17:00 teto-Mac kernel: [    2.508561]  0000000000000009 ffff880169363b78 ffffffff81782d0b ffff
880169363bc0
Mar  5 14:17:00 teto-Mac kernel: [    2.508565]  ffff880169363bb0 ffffffff8106ff2d ffffc9000a258000 0000
000000006000
Mar  5 14:17:00 teto-Mac kernel: [    2.508568]  ffffc9000a258000 ffffc9000a258000 00000000fed10000 ffff
880169363c10
Mar  5 14:17:00 teto-Mac kernel: [    2.508572] Call Trace:
Mar  5 14:17:00 teto-Mac kernel: [    2.508577]  [<ffffffff81782d0b>] dump_stack+0x45/0x56
Mar  5 14:17:00 teto-Mac kernel: [    2.508581]  [<ffffffff8106ff2d>] warn_slowpath_common+0x7d/0xa0
Mar  5 14:17:00 teto-Mac kernel: [    2.508584]  [<ffffffff8106ff9c>] warn_slowpath_fmt+0x4c/0x50
Mar  5 14:17:00 teto-Mac kernel: [    2.508588]  [<ffffffff810773e7>] ? iomem_map_sanity_check+0xc7/0xd0
Mar  5 14:17:00 teto-Mac kernel: [    2.508591]  [<ffffffff8105d63a>] __ioremap_caller+0x25a/0x2e0
Mar  5 14:17:00 teto-Mac kernel: [    2.508594]  [<ffffffff8105d6d7>] ioremap_nocache+0x17/0x20
Mar  5 14:17:00 teto-Mac kernel: [    2.508598]  [<ffffffff81033ebd>] snb_uncore_imc_init_box+0x6d/0x90
Mar  5 14:17:00 teto-Mac kernel: [    2.508602]  [<ffffffff81036e0e>] uncore_pci_probe+0xce/0x1b0
Mar  5 14:17:00 teto-Mac kernel: [    2.508606]  [<ffffffff813e5ac5>] local_pci_probe+0x45/0xa0
Mar  5 14:17:00 teto-Mac kernel: [    2.508609]  [<ffffffff813e6da5>] ? pci_match_device+0xe5/0x110
Mar  5 14:17:00 teto-Mac kernel: [    2.508612]  [<ffffffff813e6ee9>] pci_device_probe+0xd9/0x130
Mar  5 14:17:00 teto-Mac kernel: [    2.508616]  [<ffffffff814d20b3>] driver_probe_device+0xa3/0x410
Mar  5 14:17:00 teto-Mac kernel: [    2.508618]  [<ffffffff814d24eb>] __driver_attach+0x8b/0x90
Mar  5 14:17:00 teto-Mac kernel: [    2.508621]  [<ffffffff814d2460>] ? __device_attach+0x40/0x40
Mar  5 14:17:00 teto-Mac kernel: [    2.508625]  [<ffffffff814cff2b>] bus_for_each_dev+0x6b/0xb0
Mar  5 14:17:00 teto-Mac kernel: [    2.508628]  [<ffffffff814d1b3e>] driver_attach+0x1e/0x20
Mar  5 14:17:00 teto-Mac kernel: [    2.508632]  [<ffffffff814d1740>] bus_add_driver+0x180/0x250
Mar  5 14:17:00 teto-Mac kernel: [    2.508635]  [<ffffffff81d505af>] ? uncore_types_init+0x1a1/0x1a1
Mar  5 14:17:00 teto-Mac kernel: [    2.508637]  [<ffffffff814d2cc4>] driver_register+0x64/0xf0
Mar  5 14:17:00 teto-Mac kernel: [    2.508641]  [<ffffffff813e533c>] __pci_register_driver+0x4c/0x50
Mar  5 14:17:00 teto-Mac kernel: [    2.508644]  [<ffffffff81d50723>] intel_uncore_init+0x174/0x40b
Mar  5 14:17:00 teto-Mac kernel: [    2.508647]  [<ffffffff81d505af>] ? uncore_types_init+0x1a1/0x1a1
Mar  5 14:17:00 teto-Mac kernel: [    2.508650]  [<ffffffff81002148>] do_one_initcall+0xd8/0x210
Mar  5 14:17:00 teto-Mac kernel: [    2.508654]  [<ffffffff81092bfd>] ? parse_args+0x21d/0x4e0
Mar  5 14:17:00 teto-Mac kernel: [    2.508658]  [<ffffffff81d4311d>] kernel_init_freeable+0x190/0x218
Mar  5 14:17:00 teto-Mac kernel: [    2.508662]  [<ffffffff81775e10>] ? rest_init+0x80/0x80
Mar  5 14:17:00 teto-Mac kernel: [    2.508665]  [<ffffffff81775e1e>] kernel_init+0xe/0xf0
Mar  5 14:17:00 teto-Mac kernel: [    2.508668]  [<ffffffff8178ac7c>] ret_from_fork+0x7c/0xb0
Mar  5 14:17:00 teto-Mac kernel: [    2.508671]  [<ffffffff81775e10>] ? rest_init+0x80/0x80
Mar  5 14:17:00 teto-Mac kernel: [    2.508676] ---[ end trace ccb10b6cc8299ea2 ]---

```
Any idea why ? should I enable/disable a module ?

---

### Post by este.el.paz on 2015-03-08
I don't know enough to be able to tell you what your data is telling you; but, perhaps a little more info on what MBPro you are working with?  And, possibly if you are using 7.10 . . . it's time to move up to a newer version, like at least 12.04 or 14.04 LTS and see if that fixes the problem???  You have choice of "hardware" problems OR "software" problems OR possibly both are "trining" . . . Mars has invaded Venus, or some such thing.  : - )

e.e.p.

---

