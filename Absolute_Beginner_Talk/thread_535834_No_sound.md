---
title: "No sound"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by kfealz on 2007-08-27
Sorry for this cross post, but no one replied to my post in installations...

I have Intel HD Audio cable plugged into the AAFP port on my ASUS P5B wifi mobo.When I boot up, there is an 'X' over the volume button which says, "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured." when clicked. DMESG returns "[ 774.400769] n<1>hdaudio: hda: No free DMA engines." I have searched google to my limit and can not find the reason for this.

I just tried running rhythmbox and movie player at the same time playing different mp3s and it worked, but if I load firefox and go to pandora.com (awesome site btw) or any other website with sound, my sound disappears and the DMA errors start coming.  When I run "soundoff" then "soundon" my sound comes back, though the error message still comes from clicking on the volume manager. 

The following are the output of dmesg after soundoff & soundon:
[ 3123.643889] n<6>ACPI: PCI interrupt for device 0000:00:1b.0 disabled
[ 3131.412730] usbcore: deregistering interface driver ossusb
[ 3135.222474] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[ 3135.225756] hdaudio: Unknown HDA codec 0x11d4198b
[ 3135.253326] usbcore: registered new interface driver ossusb

Also, if it helps, I just installed Cedega and passed its OSS test, but failed the ALSA test.

Any help would be GREATLY appreciated since this is the last thing on my to-do list to have a fully-functioning system. :)

---

### Post by kfealz on 2007-08-29
This was my solution:
[http://4front-tech.com/forum/viewtopic.php?p=6159#6159](http://4front-tech.com/forum/viewtopic.php?p=6159#6159)

---

