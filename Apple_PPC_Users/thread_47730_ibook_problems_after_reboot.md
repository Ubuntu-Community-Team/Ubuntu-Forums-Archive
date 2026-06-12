---
title: "ibook problems after reboot"
date: 2005-07-09
forum: Apple PPC Users
---

### Post by jonest on 2005-07-09
I have a 933mhz ibook G4.  I installed 5.0.4 and everything was working great.  I have a d-link dwl-122 wireless usb key and it was working along with cd burning, etc.  In fact, I had none of the problems associated with other distros.

I rebooted a few hours after installation and update and I now cannot see the cd drive, the usb appears to be disabled, and there is no sound.  The only clue I get about the usb is the following two lines appearing in /var/log/messages upon boot.

Apple USB OHCI 0001:10:18.0 disabled by firmware
Apple USB OHCI 0001:10:19.0 disabled by firmware

The cd drive which is a combo (cd-r and dvd) was located at /dev/hdc with a link to /dev/cdrom.  Now, there is not /dev/hdc or /dev/cdrom, but the entry is still in /etc/fstab.

I do not as of yet have any clues regarding the sound.  

I do find the following entry in messages which may be odd as well.

No module symbols loaded - kernel modules not enabled.

Thanks for any help.

---

### Post by audiorevolution on 2005-07-09
Zap the PRAM (CMD+OPTION+P+R when booting at the chime, and you will hear a second chime), and the problem should be solved.

---

