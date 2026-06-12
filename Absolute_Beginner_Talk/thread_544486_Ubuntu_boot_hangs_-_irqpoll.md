---
title: "Ubuntu boot hangs - irqpoll?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-09-06
After apparently successfully installing, Ubuntu studio hangs at boot with this message

[2.454061] ir2 20: nobody cared (try booting with 'irqpoll' option
[2.454165: handlers:
[2.454193] [<f8883f10>] (usb-hcd-irq+ 0x0/0x60 [usbcore])
[2.454285] disabling IRQ#20
[34.074265] ata3.00: failed to set xfermode (err_mask=0x40)
[69.214103] ata3.00: failed to set xfermode (err_mask=0x40)
[104.353867] ata3.00: failed to set xfermode (err_mask=0x40)


Searching through the forums for irqpoll solutions I came across this thread about a possible bug
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123617](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/123617)

as well as the suggestion to boot using irqpoll , by adding

irqpoll to the defoptions in /boot/grub/menu.lst


BUT
since ubuntu won't boot, how can I do this? And is it likely to help? Or does anyone have any other suggestions?

---

### Post by jnorthr on 2007-09-06
can you boot from the live cd ? Or boot in safe mode ? Have you changed your hardware recently ?

---

### Post by nonewmsgs on 2007-09-06
there is a bug report for this
[http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg08418.html](http://www.mail-archive.com/acpi-bugzilla@lists.sourceforge.net/msg08418.html)

what i would try is to try to disable acpi in your BIOS if you can and see if that helps anything.

---

