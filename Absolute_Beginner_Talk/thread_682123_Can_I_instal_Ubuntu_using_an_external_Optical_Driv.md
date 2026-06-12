---
title: "Can I instal Ubuntu using an external Optical Drive?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2008-01-29
I've got a sony Vaio laptop.
The internal Optical drive is broken, and I have a USB external drive.  It doesn't have any OS and I can't choose USB in the booting options from BIOS....

Do I have some chance to install Ubuntu on this machine?  I can't boot it in any way..

Some ideas?


Thank you guys

---

### Post by macogw on 2008-01-29
You could try this:  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Kosimo on 2008-01-29
> **macogw said:**
> You could try this:  [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Thank you for that quick answer!

But unfortunatelly I can't boot from USB....

Something I can do is change the HD...

Can I move the HD to another laptop, copy the CD contents to that Hd and then start the installation fromt he same HD once inside the Sony vaio?

Wired?

---

### Post by macogw on 2008-01-29
Oh I thought you meant you couldn't boot from the USB hard drive because it's blank.  OK then...can you PXE boot....boot over the network?

You could actually probably do the install on the hard drive from another computer then switch it in.  You might have to change xorg.conf for the new video drivers (if it's different), but otherwise...it should pretty much work.  I've booted at least 20 computers from my hard drive just fine.

---

### Post by Joeb454 on 2008-01-29
I've never tried doing that, because I've always assumed that you'd need drivers on a per machine basis.

I.E. Machine A would have different hardware - thus different drivers - than Machine B

---

