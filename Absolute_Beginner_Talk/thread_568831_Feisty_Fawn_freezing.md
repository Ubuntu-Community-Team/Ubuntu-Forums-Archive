---
title: "Feisty Fawn freezing"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-10-06
Last night I was listening to streaming music with XMMS and I found that my system frozen. It was still streaming music but I couldn't get into terminal to reboot . . . I finally just shut the system down. This morning I ran clamscan. It went through the files okay and found a phish email . . . when I looked at this computer again it was frozen. It had ended the virus check but on the terminal screen was this strange message:
kernel: [4923.025102 disabling IRQ #17
I have looked through the system log but really don't know what I am looking for. Can anyone help me get this computer working correctly again. 

Oct  6 09:30:00 george-desktop kernel: [  922.174983] irq 17: nobody cared (try booting with the "irqpoll" option)
Oct  6 09:30:00 george-desktop kernel: [  922.175020]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Oct  6 09:30:00 george-desktop kernel: [  922.175050]  [note_interrupt+520/576] note_interrupt+0x208/0x240
Oct  6 09:30:00 george-desktop kernel: [  922.175076]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Oct  6 09:30:00 george-desktop kernel: [  922.175097]  [handle_fasteoi_irq+112/160] handle_fasteoi_irq+0x70/0xa0
Oct  6 09:30:00 george-desktop kernel: [  922.175111]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Oct  6 09:30:00 george-desktop kernel: [  922.175122]  [do_IRQ+69/128] do_IRQ+0x45/0x80
Oct  6 09:30:00 george-desktop kernel: [  922.175139]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Oct  6 09:30:00 george-desktop kernel: [  922.175187]  [native_safe_halt+2/16] native_safe_halt+0x2/0x10
Oct  6 09:30:00 george-desktop kernel: [  922.175202]  [default_idle+56/80] default_idle+0x38/0x50
Oct  6 09:30:00 george-desktop kernel: [  922.175206]  [cpu_idle+28/96] cpu_idle+0x1c/0x60
Oct  6 09:30:00 george-desktop kernel: [  922.175209]  [start_kernel+565/896] start_kernel+0x235/0x380
Oct  6 09:30:00 george-desktop kernel: [  922.175223]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Oct  6 09:30:00 george-desktop kernel: [  922.175243]  =======================
Oct  6 09:30:00 george-desktop kernel: [  922.175246] handlers:
Oct  6 09:30:00 george-desktop kernel: [  922.175248] [<f087ddc0>] (usb_hcd_irq+0x0/0x60 [usbcore])
Oct  6 09:30:00 george-desktop kernel: [  922.175276] [<f12829d9>] (nv_kern_isr+0x0/0x61 [nvidia])
Oct  6 09:30:00 george-desktop kernel: [  922.175523] Disabling IRQ #17
Oct  6 09:30:09 george-desktop kernel: [  930.977791] NVRM: Xid (0001:00): 16, Head 00000000 Count 00023a64
Oct  6 09:30:11 george-desktop kernel: [  932.974720] NVRM: Xid (0001:00): 8, Channel 00000000
Oct  6 09:30:17 george-desktop kernel: [  938.965483] NVRM: Xid (0001:00): 16, Head 00000000 Count 00023a65
Oct  6 09:30:19 george-desktop kernel: [  940.962418] NVRM: Xid (0001:00): 8, Channel 0000001e
Oct  6 09:30:25 george-desktop kernel: [  946.953187] NVRM: Xid (0001:00): 16, Head 00000000 Count 00023a66
Oct  6 09:30:27 george-desktop kernel: [  948.950117] NVRM: Xid (0001:00): 8, Channel 0000001e
Oct  6 09:30:33 george-desktop kernel: [  954.940880] NVRM: Xid (0001:00): 16, Head 00000000 Count 00023a67
Oct  6 09:30:35 george-desktop kernel: [  956.937814] NVRM: Xid (0001:00): 8, Channel 0000001e

it has crashed two times since I posted this and while trying to edit this message HELP. LOL

Tim

---

### Post by Pumalite on 2007-10-06
Check this. It might help:

[http://www.linuxquestions.org/questions/linux-newbie-8/disabling-irq-17-589197/](http://www.linuxquestions.org/questions/linux-newbie-8/disabling-irq-17-589197/)

---

### Post by SVWander on 2007-10-06
> **Pumalite said:**
> Check this. It might help:

[http://www.linuxquestions.org/questions/linux-newbie-8/disabling-irq-17-589197/](http://www.linuxquestions.org/questions/linux-newbie-8/disabling-irq-17-589197/)

I almost hate to edit  acpi=noirq or irqpoll to your kernel line in /boot/grub/menu.lst  . as the post suggests. I would like to know where the problem is and try to fix it and I am not sure how to run "/cat/proc/interrupts"

Tim

---

