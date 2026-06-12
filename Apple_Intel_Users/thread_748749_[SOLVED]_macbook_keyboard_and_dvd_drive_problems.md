---
title: "[SOLVED] macbook keyboard and dvd drive problems"
date: 2008-04-07
forum: Apple Intel Users
---

### Post by odo_ on 2008-04-07
Hi, I reasently bouhgt a macbook (2,4 gigHz etc, the new one with broadcom wifi) now i have a problem with keyboard/dvd drive.

when i'm using my laptop, after a while, the time isn't the same, once it is 5minutes otres it's a few hours; sudenly my keybord starts giving me problems, its like it take a lot of time to get the key events, so i can't write normaly and most of the key presses writes 2 or 3 times the same letter.

this happens at the same time i get a big dmesg error and the dvd drive stops working

here the dmesg
```
hda: cdrom_pc_intr: The drive appears confused (ireason = 0x01). Trying to recover by ending request.
irq 11: nobody cared (try booting with the "irqpoll" option)
Pid: 3477, comm: hald-addon-stor Tainted: P        2.6.24.4-mactel-macbook-v2 #1
 [<c0152c3a>] __report_bad_irq+0x36/0x75
 [<c01390a6>] tick_program_event+0x33/0x52
 [<c0152e8d>] note_interrupt+0x214/0x24f
 [<c015237a>] handle_IRQ_event+0x1a/0x3f
 [<c0153777>] handle_level_irq+0x6e/0xbb
 [<c010657b>] do_IRQ+0x57/0x70
 [<c0114b5c>] smp_apic_timer_interrupt+0x74/0x80
 [<c0104807>] common_interrupt+0x23/0x28
 [<c013007b>] param_set_charp+0x12/0x57
 [<c01300d8>] param_sysfs_setup+0x18/0xc7
 [<c012580b>] __do_softirq+0x5e/0xcf
 [<c01258ae>] do_softirq+0x32/0x36
 [<c0125b00>] irq_exit+0x38/0x6b
 [<c0114b5c>] smp_apic_timer_interrupt+0x74/0x80
 [<c01048c4>] apic_timer_interrupt+0x28/0x30
 [<c01f4224>] delay_tsc+0xb/0x13
 [<c01f41ed>] __delay+0x6/0x7
 [<f899a1c8>] __ide_wait_stat+0x8e/0xc5 [ide_core]
 [<f899ad14>] ide_wait_stat+0x45/0x72 [ide_core]
 [<f8998fc8>] ide_do_request+0x420/0x96b [ide_core]
 [<f8998c19>] ide_do_request+0x71/0x96b [ide_core]
 [<c02cdd5d>] schedule_timeout+0x13/0x8d
 [<c01e4206>] elv_drain_elevator+0x15/0x58
 [<c01e4aca>] elv_insert+0x107/0x1ea
 [<c01e69e4>] __blk_put_request+0x24/0x75
 [<c01e6c4b>] blk_put_request+0x22/0x36
 [<f89995cb>] ide_do_drive_cmd+0xb8/0xfc [ide_core]
 [<f89e1298>] cdrom_queue_packet_command+0x35/0xa9 [ide_cd]
 [<c01e69e4>] __blk_put_request+0x24/0x75
 [<c01e6c4b>] blk_put_request+0x22/0x36
 [<f89e1437>] cdrom_read_tocentry+0x96/0xa1 [ide_cd]
 [<c01e6c06>] blk_end_sync_rq+0x0/0x23
 [<f89e2210>] cdrom_read_toc+0x100/0x3bc [ide_cd]
 [<f89e2e41>] idecd_revalidate_disk+0x10/0x16 [ide_cd]
 [<c0175127>] get_super+0x15/0x7a
 [<c01929a8>] __invalidate_device+0x2e/0x34
 [<c01929eb>] check_disk_change+0x3d/0x5c
 [<c01e4206>] elv_drain_elevator+0x15/0x58
 [<f89db2d9>] cdrom_open+0x88d/0x8fc [cdrom]
 [<c01e69e4>] __blk_put_request+0x24/0x75
 [<c01e6c4b>] blk_put_request+0x22/0x36
 [<f8999605>] ide_do_drive_cmd+0xf2/0xfc [ide_core]
 [<c0181dea>] __d_lookup+0x91/0xe1
 [<c017977f>] do_lookup+0x4f/0x140
 [<c01821f0>] dput+0x21/0xe6
 [<c017b62e>] __link_path_walk+0xa15/0xb35
 [<f89e1675>] cdrom_lockdoor+0x59/0xc7 [ide_cd]
 [<c0136488>] getnstimeofday+0x2b/0xaf
 [<c0185489>] mntput_no_expire+0x13/0x66
 [<c017b7f7>] link_path_walk+0xa9/0xb3
 [<c02cdfd0>] mutex_lock+0xb/0x1a
 [<c0192dd1>] __blkdev_put+0xcb/0xe3
 [<c0171b48>] get_unused_fd_flags+0x54/0xb1
 [<c01f063e>] kobject_get+0xf/0x13
 [<c01ea666>] get_disk+0x30/0x46
 [<c01ea683>] exact_lock+0x7/0xd
 [<c0253f38>] kobj_lookup+0xe4/0x10e
 [<f89e1eb0>] idecd_open+0x72/0x86 [ide_cd]
 [<c0192f77>] do_open+0x87/0x23f
 [<c01932bb>] blkdev_open+0x0/0x4d
 [<c01932e0>] blkdev_open+0x25/0x4d
 [<c0171c7a>] __dentry_open+0xce/0x185
 [<c0171dab>] nameidata_to_filp+0x24/0x33
 [<c0171dec>] do_filp_open+0x32/0x39
 [<c02cdfd0>] mutex_lock+0xb/0x1a
 [<c0192dd1>] __blkdev_put+0xcb/0xe3
 [<c0171b48>] get_unused_fd_flags+0x54/0xb1
 [<c0171e37>] do_sys_open+0x44/0xc4
 [<c0171ef0>] sys_open+0x1c/0x1e
 [<c0103df6>] sysenter_past_esp+0x5f/0x85
 =======================
handlers:
[<f8978dd6>] (usb_hcd_irq+0x0/0x54 [usbcore])
[<f8978dd6>] (usb_hcd_irq+0x0/0x54 [usbcore])
[<f8863bb4>] (irq_handler+0x0/0x1b4 [firewire_ohci])
[<f899960f>] (ide_intr+0x0/0x1be [ide_core])
Disabling IRQ #11
```

i'm using a custom kernel with mactel paches, and tried to boot with irqpoll, witch dind't solve the problem

I wanted to know if anyone else is having this problem or if this is an fabrication problem

and of corse if it isn't i'm looking for a solution

sorry for my english

Thanks to all Odo_

---

### Post by cyberdork33 on 2008-04-07
if it is a custom kernel, I'd say there is a problem with your configuration.

---

### Post by odo_ on 2008-04-07
thanks for the respose, but i think this shouldn't be the problem, i used the stantard  config, patched with mactel patches, (in order to use fn keys backlight support etc) and changed processor type to core2 i think anything else is standart,

---

### Post by incubus on 2008-04-07
Do you still have a copy of your old kernel?  If so, can you boot it and see if this problems also occurs there?

---

### Post by odo_ on 2008-04-07
yes, the error also happens with old kernel, now i'm compiling a new one with a few other options concerning intel piix supprot, i saw this is deactivated in my config, but hwinfo tels that the dvd drive uses piix and the chipset is an intel, so lets see if this solves the problem.

i'm starting to think this is a hardware problem because i dont find any other with this problem

---

### Post by odo_ on 2008-04-08
Hi, i don't know how and more important If i should mar this thread as solved. 
But the case is that after another recompiling, i'm no longer getting any error messege (let's see after longer time) 

The (Hoply) solution for me, i fgured out the problem was in the driver de cd was using, is conflicting with de usb (keyboard, touchpad, external drives etc) so i decided to deactivate evey thing in the ata section of the kernel config, so i forced the laptop to use libata (scsi mode) 

the drive is the recogniced as scd0 and i had to change de device in /etc/pommed.conf to get the eject button agian working.

so this isn't a global solution but iv it works.....

Little oftopic tip: i reconfiguret the eject button with Xmodmap to get a delete buton, so only if i use fn+eject the cd is ejected, if used without fn its a delete button.

i hope this helps someone after me and, of corse i hope this is the solution

Thanks to all Odo_

---

### Post by cyberdork33 on 2008-04-08
you can mark "solved" under the "thread tools" menu at the top of this thread.

---

