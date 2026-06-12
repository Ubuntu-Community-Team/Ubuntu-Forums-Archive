---
title: "GRUB question, USB booting"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-29
G'day everyone

I have an external USB HD that is connected to my laptop, like 95% of the time.

Unfortunately my laptop's BIOS is not able to boot from USB (its quite old).

I would like to install another linux distro or 2 to the external USB drive, my concern is such.

I could quite easily edit GRUB's menu.lst to point to the USB drive, no problems at all, but on the odd occasion when my USB drive is NOT connected, will this cause GRUB to find an error?

Is there anyway to ask GRUB to check if there is an external drive connected, and to therefore create an appropriate menu.lst depending on whether it is present?

Anybody think of another workaround?

The only one i can think of at the moment is to have a boot cd with another GRUB for use when i want to boot from the USB.... would this be doable? Can you have 2 GRUB's? I don't see why not.

---

### Post by smoker on 2007-05-29
hi, i think maybe the 'super grub disk' is what you are looking for, though i am not sure how it would work with usb, it may be worth a download to try.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

if it works with usb, then you can boot as normal, until you want to boot from usb, and insert the disk and follow on from there.

if it is no use for usb, well, it is always a handy tool to have to hand if things ever go 'fubar!'

best of luck:-)

---

### Post by ugm6hr on 2007-05-29
> **drowner said:**
> 

I could quite easily edit GRUB's menu.lst to point to the USB drive, no problems at all, but on the odd occasion when my USB drive is NOT connected, will this cause GRUB to find an error?


Surely it will only error if you actually select one of the USB distros when the drive is not connected?  And then - if you do - just plug in and reboot again.  As I understand it, GRUB doesn't check the entries on menu.lst until you select one when booting.

---

### Post by drowner on 2007-05-30
> **ugm6hr said:**
> Surely it will only error if you actually select one of the USB distros when the drive is not connected?  And then - if you do - just plug in and reboot again.  As I understand it, GRUB doesn't check the entries on menu.lst until you select one when booting.

Really? Well that sounds interesting.

I might try that.

---

