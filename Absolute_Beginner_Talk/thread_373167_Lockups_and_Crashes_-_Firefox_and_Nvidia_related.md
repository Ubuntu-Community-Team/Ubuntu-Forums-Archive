---
title: "Lockups and Crashes - Firefox and Nvidia related"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by scottness on 2007-03-01
Today, I began installing Ubuntu on a new laptop.  This is my 3rd Ubuntu installation on computers in my house...each of them different.  This new laptop is a Dell Inspiron e1505 with an Nvidia Geforce Go 7300 video card.

Using the default 'nv' driver, I had no problems with any of the typical applications.  After I successfully installed Beryl and the Nvidia driver, Firefox began to have a problem.  This problem began almost immediately after the last tweak I made to xorg.conf to get Beryl fully functional.  Beryl had been loading correctly in all but one area, no window decorations showed up.  After looking at some howtos and forum posts, I realized the the problem was that the default depth set for my screen was at 16 instead of 24...so I changed it.  Beryl began to work perfectly.  After this, I opened up Firefox and it immediately locked up the computer after I tried to download a few beryl themes from gnome-look.  This lockup problem continued in Firefox, not only after downloading a file, but after just browsing for a short amount of time.  

I tried to open Firefox in the terminal to see if any messages showed up there, but all I saw was this repeating for a few lines:
> ** Message: plugin_get_value 1 (1)
** Message: plugin_get_value 2 (2) 

The lockups would simply prevent me from doing anything with the system...I could still move the mouse around, but could not actually click on anything.  I had to press the power button to reboot.  After rebooting, I looked in the system logs and found this error message:
> sbevill-laptop gconfd (root-5018): Resolved address "xml:readonly; /var/lib/gconf/defaults" to a read-only configuration source at position 4
sbevill-laptop gconfd (root-5018): GConf server is not in use, shutting down.
sbevill-laptop gconfd (root-5018): Exiting
sbevill-laptop kernel: [17180433.560000] <c01499a4> __report_bad_irq+0x24/0x80 <0149a9d>note_interrupt+0x9d/0x270
sbevill-laptop kernel: [17180433.560000] <f9595415>nv_kern_isr+0x2f/0x62[nvidia] <c0149323>handle_IRQ_event+0x33/0x60
sbevill-laptop kernel: [17180433.560000] <c0149448>__do_IRQ+0xf8/0x110 <c0105c89>do_IRQ_0x19/0x30
sbevill-laptop kernel: [17180433.560000] <c010408a> common_interrupt+0x1a/0x20 <f88586dd>acpi_processor_idle+0x220/0x3af[processor]
sbevill-laptop kernel: [17180433.560000] <c02d902a> schedule+0x48a/0xcc0 <c0102122>cpu_idle+0x42/0xb0
sbevill-laptop kernel: [17180433.560000] <c03f27a1> start_kernel+0x321/0x3a0 <c03f2210>unknown_bootoption+0x0/0x270
sbevill-laptop syslogd 1.4.1#18ubuntu6: restart.

My video card driver settings are:
> Nvidia Geforce Go 7300
Driver Version: 1.0-9746


I'm kind of stumped on this one.  Anyway to set it so that I can run both Beryl and Firefox?  As of right now, its looking like one or the other...

Thanks in advance, and if you need anymore info, let me know.

---

### Post by dubrict on 2007-03-01
The first thing I'd recommend trying is the friendly old trick from windows of reinstalling stuff.

Well, reconfiguring them at least.  Assuming you installed the nvidia driver from a repository, open up a terminal and type in:

sudo dpkg-reconfigure nvidia-glx

---

### Post by scottness on 2007-03-01
This seems to have worked with my wired connection at work.  I'll try it again with my wireless connection at home.  Thanks!

---

### Post by scottness on 2007-03-02
Seems like it is related to my wireless connection only.  I thought it was more related to the video card, but I'm only having the lockups while I'm connected wirelessly... I'll have to look on this more.

---

